# Sengoku v25 - Manual Writer Packet

Current packet date:

- `2026-04-23`

Use these files in this order.

## 1) Primary Rule Authority

- `AI/v25/RulesV25-Final.md`

This is the current source of truth for the rules.

Manual-writing note:

- Use the active rules chapters and the Retainers appendix.
- `RulesV25.md` and `RulesV25-addOns.md` are historical source drafts only.

## 2) Secondary Writing Aid

- `AI/v25/sengoku_rulebook_v25_play.md`

Use this as a shorter, cleaner play-facing summary.
It is useful for pacing, section priority, and simpler wording, but it is not above `AI/v25/RulesV25-Final.md`.

## 3) Internal Quick Reference

- `AI/v25/TURN_FLOW_RECAP_V25.md`

This file is aligned to the current turn flow and endgame logic, but it is still a recap, not the formal rule authority.
Use it only as a shorthand timing/reference sheet.

## 4) Card Text Support

- `AI/v25/actions_by_clan.md`

Use this only as a compact Retainer-action helper.
If its wording ever conflicts with `AI/v25/RulesV25-Final.md`, follow `AI/v25/RulesV25-Final.md`.

## 5) Technical Support Only

- `AI/v25/RETAINER_ACTIONS_MATRIX_V25.md`

This is a simulator/implementation reference for Retainer actions.
It is useful for card-behavior cross-checking, but it is not a manual-writing source and should not drive wording/style decisions.

## Current locked clarifications already reflected in the source files

- Final card terms use `Shinobi`, `Sohei`, and `face-down`.
- `Chain / Chain of Command`, `Near your chain`, and `Adjacent` are standardized in the glossary.
- Shogun timing is immediate when a valid connected Capital is formed.
- Shogun scoring during Imperial Summons is ordered: `+4 / +3 / +2 / +1 / +1 / ...`.
- `Market = 2 Protection`, `Castle = 3 Protection`.
- Gained Protection must be placed immediately if legal; otherwise it is discarded to supply.
- Trap effects target the revealer first whenever the printed effect allows it.
- Allied players may not Reveal each other's face-down cards unless a rule/card explicitly allows it.
- Remove/replace-style effects cannot target a protected top card unless a rule/card explicitly says otherwise.
- `Ronin A1` targets the unprotected top non-Ronin card, replaces it, returns that card, then discards/returns the rest of the stack.

## Do Not Use As Rule Authority

- Any `v24` packet files
- Old draft/history/change-tracking files
- Historical playtest notes below the formal rulebook separator

These materials may contain legacy wording or outdated rule paths.

## Working Rule

If two files disagree, follow:

1. `AI/v25/RulesV25-Final.md`
2. `AI/v25/sengoku_rulebook_v25_play.md`
3. `AI/v25/TURN_FLOW_RECAP_V25.md`

## Suggested Share Packet

If you need one deliverable, share this set:

1. `AI/v25/README_FOR_MANUAL_WRITER.md`
2. `AI/v25/RulesV25-Final.md`
3. `AI/v25/sengoku_rulebook_v25_play.md`
4. `AI/v25/TURN_FLOW_RECAP_V25.md`
5. `AI/v25/actions_by_clan.md`
6. `AI/v25/RETAINER_ACTIONS_MATRIX_V25.md`
