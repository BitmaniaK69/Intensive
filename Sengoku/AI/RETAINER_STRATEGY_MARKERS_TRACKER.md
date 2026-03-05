# Retainer Strategy Markers Tracker (v24)

Purpose:
- Collect `(*) / (**) / (***)` notes from playtest/rule clarifications.
- Keep a single status board from note -> strategy decision -> code behavior.

## Marker Meaning

- Preferred strategy levels (current):
  - `PRI-0` mandatory
  - `PRI-1` critical / highest priority
  - `PRI-2` medium priority
  - `PRI-3` low priority
  - `PRI-4` random fallback
  - `PRI-5` do not execute
- Intake format:
  - incoming notes use `ADD-X` (`X=0..5`)
  - after intake normalize to `PRI-X`
  - after implementation mark `PRI-X*`
- Legacy markers still accepted:
  - `(*)` -> `PRI-1`
  - `(**)` -> `PRI-2`
  - `(***)` -> `PRI-3`
  - `(****)` -> `PRI-4`

## Intake Workflow

1. Add marker note in your feedback/doc.
2. Copy into this table with a short ID.
3. Decide status:
- `Adopted in Code`
- `Planned`
- `Blocked by Rule Clarification`
- `Rejected`
4. If adopted, reference the code area.

## Runtime Trace Map (`[E#]`)

- `Action Log` entries now include a runtime token `[E#]`:
  - `LogTurnStep` lines: `N. [E#] ...`
  - `AI` scoring/choice lines: `[E#] ...`
- `[E#]` is sequential per match and resets on sandbox reset.
- Fast debug flow:
  1. Find the failing line by `[E#]` in Action Log.
  2. Read `rules: ...` in the AI choice line (when present).
  3. Map those rule keys to the RM item below.

### Rule-Key -> RM Quick Map

- `convert.at_cap_priority`, `convert.prevent_end_waste`, `phase.end_koku_waste_penalty` -> `RM-019`
- `convert.enable_protection_pipeline`, `convert.koku_overflow_guard`, `convert.capital_path`, `convert.castle_setup`, `protection.*`, `build.castle_capital_path`, `build.market_early_economy`, `phase.end_with_unspent_protection_penalty` -> `RM-014`
- `numbered.imperial_occupation`, `numbered.no_owned_board_high_koku` -> `RM-015`
- `facedown.no_faceup_options`, `facedown.chain_reconnect_no_faceup`, `facedown.zone_no_faceup` -> `RM-016`
- `hand.low_koku_two_cards_penalty`, `hand.penultimate_no_reason_penalty` -> `RM-012`
- `error.visible_fix_priority`, `phase.end_visible_error_penalty`, `phase.end_when_clean_bonus` -> `RM-011`
- `hidden_info.own_reveal_error_penalty`, `hidden_info.own_reveal_error_mistake` -> `RM-022`
- `error.no_token_capacity_penalty` -> `RM-023`
- `retainer.sam.a1.multi_threat_combo`, `retainer.ash.a1.double_remove_value`, `retainer.cha.a1.deck_value_window`, `retainer.ron.a2.connected_build_denial` -> `RM-024`
- `retainer.sam.a1.*`, `retainer.sam.a2.*`, `retainer.ash.a1.*`, `retainer.ash.a2.*`, `retainer.cha.a1.*`, `retainer.cha.a2.*`, `retainer.soe.a1.*`, `retainer.soe.a2.*`, `retainer.shi.a1.*`, `retainer.shi.a2.*`, `retainer.ron.a1.*`, `retainer.ron.a2.*` -> `RM-020`
- `retainer.shi.a2.trap_mode`, `retainer.ron.a2.trap_mode` -> `RM-021`

## Current Items

| ID | Marker | Source | Note | Status | Code/Doc Link |
|---|---|---|---|---|---|
| RM-001 | `PRI-1*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Prefer not removing own cards for Ashigaru/Samurai if action can resolve as placement + no-op. | Adopted in Code | `sengoku_v24_core.h`: Samurai/Ashigaru A1 switched to enemy-first with no-op when no enemy legal target. |
| RM-002 | `PRI-1*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Self-removal may be used only when it materially enables stronger follow-up (example: build path, defensive cleanup). | Adopted in Code | `sengoku_v24_core.h`: strategic own-target fallback gate (`OwnRemovalFallbackReason`) added for Samurai/Ashigaru; Shinobi A1 move generation now enemy-first with own-target fallback only when reason exists. |
| RM-003 | `PRI-1*` | User playtest feedback | `Samurai A1` must be able to remove adjacent unprotected card of any non-Daimyo type; token removal is alternative and may target Daimyo token. | Adopted in Code | `sengoku_v24_core.h`: Samurai A1 resolver switched to card-first, token fallback; token removal made legacy-safe for `plusProtection` states. |
| RM-004 | `PRI-1*` | User playtest feedback | `Ronin A2`: steal from opponent board cards; if stealable tokens are `<2`, grant direct compensation so target gain remains `2` (`1+1` or `0+2`). | Adopted in Code | `sengoku_v24_core.h`: Ronin A2 now board-first steal only, no supply/reserve steal, fixed target gain `2` with capacity cap. |
| RM-005 | `PRI-1*` | User playtest feedback | `Shinobi A1` cannot remove face-up Numbered cards (only Retainer or FaceDown targets). | Adopted in Code | `sengoku_v24_core.h`: added `IsShinobiA1TargetType` in both legality blocker and execution guard; impossible to remove face-up Numbered via Shinobi A1. |
| RM-006 | `PRI-1*` | User playtest feedback | Numbered cards must not stack on Retainer tops (example: Ronin). | Adopted in Code | `sengoku_v24_core.h`: `NumberedPlayCellBlocker` now rejects `cell.top.kind == Retainer` even when owned. |
| RM-007 | `PRI-1*/PRI-2*/PRI-3*` | User strategy iteration | AI move scoring should be additive by priority markers (e.g. `11+11+4+1`) and visible in move list. | Adopted in Code | `sengoku_v24_core.h`: `AiMovePriorityScore` + weighted PRI scoring; `sengoku_v24_panel.h`: per-move PRI shown in AI list with tooltip breakdown. |
| RM-008 | `PRI-1*` | User strategy iteration | Card moves connected to Chain of Command should rank higher; if they complete zone/line and are connected, they should rank highest. | Adopted in Code | `sengoku_v24_core.h`: `EvaluateMoveBoardImpact` + connected target / chain extension / connected zone-line completion boosts in AI scoring. |
| RM-009 | `PRI-4*` | User strategy iteration | AI should pick random from top-X weighted candidates (tier-based), where dumbness regulates depth X. | Adopted in Code | `sengoku_v24_core.h`: `ComputeAiDepthLimitFromMistakePct` + tiered pool selection in `PickAiMoveIndex`; `sengoku_v24_panel.h`: depth preview text in AI Analysis. |
| RM-010 | `PRI-1*` | User strategy iteration | `Visit Emperor` should be near-zero early, peak around turn 7-8, then decay after turn 11, with deck/discard sanity constraints. | Adopted in Code | `sengoku_v24_core.h`: `EvaluateVisitEmperorPriority`; runtime config source is TOML (`sengoku_v24_ai_priority_config.toml`). |
| RM-011 | `PRI-1*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Visible duplicate errors should be fixed before ending MAIN; if no visible errors, END transition is preferred. | Adopted in Code | `sengoku_v24_core.h`: `IsVisibleDuplicateErrorAtCell` / `HasAnyVisibleDuplicateError` + scoring keys `error.visible_fix_priority`, `phase.end_visible_error_penalty`, `phase.end_when_clean_bonus` (TOML-driven). |
| RM-012 | `PRI-1*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | With hand size `2` and low Koku (`<3`), avoid additional card plays unless strategically needed. | Adopted in Code | `sengoku_v24_core.h`: scoring raw penalty key `hand.low_koku_two_cards_penalty` (TOML-driven). |
| RM-013 | `PRI-0*` | User turn-flow update | END phase should not stall: support full END flow and automatic handoff after END resolve when configured. | Adopted in Code | `sengoku_v24_core.h`: `autoPassHandOnEndResolve` + unified `TryPassHandFromEndPhase`; `sengoku_v24_panel.h`: automation toggle UI; scenario JSON save/load updated. |
| RM-014 | `PRI-1*/PRI-2*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Autoplay should value conversion/protection/build progression (threat defense, castle setup, capital path, market economy) instead of only card placement. | Adopted in Code | `sengoku_v24_core.h`: added contextual scoring gates for `ConvertKoku`, `PlaceProtection`, `BuildCastle`, `BuildMarket`, and END-phase penalty with unspent legal protection opportunities; tuned via TOML keys. |
| RM-015 | `PRI-1*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Numbered expansion priorities should explicitly boost Imperial occupation and “no-owned-numbered + high Koku” recovery line. | Adopted in Code | `sengoku_v24_core.h`: scoring keys `numbered.imperial_occupation`, `numbered.no_owned_board_high_koku` integrated in move ranking (TOML-driven). |
| RM-016 | `PRI-1*/PRI-2*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Face-down should be selected when face-up numbered options are unavailable and for chain/zone fallback. | Adopted in Code | `sengoku_v24_core.h`: `HasAnyFaceUpNumberedPlayOption` + facedown-specific scoring keys (`facedown.no_faceup_options`, `facedown.chain_reconnect_no_faceup`, `facedown.zone_no_faceup`) in AI ranking. |
| RM-017 | `PRI-0*` | User debug workflow request | Add deterministic action identifiers in runtime log and expose rule-ids used by AI chosen move for faster playtest forensics. | Adopted in Code | `sengoku_v24_core.h`: `LogTurnStep` now prefixes `[E#]`; AI chosen-move log now includes `rules: ...` extracted from scoring keys. |
| RM-018 | `PRI-1*` | User playtest feedback | Ronin A1 must not be playable on empty cells; it is replacement-only on occupied legal targets. | Adopted in Code | `sengoku_v24_core.h`: `RetainerPlayCellBlocker` now rejects `Ron A1` on empty cells (`Ronin replacement requires occupied target`). |
| RM-019 | `PRI-1*` | User playtest feedback | Avoid Koku waste at end phase: AI should prioritize conversion when at/near cap and penalize ending turn with projected overflow when conversion is possible. | Adopted in Code | `sengoku_v24_core.h` + TOML: `convert.at_cap_priority`, `convert.prevent_end_waste`, `phase.end_koku_waste_penalty`. |
| RM-020 | `PRI-1*/PRI-2*/PRI-3*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` | Add contextual AI scoring for Retainer actions (`A121..A162`, excluding trap-only windows) using explicit TOML keys and doc-tag traceability. | Adopted in Code | `sengoku_v24_core.h`: retainer context scoring block in `ScorePossibleMoveForBehavior`; `sengoku_v24_ai_priority_config.toml`: new `retainer.*` point keys; runtime logs show `[Axxx]` tags via key mapping. |
| RM-021 | `PRI-1*` | `AI/RETAINER_AUTO_STRATEGY_V24.md` + user confirmation | Implement trap-mode reveal windows for `Shinobi A2` (`A152`) and `Ronin A2` (`A160`) with primary target = current revealer, including self-reveal error path. | Adopted in Code | `sengoku_v24_core.h`: trap metadata on face-down tops, trap-capable retainer face-down placement, reveal trigger resolver (`ResolveTrapOnReveal`), and `retainer.shi.a2.trap_mode` / `retainer.ron.a2.trap_mode` scoring; `sengoku_v24_ai_priority_config.toml` updated. |
| RM-022 | `PRI-3*` | User clarification | Revealing own face-down card is an error-path move: AI should heavily penalize it and allow only as rare intentional mistake according to behavior config. | Adopted in Code | `sengoku_v24_core.h`: `ScorePossibleMoveForBehavior` applies `hidden_info.own_reveal_error_penalty` + gated `hidden_info.own_reveal_error_mistake` bonus from `intentionalErrorChancePct`; `sengoku_v24_ai_priority_config.toml` contains both weights. |
| RM-023 | `PRI-1*` | Loop/stall stabilization | If token capacity is full, `Declare Error` should be heavily deprioritized to avoid rewardless reveal/error cycles. | Adopted in Code | `sengoku_v24_core.h`: `ScorePossibleMoveForBehavior` applies raw penalty key `error.no_token_capacity_penalty`; configured in `sengoku_v24_ai_priority_config.toml`. |
| RM-024 | `PRI-1*/PRI-2*` | Gameplay strategy depth | Add richer contextual scoring for Samurai/Ashigaru/Tea/Ronin tactical windows (multi-threat swing, double remove, deck-value draw window, connected build denial). | Adopted in Code | `sengoku_v24_core.h`: retainer scoring block now adds keys `retainer.sam.a1.multi_threat_combo`, `retainer.ash.a1.double_remove_value`, `retainer.cha.a1.deck_value_window`, `retainer.ron.a2.connected_build_denial`; TOML defaults added. |
| RM-025 | `PRI-1*` | Hidden-info safety | AI with `intentionalErrorChancePct=0` should not self-reveal own face-down cards if other legal moves exist. | Adopted in Code | `sengoku_v24_core.h`: `TryRunAiSingleMove` filters own-reveal candidates for AI seats unless no alternatives remain. |

## Proposed (PROP-X) Awaiting ADD-X

| PROP ID | Proposal | Status |
|---|---|---|
| PROP-1 | Samurai A1 combined swing score (cards/tokens/zone-line denial) | Pending user ADD |
| PROP-2 | Shinobi A2 target by projected short-term score growth | Pending user ADD |
| PROP-3 | Sohei A1 anti-self-blocking overlap near own build path | Pending user ADD |
| PROP-4 | Ronin A1 pile-value delta scoring (recover vs deny) | Pending user ADD |
| PROP-5 | Tea/Cha A2 immediate-play unlock priority (mandatory build/protection) | Pending user ADD |
| PROP-6 | Numbered global placement with opponent-counterplay risk score | Pending user ADD |

## Notes

- When you send new clarifications, prefix with marker and card/action context.
- I will append them here and mirror outcome in `AI/RETAINER_AUTO_STRATEGY_V24.md`.
- Quick scan command:
  - `rg -n "\\(\\*\\)|\\(\\*\\*\\)|\\(\\*\\*\\*\\)" AI`
