# Sengoku V24 Simulator - Phase Plan & Iteration Tracker

Purpose:
- Track implementation phases for the local desktop simulator (single-machine, same-screen playtest tool).
- Keep development aligned with `RulesV24` and clarifications collected in `AI/SIMULATION.md`.
- Allow iterative compile/test/fix cycles with explicit user approval before moving to the next phase.

Scope (current target):
- A local simulator for testing Sengoku v24 gameplay and balance.
- Not online multiplayer (that is a later phase).
- Supports human-assisted play, designer-driven simulation, and AI-controlled players with behavior profiles.

## Workflow Rules (agreed)

Status vocabulary:
- `TODO`
- `IN PROGRESS`
- `IMPLEMENTED - WAITING FEEDBACK`
- `DONE (USER OK)`

Rules:
- A phase can contain multiple steps.
- Steps may be implemented in parallel when they do not conflict.
- A phase is complete only when **all** steps are `DONE (USER OK)`.
- No implicit OK: a step is marked `DONE (USER OK)` only after your explicit confirmation for that specific step.
- After a phase is complete and you confirm, **you** decide whether/when to commit.
- We do not move to the next phase without your explicit OK.

Configuration persistence principle:
- Any option added to a `Configuration` panel should be considered `save/load-capable` by design (scenario creation workflow), even if persistence is implemented in a later phase.
- Temporary debug/tool options may remain non-persisted at first, but they should be explicitly tagged as such.

## Phase 1 - UX Foundation (Global vs Personal Controls, Readability)

Goal:
- Make UI ownership clear: one active turn player, optional focused/inspected player board.
- Separate global controls from per-player actions.
- Improve “what can I do now?” visibility.

Phase gate:
- You can use the app without confusion about which player is spending Koku / Protection.

Steps:
- `P1-S1` Focus model in UI (`ACTIVE` vs `FOCUSED` player board)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P1-S2` Click on compact player boards changes detail focus (does not change turn)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P1-S3` Per-player quick actions shown near active player personal board (Koku->Protection, [+P])
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P1-S4` Remove/reduce duplicated personal actions from global controls (keep global controls truly global)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P1-S5` Add “Available Actions Now” recap for current situation (phase-1 rules only)
  - Parallel: `Yes` (with `P1-S4`)
  - Status: `DONE (USER OK)`
- `P1-S6` UX labels/tooltips polish after feedback pass
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P1-S7` Debug toggle to reveal/hide hidden hands of non-active players (tool-only visibility)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P1-S8` Compact player boards vertical size trim (reduce unused vertical space)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`

## Phase 2 - Turn Flow & Recaps (Playable Manual Simulation Loop)

Goal:
- Make turn structure explicit and testable step-by-step with clear recap before/after actions and end-of-round summaries.

Phase gate:
- A full round (all players) can be played manually with readable recaps and logs.

Steps:
- `P2-S1` Turn state panel (start refill / main options / end turn state)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P2-S2` “What can be done now” rules recap with legal/blocked reasons
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P2-S3` End-turn handoff button + optional auto sub-operations toggles (refill/income/log)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P2-S4` End-of-round recap panel (events, Koku changes, board changes, controls)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P2-S5` Log alignment pass with `AI/SIMULATION.md` turn sequence conventions
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P2-S6` Undo checkpoints (baseline)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
  - Notes:
    - Start simple: undo to `start of active turn` and/or `start of round` checkpoints.
    - Prefer snapshot-based restore first (less fragile than full command-undo at this stage).
- `P2-S7` Turn workspace consolidation pass (reduce panel clutter)
  - Parallel: `Yes` (with `P2-S5` UI-side part, if needed)
  - Status: `DONE (USER OK)`
  - Notes:
    - Unify phase-centric info/actions (`TURN STATE`, `AVAILABLE ACTIONS NOW`, phase transition button) into a single turn workspace.
    - Keep tool/debug controls separate or clearly isolated.
    - Consider embedding/collapsing `ROUND RECAP` and/or `ACTION LOG` sections to reduce window count.

## Phase 3 - Setup & Scenario Configuration Panel

Goal:
- Support multiple test setups without code edits.

Phase gate:
- You can configure a test match (players, variants, setup presets) from UI and reset into that state.

Steps:
- `P3-S1` Match setup panel (players 2/3/4, clans, turn order, open/fog mode)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P3-S2` Variant setup panel (line income +2, other toggles)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)` (first pass: `Line +2` moved into scenario config tab)
- `P3-S3` Sandbox presets (economy test / imperial test / error/reveal test / capital race)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P3-S4` Save/load scenario config (JSON)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P3-S4-core` Define configuration schema/versioning for scenario save/load (to avoid breaking old scenario files later)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P3-S4a` Persist sandbox setup values (e.g. starting Koku) in Configuration Management
  - Parallel: `Yes`
  - Status: `DONE (USER OK)` (covered by current JSON save/load implementation)
- `P3-S4b` Persist tool/debug view preferences when useful (e.g. hidden-hand reveal toggle)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
  - Notes:
    - Scenario JSON now persists local view preferences:
      - `view.revealHiddenHandsOnPlayerBoards`
      - `view.cardGraphicMode`
- `P3-S5` Behavior profile setup panel per player (aggressive, balanced, defensive, etc.)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`

## Phase 4 - Core Rules Expansion (Board Actions Phase 1.5 -> 2.0)

Goal:
- Move from sandbox-only interactions to a more faithful v24 board action engine.

Phase gate:
- Core manual play supports main board actions needed for realistic playtests (beyond empty-cell numbered placement).

Steps:
- `P4-S1` Stacking base rules (legal stack targets + top card update)
  - Parallel: `No`
  - Status: `DONE (USER OK)`
- `P4-S2` Building progression (`[+MK]`, `[+CS]`, `[+CAP]`) with Protection/Koku constraints
  - Parallel: `No`
  - Status: `DONE (USER OK)`
  - Current baseline assumptions (to confirm):
    - `Market`: same build-resource logic as `Castle` (chain-based Protection consumption; simulator currently auto-selects sources)
    - `Castle`: transform using `3 total Protection` on the connected chain (tokens may come from the same card, e.g. Daimyo), place castle on selected connected Numbered card (temporary auto-source selection in simulator)
    - `Capital`: transform using `3 Castles` on `3` different connected cards, place capital on selected connected Numbered Castle (temporary auto-source selection in simulator)
    - No buildings in Imperial Zones (confirmed)
    - No buildings on Daimyo (confirmed)
  - UI note:
    - Build markers/badges (`+CS/+CAP/+MK`) are shown on `GAME BOARD` only for now (good enough for current testing; can be extended later to playerboard views).
    - Castle **mandatory trigger** is treated separately from Castle **availability** (mandatory depends on protected connected Numbered-card condition, not just total chain Protection).
    - Hidden phase-advance button while mandatory Castle/Capital is pending is approved UX.
- `P4-S3` Legality validation helpers reused by UI recap (no duplicated rule checks)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
- `P4-S4` Action command log events for builds/stacking
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
  - Notes:
    - Richer action log telemetry for Phase 4 interactions:
      - stack depth deltas on play/stack
      - Protection placement count/supply/pending-converted deltas
      - build source lists aggregated (e.g. repeated source cells shown as `A1x2`)
      - build pool/flag deltas (`Market`, `Castles`, `Capital`)
- `P4-S5` Regression tests for board legality cases (manual or scripted)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)` (first scripted smoke pass)
  - Notes:
    - First scripted/non-destructive smoke check added (`Run P4 Smoke` in Simulation Controls).
    - Current scope: state invariants + known build restrictions (Imperial/Daimyo) + target/phase summary.
- `P4-S6` Per-card action UI (mini action panel / action modes)
  - Parallel: `Yes`
  - Status: `DONE (USER OK)`
  - Notes:
    - Evolve hand cards from "click-to-play" into small action controls.
    - Expected actions over time: play face-up, play face-down, stack, sacrifice, etc. (depending on rule phase implementation).
    - Move `Play face-down` from global toggle to per-card controls (user feedback).
    - Consider drag-and-drop card play to board cells (user feedback; optional UX enhancement).
    - Current first pass: hand cards have mini `Play` / `Down` buttons under each Numbered card; card click defaults to face-up play. Recap now shows `Face-up` and `Down` legality separately.
    - Keyboard shortcuts refined (user feedback): `P` Protection, `M` Market, `C` Castle, `W` Capital, `1..9` Numbered (face-up), `Shift+1..9` Numbered Down, `F` toggles one-shot keyboard face-down mode for the next number shortcut, `K`/`+` converts `2 Koku -> 1 Protection`, `Enter` next phase, `Backspace` phase-step undo.
    - Keyboard shortcuts now prefer the hovered GAME BOARD cell as target when the mouse is over the board (fallback to selected cell).
    - Shortcut collision note: `C` is currently reserved for `Castle`; `Chajin` shortcut key needs a final mapping when retainer shortcut behavior is finalized.
    - Added shortcut legend + explicit hovered/selected/effective target indicators in `Simulation Controls`, plus pending keyboard `Down` mode indicator.
    - Drag-and-drop baseline added: drag a Numbered card from the active hand (MAIN phase) and drop on a GAME BOARD cell to play it, reusing the same legality/status path as button/click actions. `Shift` (or keyboard `F` one-shot mode) applies `Down` during drag.
    - UX split refined after testing: hand buttons/click and quick actions use the selected cell; keyboard shortcuts may use the hovered cell; hover no longer changes selection while moving toward the hand panel.
    - Drag UX polish: source card is highlighted while dragging; drag preview shows a semi-transparent duplicated card under cursor.
    - Drag preview now includes target coordinate info; invalid target preview is tinted reddish with blocker reason text.
    - Retainer baseline is now playable in placeholder mode:
      - `Action1` via click/shortcut uses a simplified placement/chained/overlap legality mapping per retainer code.
      - `Action2` is treated as sacrifice placeholder (card consumed to discard with log), with full effects still pending.

## Phase 5 - Hidden Info, Reveal, Errors, Rebellions, Emperor Interactions

Goal:
- Cover the major v24 edge systems that matter for balance and playtesting quality.

Phase gate:
- Hidden info / reveal / error flows are testable and clearly logged.

Steps:
- `P5-S1` Face-down/reveal flow and paid reveal actions
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - MAIN-only activation: includes MAIN-panel button and `Shift + Right Click` on a face-down board card target.
    - Own face-down reveal is queued and resolved at the player's next START phase (deferred timing behavior).
    - Opponent face-down reveal resolves immediately when hidden identity is tracked.
- `P5-S2` Error declaration flow + correction UI and logs
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - MAIN-only activation: includes MAIN-panel button and `Shift + Right Click` on a face-up Numbered board card target.
    - Current baseline correction: valid duplicate Numbered target flips face-down and grants `+1` Protection pending placement.
- `P5-S3` Rebellion handling (if/where applicable in v24 scope)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK` (placeholder queue hook)
  - Notes:
    - Added pre-START pending hand-effect queue infrastructure.
    - First placeholder hooks wired via Retainer sacrifice actions:
      - `Shinobi A2`: queue next-player `-1 hand` before START refill, and self `+1 hand` before own START refill.
      - `Samurai A2`: queue next-player `-1 hand` before START refill.
    - Effects are logged and resolved before START refill; full rebellion rule logic still pending.
- `P5-S4` Emperor visit/use flow integration in turn options
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
- `P5-S5` Recap integration for hidden-info events (designer/debug mode vs normal)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - In `Controlled` mode, reveal-sensitive details in `Round Recap` and `Action Log` are masked.
    - In `Open Info` or `Debug Reveal`, full details remain visible.

## Phase 6 - AI Behavior Engine (Local Computer Players)

Goal:
- Let computer-controlled players act with different styles for playtesting and balance evaluation.

Phase gate:
- AI turns can run in at least 3 distinct styles with readable decision explanations.

Steps:
- `P6-S1` Behavior model framework (policy interface + parameters)
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Per-seat control/style config (`Human` / `AI`) is wired in scenario config and JSON persistence.
    - Baseline scoring policy hook (`ScorePossibleMoveForBehavior`) is active.
- `P6-S2` Baseline policies: `Aggressive`, `Balanced`, `Defensive`, `Semi-Random`, `Conservative`
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Distinct style scoring deltas are active in AI move selection.
    - Priority-weight model added for move selection:
      - `PRI-1=11`, `PRI-2=7`, `PRI-3=4`, random floor `R=1`
      - final move score is additive (`11+11+4+1` style formula).
    - Multiple conditions on the same move stack additively (e.g. card action + protection/build urgency).
    - Connected-chain priority rule added:
      - card plays on connected targets score higher than non-connected,
      - connected chain extension/repair gets extra weight,
      - completing zone/line is high priority only when target is connected (otherwise low-priority completion bonus).
    - `Visit Emperor` dynamic timing curve added (turn-window based with deck/discard constraints):
      - early turns de-prioritized,
      - mid-turn window peaks,
      - late turns decay to near-zero/zero.
- `P6-S3` Mistake profile controls (intentional/unintentional error tendency)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK` (config/persistence layer)
  - Notes:
    - Non-linear stepped values are in config UI + JSON.
    - Runtime integration baseline:
      - `mistakeChancePct` now drives AI top-depth exploration pool size (tiered by score bands).
      - higher mistake% => deeper candidate pool before random pick.
      - selection model uses score tiers (not flat random):
        - include full score bands up to top-depth `X`,
        - random pick inside resulting candidate pool.
- `P6-S4` Decision explanation log (“why this move”)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - AI logs top scored candidates and chosen move each step.
    - Explanation now includes PRI formula and hit counts (`P1x/P2x/P3x/Rx`).
    - AI move list in `ANALYSIS > AI Analysis` shows per-move PRI score beside each legal move with tooltip reason breakdown.
- `P6-S5` Human/AI mixed table support (same-screen)
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Per-seat `Human/AI` badges are visible in player/active board panels.
    - Mixed tables run in the same local simulation flow.

## Phase 7 - Simulation Automation & Analysis Tools

Goal:
- Make the simulator a practical balance lab, not only a manual testing UI.

Phase gate:
- You can run semi-automated/full simulations and inspect recaps per turn/round/game.

Steps:
- `P7-S1` Autoplay controls (single step / per-turn / per-round / full game)
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Implemented: `AI Step (1 move)`, `AI Auto Turn`, `AI Auto Round`, `AI Auto Game`, `AI N Moves`, step cap.
    - Full-game autopilot now stops on endgame trigger completion (`state.gameOver`) or safety cap.
- `P7-S2` Automatic recap snapshots (turn + round summaries)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK` (partial)
  - Notes:
    - AI analysis timeline snapshots are auto-captured by turn/phase.
    - Dedicated turn+round report export formatting still pending.
- `P7-S3` Metrics panel (Koku curves, control counts, build timing, win conditions path)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Added `ANALYSIS > Metrics` tab with one-chart multi-player timeline.
    - Current selectable series: `Legal Moves`, `Koku`, `Protection`, `Income Preview`, `OnBoard`, `Castles`.
    - Added latest-snapshot table per player.
- `P7-S4` Export log/report for external analysis (markdown/json/csv)
  - Parallel: `Yes`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Added `ANALYSIS > Export` tab.
    - Exports:
      - markdown simulation report (`.md`)
      - action log CSV (`_action_log.csv`)
      - runtime snapshot JSON (`_snapshot.json`)
- `P7-S5` Batch runs with seed control (single machine, non-network)
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Scenario random seed is configurable/persisted and used in setup shuffle + AI tie-break randomness.
    - Added `ANALYSIS > Export > AI Seed Sweep Batch`:
      - seed range (`start`, `end`), per-match step cap, optional `Force all seats to AI`
      - one full AI match per seed (inclusive range)
      - exports:
        - `*_seed_sweep_<start>_<end>_summary.md`
        - `*_seed_sweep_<start>_<end>_matches.csv`
        - `*_seed_sweep_<start>_<end>_summary.json`
      - summary includes winner counters by seat/clan, seat-1 win rate, avg rank/score/koku, rank drift.

## Phase 8 - Validation, Rulebook Feedback Loop, and Polish

Goal:
- Tighten confidence in the simulator and feed ambiguities back into rulebook updates.

Phase gate:
- Simulator is reliable enough to be used regularly for v24 balance and rules clarity testing.

Steps:
- `P8-S1` Add formal validation checks (state invariants, turn invariants)
  - Parallel: `No`
  - Status: `IMPLEMENTED - WAITING FEEDBACK`
  - Notes:
    - Added `Run Formal Validation` button in `Simulation Controls`.
    - Validation results are appended to `Action Log` with `Validate` tag.
- `P8-S2` Build test scenarios from `AI/SIMULATION.md` clarifications (`C-001`, `C-002`, ...)
  - Parallel: `Yes`
  - Status: `TODO`
- `P8-S3` UI polish pass (layout presets, compact/ultra-compact, readability)
  - Parallel: `Yes`
  - Status: `TODO`
- `P8-S3a` Optional visual asset integration (clan crests / logos / card art placeholders)
  - Parallel: `Yes`
  - Status: `TODO`
  - Notes:
    - Support loading images from a local assets subfolder.
    - Should degrade gracefully if assets are missing (fallback to colored cards + text).
- `P8-S4` Rulebook wording feedback export (ambiguities found in testing)
  - Parallel: `Yes`
  - Status: `TODO`
- `P8-S5` “Release candidate” checklist for local v24 simulator tool
  - Parallel: `No`
  - Status: `TODO`

## Current Focus (This Iteration)

- Active phase: `Phase 5/6/7 overlap (incremental implementation)`
- Immediate target:
  - increase Retainer action coverage beyond placeholder baseline (phase-5/phase-4 bridge)
  - harden AI-assisted simulation loop for longer autonomous runs
  - keep scenario config + analysis tabs aligned with current runtime behavior
  - contextualize Retainer AI scoring (`A121..A162` practical subset) via TOML keys + `[Axxx]` trace tags

## Backlog (Future / Not Scheduled Yet)

- `B-005` Per-player selected-cell memory (restore last used target at turn start)
  - Goal:
    - When a player's turn starts, restore that player's last selected board cell instead of defaulting to a generic starting cell.
  - Notes:
    - Selection should remain personal to each player for smoother same-screen testing.
  - Status: `DONE (USER OK)`
  - Notes:
    - Active player's last board target is remembered and restored at turn start.
    - Sandbox auto-Junbi initializes each player's default target to their Daimyo start cell.
    - Target memory is updated on explicit selection/actions (not on hover alone).

- `B-006` Phase reverse step button (Start/Main/End back one phase)
  - Goal:
    - Allow small-step reverse navigation within the current turn phases (e.g. `END -> MAIN -> START`) using a non-primary button near the phase-advance button.
  - Notes:
    - Prefer lightweight/safe implementation first (phase-boundary snapshots) before full command undo.
  - Status: `PARTIALLY IMPLEMENTED (keyboard Backspace)` 

- `B-001` Save/load in-progress match state (full snapshot)
  - Goal:
    - Save a running game and resume later for continued testing.
  - Notes:
    - Different from scenario configuration save/load.
    - Requires serializing board state, hands/decks/discards, hidden info, turn state, logs, variants, and AI behavior state.
    - Should include versioning and compatibility strategy.
  - Status: `TODO`

- `B-002` Match snapshot export/import (read-only analysis snapshots)
  - Goal:
    - Capture a specific turn state for discussion/balance review without necessarily resuming gameplay.
  - Status: `TODO`

- `B-003` Asset pipeline conventions for UI images (names/paths/loading/cache)
  - Goal:
    - Standardize how local assets (clan crests, board images, card images) are organized and loaded.
  - Notes:
    - Useful before large-scale visual asset integration.
    - Current shared asset root (agreed): `E:\Projects\Sengoku-Imgui\sengoku\resources\`
    - Example: `resources/clans/TI_crest.png`, `resources/cards/...`
    - UI loaders should support graceful fallback if an asset is missing.
  - Status: `TODO`

- `B-004` Panel consolidation / layout simplification pass
  - Goal:
    - Reduce panel count and group related information once Phase 2/3 features stabilize.
  - Notes:
    - Candidate merges: `SIMULATION CONTROLS` + `TURN STATE`, or a tabbed/sectioned side panel.
    - Preserve clarity of game actions vs tool/debug actions while reducing window clutter.
  - Status: `TODO`
