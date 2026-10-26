# ROARR — development journal and the origin of the `roar` repo

**Project author / creative director:** Babuni.dev  
**Preparation date:** 2026-10-26. This account uses the repository README, committed source, and dated Git diffs. It is a **retrospective reconstruction**, not a recovered verbatim design conversation.

## 22 November 2025: from the BuxbrewCharge pattern to ROAR

The earliest visible source commit, `d618976` on **2025-11-22**, begins with an unusually useful attribution of code lineage: it states that ROAR was **based on BuxbrewCharge and rewritten** under a `/roar` command. That is more concrete than merely noticing the two addons both monitor an action slot.

The first implementation already contained much of the idea: select an action-bar slot, intercept `UseAction`, check an interval and chance, then invoke a game-supplied emote. Its small token pool mixed the grandiosity of ROAR and CHARGE with CHEER, FLEX, and the wonderfully incongruous BORED. The concept was a fast, lightweight expression of combat mood rather than a custom combat system.

The earliest source initially used `ROARDB` and `/roar`, with a 20-second default cooldown visible in that first snapshot. These are historical facts of that initial code, not the settings of the current ROARR release. The original conversations that produced the idea are not preserved in this repo; the project remains credited to Babuni.dev.

## 23 November 2025: short-cycle toolmaking and configurability

A dense group of commits on **2025-11-23** shows the addon being revised rapidly. One visible diff (`2bb6ab8`) removed an upper limit of 60 seconds from the cooldown command. Another (`1157988`) introduced on/off and tutorial branches into the earlier ROAR interface. The public README grew from a one-line description into a real installation guide explaining the watched slot, chance, cooldown and enable switch.

That matters for the interaction design. The tool moved beyond “an emote appears on a button” toward “a player can discover the button's ID, decide how often expression is welcome, and switch the feature off when needed.” This is the implemented direction evident in code and documentation; attributing particular proposals or approvals to an unrecorded conversation would be speculation.

## A day of names: ROAR, ROARR, and the installed package

The same date is notable for repeated renames. Git shows `roar.lua` and `roarr.lua`, matching TOCs, command namespaces and saved-variable names being revised across several commits. One intermediate revision (`2191768`) even contains `/raorr` in its diff, illustrating that some intermediate code states were not necessarily the intended final user interface.

Later commits renamed both code and manifest, briefly deleted the `roarr` pair (`2270a96`, `3f308c8`) and then re-created them (`8e4201e`, `ac623d1`). The resulting package is **ROARR** version **1.0**, with files `roarr.lua` and `roarr.toc`, command `/roarr`, and `ROARRDB`.

It would be tempting to smooth all of this into a single polished “rebranding decision.” The commits do not justify that story. What they show is exploratory iteration and a final stable naming scheme. The precise reason for each swap, typo and temporary deletion remains unverified.

## What the finalized code actually does

When the player presses the watched slot, the current addon runs a gated attempt at one of five built-in emotes. The default cooldown is **6 seconds**, chance **100%**, and the feature starts enabled. A missed chance roll still sets the last-attempt clock: the player must wait again before another chance roll. That subtle distinction is easy to miss in a quick README description and is now explicitly preserved in the technical record.

The source uses a global `UseAction` wrapper, lazily reads account-wide preferences, and offers chat commands for configuration and diagnostics. Its content comes from built-in WoW emotes, not bespoke dialogue, sound assets or animation rigs. It does not change a character's attack or make tactical combat decisions.

## 2026: wording, credit and preservation

A **2026-09-18** change (`371fa98`) generalized client descriptions to avoid tying support claims to one specific private-server provider. On **2026-10-26**, several commits updated displayed authorship to **Babuni.dev** and added a short documentation scaffold. The repository's separate MIT license retains an earlier copyright statement naming **Elexior**; this expansion leaves that legal file intact and flags attribution for future clarification without inventing the relationship.

This documentation pass inspected the code and selected dated diffs and replaced the sparse scaffold with a detailed user guide, creative concept, interaction design, content register, architecture, decision record, roadmap, and human–AI attribution method. AI contributed research, analysis, drafting and the repository documentation commit **only**. It did not originate the project, approve new game behavior, modify `roarr.lua`, or run the addon in a client.

## The honest remaining questions

The creator has not yet indicated, in available evidence, whether a failed chance roll *should* consume the cooldown, whether sharing one watched slot across the account is desirable, or how this original `roar` repository should sit beside a separate `roarr` repository and the more recent RoarForever line. These questions belong in the continuing human–AI collaboration and the eventual portfolio retrospective.

**Verified through repository evidence:** dates and file renames, final code structure, 5 tokens, default settings, saved-variable design, MIT file presence. **Not verified:** specific motivations behind all renames, final WoW runtime behavior, player reception, cross-addon compatibility and the LICENSE copyright relationship.
