# ROARR — development collaboration rules

**Creator and project author:** Babuni.dev.

## Protect the work's identity

The current repository is `babunidev/roar`. The installed addon is **ROARR** with files `roarr.lua` and `roarr.toc`, slash command `/roarr` and DB `ROARRDB`. A **different** GitHub repository named `roarr` and the separate **RoarForever** project must not be silently merged into this history.

The core experience is player-triggered battle emotes, with configurable chance, cooldown and enable state. Do not convert it into combat automation or a different visual system without explicit direction from Babuni.dev.

## Standards

1. Before changing anything, inspect `README.md`, `CONCEPT.md`, `docs/DEVLOG.md`, `docs/DECISIONS.md`, `roarr.lua` and `roarr.toc`.
2. Record **creator direction**, **AI proposals**, **accepted/rejected alternatives**, **actual changes**, **commit references** and **verification evidence** separately.
3. Use dated Git diffs for historical claims. Do not invent reasons for repeated November 2025 renames, deletions or code revisions.
4. Maintain Babuni.dev credit, but **preserve the existing MIT license** and its historical 2025 copyright line until appropriate ownership clarification; never rewrite legal attribution speculatively.
5. Treat the code as evidence of implementation, not as proof of live WoW compatibility. List untested edge cases.
6. For future changes, keep README, CHANGELOG, ARCHITECTURE, DEVLOG, DECISIONS, DESIGN and CONTENT consistent with code.
7. Avoid private chat archives, player names, credentials and unapproved historical excerpts in public docs.

## Implementation checks

- Stay compatible with World of Warcraft 1.12 and Lua 5.0 unless the creator changes the requirement.
- Review global `UseAction` hook chaining with other addons.
- Preserve saved preferences in `ROARRDB`; check initialization and logout behavior.
- Know that a failed chance roll currently still starts the cooldown.
- Verify rather than assume all built-in emote tokens exist on the user's client.
- Run and report actual tests before marking gameplay verified.
