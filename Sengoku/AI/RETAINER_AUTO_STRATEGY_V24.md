# Sengoku v24 - Retainer Auto-Resolution Strategy

Purpose:
- Define deterministic, testable auto-resolution policies for Retainer actions.
- Keep simulator behavior explainable, tunable, and aligned with rules clarifications.

Scope:
- Base retainers: `Sam`, `Ash`, `Cha/Tea`, `Soe`, `Shi`, `Ron`, plus `Uni` placeholder.
- Applies to legal-move generation and AI move selection.

## 1) Priority System (normalized)

Use numeric priorities in strategy rules:

- `PRI-0` = Mandatory (must execute / must satisfy)
- `PRI-1` = Critical / highest priority
- `PRI-2` = Medium priority
- `PRI-3` = Low priority
- `PRI-4` = Random-choice fallback
- `PRI-5` = Do not execute (explicitly avoided)

Intake/implementation flow:
- Incoming notes are tagged as `ADD-X` (`X` in `0..5`).
- After strategy intake, convert `ADD-X` -> `PRI-X`.
- When behavior is implemented in code, mark as `PRI-X*`.

Legacy marker mapping:
- `(*)` -> `PRI-1`
- `(**)` -> `PRI-2`
- `(***)` -> `PRI-3`
- `(****)` -> `PRI-4`

## 2) Dumbness Model (controlled randomness)

Definition:
- `dumbnessPct` controls AI selection depth (`top-X`) before random pick.

Skill presets:
- Expert: `<4%` (recommended `2-4%`)
- Intermediate: `4-14%`
- Novice: `15-25%`

Operational rule:
1. Generate all legal moves.
2. Score moves by strategy priorities and behavior style.
3. Sort by score descending and build a tiered candidate pool:
   - include full score tiers until `top-X` is reached;
   - if top tier alone is larger than `X`, use the full top tier only.
4. Pick random among candidates in that pool.
5. Higher `dumbnessPct` increases `X`, so lower-score tiers can be included.

Implementation note:
- In simulator configuration, `mistakeChancePct` is treated as `dumbnessPct` for depth expansion.
- `intentionalErrorChancePct` remains separate (deliberate stress-test behavior).

## 3) Global Principles

1. Legality first:
- Every auto action must pass the same blockers as manual play.

2. Enemy-first removal:
- For `KILL/REMOVE/DESTROY`, target enemy cards/tokens first.
- `PRI-1*`: adopted in code for Samurai/Ashigaru/Shinobi selection flow. [A101] [code-logic]

3. Own-target fallback (`Remove if Needed`):
- Default: do not remove own cards/tokens.
- Own-target removal is allowed only when it materially unlocks a stronger plan.
- `PRI-1*`: adopted in code (`OwnRemovalFallbackReason` gate). [A102] [code-logic]
- Typical reasons:
  - no usable Numbered progression available and space must be opened for build path,
  - own unprotected face-down is a reveal risk for key structures,
  - own card/token blocks chain expansion or building evolution.

4. Chain-aware placement:
- For `PLACE_CHAINED`, priority is: selected legal target -> best connected legal target -> no-op.

5. Overlap priorities:
- `OVERLAP` should maximize board impact, not only immediate legality.
- `Sam`: overlap own border card to open enemy-line breaks.
- `Soe`: central-zone overlap is often strong for expansion denial/disruption.
- `Ron`: replacement should consider pile outcome value (recover or remove impact cards).

6. Explainability:
- Log short reason for auto target selection and fallback usage.
- Runtime action log IDs: each `LogTurnStep` entry carries a unique event id token `[E#]` for quick cross-reference.
- AI choice log includes explicit rule-id keys from scoring config (for example `rules: convert.prevent_end_waste, protection.connected_target`).
- Reference mapping for adopted rules is maintained in:
  - `AI/RETAINER_STRATEGY_MARKERS_TRACKER.md` -> section `Runtime Trace Map ([E#])`.
- This document also uses stable rule reference tags `[A101..]` on PRI bullets.
  - They are static strategy IDs for discussion/review.
  - They are different from runtime event IDs `[E#]` emitted in logs.
  - Implemented AI-config rules also carry a second tag `[config_key=value]`.
  - Non-config behavior gates are tagged as `[code-logic]`.

## 4) Global Action Heuristics

### 4.1 Numbered card usage
- `PRI-0*`: Numbered cards must never stack on Retainer top cards. [A103] [code-logic]
- `PRI-0*`: Numbered cards in Imperial Zones cannot be overlapped by other Numbered cards (Retainer overlap/replacement only). [A172] [code-logic]
- `PRI-1*`: when no other legal/valuable card action exists. [A104] [base.play_numbered=7]
- `PRI-1*`: when there is a position connected to the chain of command where the card can be placed. [A105] [board.connected_target=7]
- `PRI-1*`: penalize unconnected Numbered placement when at least one legal connected Numbered placement exists. [A105] [numbered.unconnected_when_connected_exists_penalty=22]
- `PRI-1*`: when it reconnects a broken Chain of Command. [A106] [board.chain_extend=7]
- `PRI-1*`: when it legally occupies an Imperial Zone. [A107] [numbered.imperial_occupation=11]
- `PRI-1*`: when no own Numbered is on board and `Koku > 3`. [A108] [numbered.no_owned_board_high_koku=11]
- `PRI-2*`: when it exactly completes a zone footprint. [A109] [board.zone_connected=11]
- `PRI-2*`: when own Numbered board presence is still low and expansion space is wide. [A110] [board.completion_unconnected=4]
- `PRI-1*`: when a card can be in a place face-up or face-down, prefer face-up. [A111] [numbered.face_up_prefer=11]
- `PRI-1*`: avoid playing cards when hand size is `2` and active player has `<3 Koku` (low-koku hand-floor caution). [A112] [hand.low_koku_two_cards_penalty=11]
- `PRI-3*`: overlap on an own stack already at depth `>=3` is extremely rare. [A173] [numbered.overlap_same_clan_depth3_penalty=4]
- `PRI-3*`: first overlap using a face-down Numbered on own stack is extremely rare. [A174] [numbered.overlap_first_with_facedown_penalty=4]
- `PRI-2*`: overlapping an own first-layer face-down with face-up Numbered is more practical. [A175] [numbered.overlap_first_facedown_to_faceup_bonus=7]

### 4.2 Face-down usage
- `PRI-1*`: when no other legal/valuable card action exists. [A113] [facedown.no_faceup_options=11]
- `PRI-1*`: when it reconnects chain and no Numbered can do it. [A114] [facedown.chain_reconnect_no_faceup=11]
- `PRI-2*`: when it helps complete a zone and no better face-up play exists. [A115] [facedown.zone_no_faceup=7]

### 4.3 Protection placement usage
- `PRI-1*`: when target card is threatened (adjacent to `>2` enemy-adjacent cells/cards). [A116] [protection.threatened_target=11]
- `PRI-1*`: when conversion/build tempo is high (`Koku >= 4`) and protection enables immediate progress. [A117] [convert.enable_protection_pipeline=11]
- `PRI-1*`: when +2 additional protection would unlock Castle that leads toward Capital timing. [A118] [protection.castle_trigger_setup=11]
- `PRI-2*`: when +2 additional protection unlocks Castle in general. [A119] [protection.castle_progress=7]
- `PRI-2*`: when `Koku > 2` and proactive protection tempo is useful. [A120] [protection.proactive_high_koku=7]
- `PRI-0*`: when pending protection placements exist (from convert/effects), resolve them immediately before hidden-info/card-play/extra convert actions. [A176] [code-logic]

### 4.4 Koku overflow handling
- `PRI-1*`: when current `Koku` is already at cap (`5`), convert before ending turn to avoid immediate waste. [A166] [convert.at_cap_priority=11]
- `PRI-1*`: when projected end-of-turn `Koku` (current + expected income) exceeds cap and conversion is legal, prioritize conversion. [A167] [convert.prevent_end_waste=11]

### 4.5 Visit Emperor priority (timing curve)
- Early game (`turn <= 4`): value `0` (do not prioritize).
- Mid curve:
  - `turn 5`: low (`~4`)
  - `turn 6`: medium (`~7`)
  - `turn 7-8`: peak (`~10-11`)
- Late decay:
  - `turn 9`: medium (`~7`)
  - `turn 10`: low (`~4`)
  - `turn 11`: very low (`~2`)
  - `turn 12`: near-zero (`~1`)
  - `turn >= 13`: `0`
- Extra constraints:
  - if `deck < 4`: force value `0`,
  - if discard is too small, reduce value,
  - if `Emperor` already used: value `0`.

### 4.6 Endgame objective basis (to drive future AI evaluation)
- Current clarified final-scoring components:
  - `+1` per face-up card in play (including Daimyo),
  - `+1` per completed zone,
  - `+1` per completed line,
  - `+1` per controlled Imperial zone,
  - `+1` per Castle,
  - `+2` per Capital,
  - `+4` for Shogun status.
- Strategy implication:
  - future move-evaluation should optimize projected delta on these components, not only local tempo/safety heuristics.

### 4.7 Hidden-info stability rules
- `PRI-0*`: in the same turn and same cell, block `Declare Error`/`Reveal` ping-pong loops (no repeat declare, no repeat reveal, no reveal-after-declare, no declare-after-reveal). [A177] [code-logic]
- `PRI-2*`: if AI has no legal move in MAIN and hand is still `>2`, allow deterministic fallback discard (lowest tactical value card) to avoid deadlock. [A178] [code-logic]
- `PRI-3*`: revealing own face-down card is an error path and should be strongly penalized; allow only as rare intentional mistake behavior. [A179] [hidden_info.own_reveal_error_penalty=22]
- `PRI-3*`: if intentional-error roll triggers, self-reveal may re-enter candidate pool at low frequency. [A179] [hidden_info.own_reveal_error_mistake=22]
- `PRI-1*`: when token capacity is full, `Declare Error` should be heavily penalized (no reward capacity) to avoid non-productive loops. [A184] [error.no_token_capacity_penalty=22]
- `PRI-1*`: when MAIN legal moves are hidden-info only and hand is `>2`, AI should fallback-discard deterministically to recover turn flow. [A185] [code-logic]
- `PRI-1*`: for AI seats with `intentionalErrorChancePct=0`, own face-down reveal candidates are filtered out when alternative legal moves exist. [A186] [code-logic]

## 5) Per-Card Strategy

Notation:
- `AP` = active player.
- `OP1/OP2` = other players (typical targets/rivals).

### Samurai (`Sam`)

`A1` (Place chained/overlap own, then remove adjacent)
- Baseline legality:
  - place with `PLACE_CHAINED_OVERLAP_OWN`.
  - remove adjacent unprotected top card (non-Daimyo) or remove adjacent token.
- Priorities:
  - `PRI-1*`: when chain cannot expand otherwise and overlap-own-at-border can remove key adjacent blocker. [A121] [retainer.sam.a1.chain_break=11]
  - `PRI-2*`: when opponent has critical adjacent protection token (especially near Castle/Capital timing). [A122] [retainer.sam.a1.token_threat=7]
  - `PRI-3*`: general disruption when no direct expansion gain. [A123] [retainer.sam.a1.disrupt=4]
  - `PRI-1*`: when one placement can threaten multiple adjacent removals (cards/tokens), prioritize multi-threat swing. [A180] [retainer.sam.a1.multi_threat_combo=11]

`A2` (Reactive interrupt)
- Baseline:
  - queued one-block interrupt on next opponent Retainer action.
- Priorities:
  - `PRI-1*`: stop destructive actions that would break your zone/chain or remove high-value pieces. [A124] [retainer.sam.a2.prevent_direct_threat=11]
  - `PRI-2*`: stop token-steal or overlap that would heavily damage your tempo. [A125] [retainer.sam.a2.prevent_token_steal=7]
  - `PRI-2*`: protect against `Shinobi A2` hand disruption when hand quality/size is high. [A126] [retainer.sam.a2.prevent_shinobi_handhit=7]
  - `PRI-3*`: stop attacks on another player only when attacker is clearly runaway leader. [A127] [retainer.sam.a2.runaway_check=4]

### Ashigaru (`Ash`)

`A1` (Place chained, remove up to 2 adjacent unprotected Numbered/FaceDown)
- Priorities:
  - `PRI-1*`: when removal opens immediate expansion into freed cells. [A128] [retainer.ash.a1.open_expansion=11]
  - `PRI-2*`: when removal reduces opponent zone completion risk. [A129] [retainer.ash.a1.zone_denial=7]
  - `PRI-3*`: tactical cleanup without immediate follow-up gain. [A130] [retainer.ash.a1.cleanup=4]
  - `PRI-1*`: when two removals are available from the same placement, prioritize double-remove value. [A181] [retainer.ash.a1.double_remove_value=11]

`A2` (Look 4, keep 1, route others top/bottom)
- Priorities:
  - `PRI-1*`: when deck is short and key retainers (`Tea/Cha`, `Shi`, `Sam`) are still missing from hand. [A131] [retainer.ash.a2.key_missing_short_deck=11]
  - `PRI-2*`: when hand is mostly Numbered and tactical retainer is needed. [A132] [retainer.ash.a2.numbered_heavy_hand=7]
  - `PRI-3*`: general filtering when no high-impact board move is available. [A133] [retainer.ash.a2.no_high_impact=4]

### Chajin / Tea Master (`Cha` / `Tea`)

`A1` (Draw 2 once/turn)
- Priorities:
  - `PRI-1*`: no Numbered in hand and zone completion is near. [A134] [retainer.cha.a1.no_numbered=11]
  - `PRI-1*`: late game (final-turn tempo/value). [A135] [retainer.cha.a1.late_game=11]
  - `PRI-2*`: early phase if Imperial position race is active. [A136] [retainer.cha.a1.early_imperial_race=7]
  - `PRI-2*`: when hand contains other retainers that synergize with extra draw. [A137] [retainer.cha.a1.retainer_synergy=7]
  - `PRI-2*`: when deck is still deep and discard has value (`deck>=8`, `discard>=2`), draw window is favorable. [A182] [retainer.cha.a1.deck_value_window=7]

`A2` (Draw 1 + immediate play)
- Priorities:
  - `PRI-1*`: after turn 10 when high-impact retainers are still underdrawn. [A138] [retainer.cha.a2.late_key_underdrawn=11]
  - `PRI-2*`: after turn 6 when retainer density seen is low. [A139] [retainer.cha.a2.mid_low_retainer_density=7]
  - `PRI-3*`: generic tempo fishing when no direct high-value action is legal. [A140] [retainer.cha.a2.no_high_impact=4]

### Sohei (`Soe`)

`A1` (Place anywhere + overlap)
- Priorities:
  - `PRI-1*`: overlap in central zones on legal `Numbered`/`Soe`/`FaceDown` to disrupt control. [A141] [retainer.soe.a1.central_overlap=11]
  - `PRI-1*`: overlap near border cells that connect to opponent chain and can cut expansion. [A142] [retainer.soe.a1.chain_cut_overlap=11]
  - `PRI-2*`: deny favorable follow-up cells even without immediate scoring swing. [A143] [retainer.soe.a1.deny_followup=7]

`A2` (Retrieve top discard)
- Priorities:
  - `PRI-1*`: top discard is high-impact retainer (`Sam`, `Soe`, `Shi`). [A144] [retainer.soe.a2.top_high_impact=11]
  - `PRI-2*`: top discard is utility retainer (`Ash`, `Ron`). [A145] [retainer.soe.a2.top_utility=7]
  - `PRI-2*` negative rule: avoid when top discard is `Cha` and board tempo is low-value. [retainer.soe.a2.avoid_cha_low_tempo_penalty=7]

### Shinobi (`Shi`)

`A1` (Targeted removal: Retainer or FaceDown only)
- `PRI-0*`: never remove face-up Numbered with Shinobi A1. [A146] [code-logic]
- Priorities:
  - `PRI-1*`: remove enemy special/face-down occupying Imperial zones. [A147] [retainer.shi.a1.enemy_imperial=11]
  - `PRI-2*`: remove protected enemy special near your chain before it snowballs. [A148] [retainer.shi.a1.protected_near_chain=7]
  - `PRI-3*`: cleanup removal when stronger direct expansion line is unavailable. [A149] [retainer.shi.a1.cleanup=4]

`A2` (Disrupt hand + delayed draw)
- Priorities:
  - `PRI-1*`: when opponent board share is runaway (`~40%` above others) and deck depth still high. [A150] [retainer.shi.a2.runaway_board=11]
  - `PRI-1*`: when you need next-turn hand boost and current turn played-card count is low. [A151] [retainer.shi.a2.low_playcount_boost=11]
  - `PRI-1*`: use face-down trap mode when hidden pressure is valuable. [A152] [retainer.shi.a2.trap_mode=11]
  - `PRI-3*`: trap pressure when table already has many face-down cards (`>3`) and info chaos is useful. [A153] [retainer.shi.a2.facedown_pressure=4]
- Discard preference:
  - retainers first, then high-impact Numbered planning cards.

### Ronin (`Ron`)

`A1` (Replace unprotected non-Ronin top)
- Priorities:
  - `PRI-1*`: replace enemy card near your chain that threatens zone/chain integrity. [A154] [retainer.ron.a1.chain_threat_replace=11]
  - `PRI-1*`: replace key occupant in/near Imperial pressure lines. [A155] [retainer.ron.a1.imperial_line_replace=11]
  - `PRI-2*`: replacement for local tactical cleanup when free cells are scarce. [A156] [retainer.ron.a1.scarce_cells_cleanup=7]

`A2` (Steal up to 2 tokens, compensation to total target gain 2)
- `PRI-1*`: implemented compensation rule (`2` total gain: `2+0`, `1+1`, or `0+2`). [A157] [retainer.ron.a2=11]
- Priorities:
  - `PRI-1*`: early game (`turn < 5`) when token economy is sparse. [A158] [retainer.ron.a2.early_sparse_economy=11]
  - `PRI-1*`: when you are at `2 Castles` and one more protection step materially accelerates Capital path. [A159] [retainer.ron.a2.castle_to_capital=11]
  - `PRI-1*`: use face-down trap mode for hidden token-swing threat. [A160] [retainer.ron.a2.trap_mode=11]
  - `PRI-1*`: when opponents have connected protection/build pressure (`>=2` connected token pressure), prioritize denial swing. [A183] [retainer.ron.a2.connected_build_denial=11]
  - `PRI-2*`: when opponents have 1-2 exposed board tokens and you can convert swing immediately. [A161] [retainer.ron.a2.exposed_enemy_tokens=7]
  - `PRI-3*`: pressure play when table has many face-down cards and visibility is low. [A162] [retainer.ron.a2.facedown_pressure=4]

### Uni (`Uni`)

`A1/A2`:
- Placeholder until official text is locked.

## 6) Known Gaps

1. Trap reveal windows for `Shi/Ron` are now implemented in baseline; further UX polish (manual selection popups) remains optional.
2. `Sam A2` uses queued interrupt policy (not live pop-up reaction window).
3. Deep stack restoration semantics beyond top-layer metadata are still partial.
4. `Cha A2` special boost metadata (`+2 up to cap`) still pending final lock.



### 7 End phase
- `PRI-1*`: `Declare Error` has priority over `Go to END` when visible duplicate errors are present on board. [A163] [error.visible_fix_priority=11]
- `PRI-0*`: if no visible duplicate errors are present, phase progression to `END` is allowed/preferred. [A164] [phase.end_when_clean_bonus=4]
- `PRI-0*`: END-phase full flow is implemented as refill -> income -> pass hand; optional auto-pass after END resolve is supported by runtime toggle. [A165] [code-logic]
- `PRI-1*`: avoid `Go to END` when projected Koku overflow exists and conversion is still legal in MAIN. [A168] [phase.end_koku_waste_penalty=11]
- `PRI-1*`: avoid playing penultimate card (`2 -> 1`) without strong reason (chain/zone/line progress). [A169] [hand.penultimate_no_reason_penalty=22]
- `PRI-1*`: prioritize Castle build when at `2 Castles` and legal path to Capital timing exists. [A170] [build.castle_capital_path=11]
- `PRI-2*`: prefer early Market stabilization when `Koku` is low and Market not built. [A171] [build.market_early_economy=7]

## 8) Proposed Gameplay Strategies (PROP-X, pending ADD-X)

- `PROP-1`: `Samurai A1` evaluate combined swing (`adjacent removable cards + token threat + zone/line denial`) before selecting target.
- `PROP-2`: `Shinobi A2` target priority by projected short-term score growth (`next 1-2 turns`) rather than static board share only.
- `PROP-3`: `Sohei A1` overlap policy should avoid self-blocking build paths (especially near own 2-castle state).
- `PROP-4`: `Ronin A1` should score stack replacement by “pile value delta” (recover-own useful card vs deny-opponent useful card).
- `PROP-5`: `Tea/Cha A2` should prefer immediate-play candidates that unlock mandatory build/protection states this turn.
- `PROP-6`: global Numbered placement should include opponent-counterplay risk score (how easily adjacent enemies can break the new line).
