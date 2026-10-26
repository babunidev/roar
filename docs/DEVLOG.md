# roar — development journal

**Author:** Babuni.dev

## Retrospective source reading — 2026-10-26

An early ROARR add-on that randomly plays built-in battle emotes when a configured action-slot button is pressed. The source shows its concrete form: roarr.lua handles UseAction, watch mode, cooldown, chance, on/off state and ROARRDB; roarr.toc declares Vanilla 1.12. Player action triggers a probabilistic flavor reaction; combat execution itself remains unchanged.

No dated original design conversation was present in the inspected files. This is a reconstruction from existing source, not a claim about a complete development chronology. Babuni.dev is credited for the project; AI assisted this documentation and analysis only. The README still contains an older author alias in its bottom attribution paragraph; compare source and README, and verify in WoW 1.12.
