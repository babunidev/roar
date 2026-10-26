# ROARR — decision evidence and unresolved choices

**Creator:** Babuni.dev.

## Direct historical evidence

The first committed `roar.lua` (2025-11-22, `d618976`) explicitly describes the initial addon as based on **BuxbrewCharge**. That is a direct source comment and justifies recording a **technical lineage**, not a claim that AI conceived the original idea.

The README expanded on 2025-11-23 states a clear character-flavor experience: built-in battle emotes chosen randomly from a watched action-bar slot, with adjustable chance/cooldown and an on/off switch. This is repository evidence of the project's stated direction.

## Source-observed technical decisions

| Current approach | Evidence | Qualification |
| --- | --- | --- |
| Built-in emote pool | Five `EMOTE_TOKENS_BATTLE` and `DoEmote` | Built-in client behavior not in-game tested |
| Trigger follows button press | `UseAction` wrapper | Does not inspect cast success |
| Configurable chance and cooldown | `battle_chance`, `BATTLE_COOLDOWN` | Missed roll still consumes cooldown |
| Select a slot without a GUI | `/roarr watch`, `/roarr slot` | Not evidence of a formally rejected GUI |
| Explicitly suspend output | `ENABLED` and `/roarr off/on` | Settings preserved in saved table |
| Account-wide preferences | `SavedVariables: ROARRDB` | Multiple characters may have different slot layouts |
| Rename project in the installed package | November 23 filename and identifier changes | Motivation for repeated renames not known |

## Chronology of visible alternatives

The Git history shows both `roar` and `roarr` names applied to Lua and TOC files, several adjustments within 2025-11-23, a deletion and re-creation sequence, and a final `ROARR` package. The factual sequence is retained; it would be inappropriate to assert that these represent deliberately rejected concepts or that a particular failure forced a rename without logs.

The MIT LICENSE contains `Copyright (c) 2025 Elexior`, while current repo and manifest display Babuni.dev as project author. **Both are preserved**. The historical legal relationship is not verified; no authorship transfer or license edit is implied.

## Creator decisions pending

1. Should chance failures consume a cooldown?
2. Should the saved slot be per-character rather than shared account-wide?
3. Does ROARR remain a deliberately five-token lightweight sibling or belong to a migration narrative with `roarr` and RoarForever repositories?
4. Should an optional non-public preview be added?
5. Should historical attribution in the LICENSE be clarified?

These questions were **not answered or approved** by the creator during the documentation expansion.

## 2026-10-26 documentation decision

The assistant expanded docs only. It did not change addon behavior or settle any of the pending choices. Runtime validity remains unverified.
