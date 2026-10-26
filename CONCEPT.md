# ROARR — concept and creative direction

**Creative author:** Babuni.dev  
**Package:** `roarr.lua` / `roarr.toc` within the repository named `roar`.

## The experience

ROARR adds a moment of visible character expression to an action the player already chooses to make. Pressing a watched action slot may lead to an in-game ROAR, CHARGE, CHEER, BORED or FLEX emote. The effect is deliberately light: a bit of mood, bravado, impatience or celebration rather than another combat mechanic.

The **act of playing** supplies the timing. ROARR does not scan the combat log or automate spell choices; it reacts to the player's button press. Two controls shape how present that response feels: the probability of a reaction and the minimum interval between opportunities. The addon can also be turned off without losing the setup.

## Relationship to earlier work

This origin is unusually clear in an early **2025-11-22 Lua source comment**: the first ROAR version was “Based on BuxbrewCharge, rewritten as ROAR with /roar slash command.” That is direct code evidence of an implementation lineage. The present ROARR is a **built-in-emote** addon, unlike Buxbrew's larger pool of bespoke written `EMOTE` sentences.

This does not prove a recovered conversation in which every design choice was individually proposed or accepted. Babuni.dev is the project author; the assistance behind the first historical code and the reasons for each rename are not documented with a full dialogue.

## Creative boundaries

- Character presence, not ability automation or gameplay advantage.
- Five recognizable built-in WoW emotes, not a custom sound engine.
- Easy slot discovery through `/roarr watch`, no permanent UI clutter.
- Chance and cooldown make reactions intermittent; switch-off is deliberate and reversible.
- Chat commands and account-wide preferences keep it a small script.

The current source starts the cooldown **before** the chance roll. Consequently, a failed roll still delays the next opportunity. This behavioral detail is documented as implemented; whether that rhythm matches the creator's ideal is an open design question, not a newly approved change.

## Canonical identity boundaries

`roar` (this GitHub repository), `roarr` (installed addon identity and also a separate repository in the audit), and `RoarForever` (another project) must remain distinct unless the creator explicitly establishes how they relate. Shared thematic naming alone does not make them the same codebase or development timeline.
