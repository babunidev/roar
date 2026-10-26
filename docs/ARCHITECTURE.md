# ROARR — source architecture (v1.0)

**Source:** `roarr.lua` and `roarr.toc` on `main`, inspected 2026-10-26. This is **static inspection**, not a live-client test.

## Execution path

```text
Player presses action-bar slot
       |
UseAction(slot, checkCursor, onSelf) wrapper
       |-- ensureLoaded() hydrates ROARRDB once
       |-- WATCH_MODE? -> print pressed slot
       |-- matches WATCH_SLOT? -> doBattleEmoteNow()
       |                          |-- check ENABLED
       |                          |-- check GetTime() - LAST_BATTLE_EMOTE_TIME >= BATTLE_COOLDOWN
       |                          |-- update LAST_BATTLE_EMOTE_TIME
       |                          |-- roll chance 1..100
       |                          '-- on success pick built-in emote and DoEmote(token)
       '-- delegate to captured _Orig_UseAction(slot, checkCursor, onSelf)
```

The order of operations is crucial: `LAST_BATTLE_EMOTE_TIME` is set **before** the chance check. A missed roll still postpones the next opportunity. The code does not inspect spell success or combat status.

## Key components and defaults

| Element | Purpose |
| --- | --- |
| `EMOTE_TOKENS_BATTLE` | Five strings: `ROAR`, `CHARGE`, `CHEER`, `BORED`, `FLEX` |
| `WATCH_SLOT` | Selected button number, initially none |
| `WATCH_MODE` | Temporary slot-discovery printout, not saved |
| `LAST_BATTLE_EMOTE_TIME` | Unsaved time of previous *eligible chance attempt*, initially 0 |
| `BATTLE_COOLDOWN` | Nonnegative seconds; default `6`; no input-enforced maximum |
| `battle_chance` | Percentage `0..100`; default `100` |
| `ENABLED` | Defaults `true`; can be persisted through `on`/`off` |
| `ROARRDB` | Account-wide SavedVariables table for `slot`, `battle_cd`, `battle_chance`, `enabled` |

## Lifecycle

`ensureLoaded()` reads the saved table lazily on the **first `UseAction` or `/roarr` call**. `PLAYER_LOGIN` seeds `math.random`; `PLAYER_LOGOUT` copies the current in-memory slot, chance, cooldown, and enabled state to `ROARRDB`.

**Possible edge case:** no call to `ensureLoaded()` occurs explicitly in the login or logout event handler. In a session where the user never presses any hooked action and never issues `/roarr`, logout may write initial/default values over previous saved preferences. This is a source-supported concern, not an observed in-game failure.

The code registers no other events or background timer. Cooldown checks are made only on watched-slot presses.

## The command parser

`/roarr` is parsed using `string.gsub` and Lua `string.find`, consistent with Lua 5.0-era syntax. Commands: `slot`, `watch`, `chance`, `cd`, `on`, `off`, `info`, `reset`, `save`, `tutorial`; unknown command prints usage.

Slot input is passed through `tonumber` but not clamped to valid integer slot IDs. Chance validates 0–100 inclusive; cooldown accepts any nonnegative number.

## WoW integration

- `DoEmote(token)` is the main output. If `DoEmote` does not exist, fallback uses `SendChatMessage("makes a battle cry!", "EMOTE")`.
- `_Orig_UseAction` is captured on file load and invoked after the emote attempt. Other addons with `UseAction` wrappers can affect call chains and load order.
- The TOC sets `Interface: 11200`, `Title: ROARR`, `Version: 1.0` and `SavedVariables: ROARRDB`.
- There is no addon-to-addon messaging, distance attenuation, sound file, custom UI, runtime network sync, or source dependency on RoarForever.

## Source risks to verify

Default timing on first press depends on initial `LAST_BATTLE_EMOTE_TIME=0` and current `GetTime()`. `math.randomseed` can affect the global PRNG used by other Lua code. Built-in emote names and their output depend on the actual client. None of these behaviors was tested by the documentation update.
