# Sengoku v24 - Retainer Actions Matrix

Purpose:
- Single implementation-ready reference for Retainer action text and behavior mapping.
- Source of truth for simulator logic/UI wiring.

Primary source:
- `AI/RulesV24.md` (general rules + appendix).

## 1) Global Retainer Rules (v24)
1. Each Retainer has exactly 2 Order Actions (`A1` / `A2`).
2. When used, choose and resolve exactly 1 action.
3. Retainer Order Actions are separate from Turn Procedures (`Reveal`, `Convert Koku`, `Build`, `Error Fix`).
4. `[PLACE_CHAINED]` means orthogonally connected to own Chain of Command.
5. Some Retainers may be used as traps (`[TRAP]`) depending on card text/timing.

## 2) Action Categories (normalized for code)
- `PLACE_ANYWHERE` -> `[PLACE]`
- `PLACE_CHAINED` -> `[PLACE_CHAINED]`
- `SACRIFICE` -> `[SACRIFICE]`
- `OVERLAP` -> `[OVERLAP]`
- `TRAP_MODE` -> `[TRAP]` (timing/trigger subflow)

## 3) Retainer Matrix (current base set)

| Card | Deck Code | A1 Tags | A1 Summary | A2 Tags | A2 Summary | Notes |
|---|---|---|---|---|---|---|
| Samurai | `Sam` | `PLACE_CHAINED`, `OVERLAP` | Place near own chain or cover own clan card; then remove 1 adjacent unprotected card OR remove 1 token | `SACRIFICE` | Reactive interrupt during opponent turn: block one Special card action | Opponent may continue using another legal card |
| Ashigaru | `Ash` | `PLACE_CHAINED` | Place near own chain; remove up to 2 adjacent unprotected Numbered or face-down cards | `SACRIFICE` | Draw 4, keep 1, put remaining 3 on top/bottom of deck | Deck-order manipulation action |
| Chajin (Tea Master) | `Cha` | `SACRIFICE` | Draw 2 new cards (max 1 use of this action per turn) | `SACRIFICE` | Draw and immediately play 1 card; if Special, effect boost (+2 up to cap) | Per-turn limiter required on A1 |
| Sōhei | `Soe` | `PLACE_ANYWHERE`, `OVERLAP` | Overlap on legal target: Sohei OR unprotected Numbered OR face-down (any clan) | `SACRIFICE` | Retrieve top discard card to hand | Overlap-focused placement retainer |
| Shinobi | `Shi` | `SACRIFICE` | Remove from map: 1 Special (+any token on it) OR 1 face-down card | `SACRIFICE`, `TRAP_MODE` | Spy hand, force 2 discards, then delayed end-turn extra draw | Trap-capable flow |
| Rōnin | `Ron` | `PLACE_ANYWHERE` | Replace 1 unprotected non-Ronin card; returned/remainder stack resolution as printed | `SACRIFICE`, `TRAP_MODE` | Steal up to 2 tokens from opponent in-play cards; if fewer are available, gain direct compensation so total gain target remains 2 | Trap-capable flow; compensation respects token-cap |

## 3b) Target Interaction Matrix (Numbered / FaceDown / Retainer / Protected / Any)

Interpretation rule:
- `any card` means any valid top card for that specific action text; it is not a global override.
- Unless action text says otherwise, `Daimyo` is never a removable/replaceable card target.

| Action | Numbered (face-up) | FaceDown | Retainer | Daimyo | Protected target |
|---|---|---|---|---|---|
| `Sam A1` remove card | Yes (adjacent, unprotected) | Yes (adjacent, unprotected) | Yes (adjacent, unprotected) | No | No (for card removal) |
| `Sam A1` remove token | Yes (if token exists) | Yes (if token exists) | Yes (if token exists) | Yes (adjacent Daimyo token allowed) | Yes (token removal path) |
| `Ash A1` remove card | Yes (adjacent, unprotected) | Yes (adjacent, unprotected) | No | No | No |
| `Soe A1` overlap | Yes (if unprotected) | Yes (if unprotected) | Only `Soe` top (if unprotected) | No | No |
| `Shi A1` remove card | **No** | Yes | Yes | No | Yes (tokens/building on removed target are removed with it) |
| `Ron A1` replace | Yes (if unprotected) | Yes (if unprotected) | Yes (if unprotected and non-`Ron`) | No | No |
| `Ron A2` steal token | N/A card-type agnostic; steals board tokens from opponent top cards (including Daimyo token if present) | N/A | N/A | N/A | Token required |

## 4) Simulator Deck/Code Alignment
- Implemented base deck codes in simulator: `Sam`, `Ash`, `Cha`, `Soe`, `Shi`, `Ron`, plus `Uni` placeholder.
- `Uni` is not defined in the current appendix action list and must stay placeholder until rule text is finalized.

## 5) Suggested Implementation Order
1. UI-only selection lock (A1/A2 exclusive) per Retainer card use context.
2. Placement validators by category:
   - `PLACE_CHAINED`
   - `PLACE_ANYWHERE`
   - `OVERLAP`
3. `SACRIFICE` flow skeleton (cost/discard/timing hooks), then per-card effects.
4. `TRAP_MODE` subflow for `Shi`/`Ron` (armed state, trigger, resolve, remove/discard).
5. Reactive window system for Samurai `A2`.

## 5b) Current Simulator Status (implementation snapshot)

- Implemented baseline:
  - `Sam A1` placement + deterministic adjacent removal (card-first priority on unprotected adjacent top cards, fallback token removal including Daimyo token).
  - `Ash A1` placement + deterministic removal up to 2 adjacent unprotected Numbered/FaceDown.
  - `Soe A1` overlap legality baseline.
  - `Shi A1` targeted sacrifice removal (Retainer/FaceDown).
  - `Ron A1` replacement baseline on unprotected non-Ronin top, with replaced top returned to owner hand when reconstructable.
  - `Cha A1` draw-2 with once-per-turn limiter.
  - `Ash A2` draw/look with pending keep-1 choice subflow (AI fallback deterministic keep index 0).
  - `Soe A2` retrieve top discard.
  - `Cha A2` draw-1 with immediate-play deterministic resolver.
  - `Ron A2` board-first steal with direct compensation to target total gain `2` (capacity-aware).
  - `Sam A2` queued one-block Retainer interrupt on next player.
  - `Shi A2` deterministic hand disruption (up to 2 forced discards) + delayed end-turn draw bonus.

- Partially implemented / placeholder:
  - `Sam A2` true live reactive timing window (current implementation uses queued interrupt policy).
  - `Shi A2` full wording-accurate spy/trap timing window.
  - `TRAP` armed/reveal timing windows.

- Not implemented yet:
  - Full deterministic stack restoration semantics where card text requires deeper stack manipulation beyond top-layer baseline.

## 6) Open/Clarification Items (before full logic)
1. Exact stack-resolution semantics for Ronin `A1` (“kill or return rest of stack”) need strict deterministic order.
2. Chajin `A2` Special boost cap must be represented with explicit numeric metadata in simulator state.
3. Trap trigger timing windows and reveal ownership for `Shi`/`Ron` should be locked before automation.
4. `Uni` (and expansion Retainers) need final card text before effect implementation.
