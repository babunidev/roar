# ROARR / roar — changelog and source history

**Project author:** Babuni.dev. Dates below identify **Git commits**, not necessarily releases.

## 2026-10-26 — expanded documentation

- Replaced the minimal scaffold with source-grounded README, concept, roadmap, architecture, interaction design, content register, decisions, narrative development journal and AI attribution.
- Documented the transition from ROAR to ROARR and the final `roarr` package, including historical rename/recreation steps.
- Clarified that cooldown is consumed before a chance roll and that `ROARRDB` is account-wide.
- Documented the MIT license's historical copyright line without changing it.
- **Markdown-only edits:** no Lua, TOC, license or runtime behavior changed; no in-game testing was performed.

## Prior changes supported by Git

| Date | Evidence | Observed evolution |
| --- | --- | --- |
| **2025-11-22** | `438b0a2`, `d618976` | First TOC and ROAR Lua uploaded; initial header says based on BuxbrewCharge. The first code already used slot hooking, chance and cooldown. |
| **2025-11-23** | `2bb6ab8` | Cooldown command no longer capped at 60 seconds. |
| **2025-11-23** | `1157988` | A code revision introduced on/off and tutorial branches in the then-ROAR source. |
| **2025-11-23** | `2191768`, `1caaace`, `49d9621` | Visible transition and repeated package/identifier renaming from ROAR to ROARR, with files ultimately becoming `roarr.lua` and `roarr.toc`. |
| **2025-11-23** | `2270a96`, `3f308c8`, `8e4201e`, `ac623d1` | Deleted then re-created files, leaving the final ROARR layout and version 1.0. |
| **2025-11-23** | `d313677`, `3b3a27d` | README expanded from a brief note into usage and installation instructions, later renamed to ROARR terminology. |
| **2026-09-18** | `371fa98` | Client/provider wording generalized to Vanilla 1.12 terminology. |
| **2026-10-26** | `f479c1a`, `87d225f`, `dfda278`, `ed1dc5d`, `9af91ca` | Author-credit and initial documentation edits completed before this expansion. |

The commit history supports the sequence of modifications but does not tell us why a particular intermediate filename was changed or why files were briefly deleted. Don't invent those motives.
