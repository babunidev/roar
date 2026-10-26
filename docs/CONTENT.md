# ROARR — emote and UI text inventory

**Author:** Babuni.dev  
**Canonical source:** `EMOTE_TOKENS_BATTLE` in `roarr.lua`.

## Built-in emote tokens

| Token in source | Familiar slash-emote concept | Narrative purpose |
| --- | --- | --- |
| `ROAR` | roar | Battle cry |
| `CHARGE` | charge | Momentum |
| `CHEER` | cheer | Celebration |
| `BORED` | bored | Comic contrast |
| `FLEX` | flex | Strength/swagger |

ROARR passes a randomly chosen token to `DoEmote`. The text/animation experienced by nearby players is supplied by the **game client**, not by an embedded custom audio or animation file. Token availability on a specific client has not been verified in this documentation pass.

If `DoEmote` is absent, the Lua fallback posts the short generic string “makes a battle cry!” in `EMOTE` chat.

## Other player-facing writing

- Slash command prefix: `/roarr`, with `ROARR:` message label.
- Setup/status commands: `slot`, `watch`, `chance`, `cd`, `on`, `off`, `info`, `reset`, `save`, `tutorial`.
- Tutorial: a compact series of configuration commands, not a graphical wizard.
- Invalid command: concise usage text; invalid chance/cooldown produces its corresponding usage guidance.

## Editorial maintenance

Do not replace the five built-in tokens with bespoke text strings without the creator's direction. Content changes should distinguish gameplay effects, specific game-owned emotes and Babuni.dev's own addon-authored strings.

Historical source variants used `ROAR`, `/roar` and `ROARDB`; the final package uses the distinct `ROARR` namespace. See `docs/DEVLOG.md` for source-backed evolution.
