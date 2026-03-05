# Sengoku v24 - Turn Flow Recap

## 1. START phase
1. Open active player's turn.
2. Setup baseline reminder: each player starts with Daimyo Protection (`+P1` default, `+P2` only for specific experimental starts).
3. Koku on player board follows storage cap `max 5`.
4. Resolve any pending delayed hand effects that trigger at turn start (before refill).
5. Resolve start refill to hand size 3 (auto/manual based on simulator toggle).
6. Optional: `Visit Emperor` (start-of-turn option, before card play).
7. No board-play actions here.
8. Transition action: `Begin Main Phase`.

## 2. MAIN phase
1. Core board actions:
   - Play cards (face-up / face-down when legal).
   - Stack/overlap where legal.
   - Retainer action selection/use (`A1` or `A2`) in simulator placeholder mode.
   - `Chajin A1` draw-2 is limited to once per turn in current simulator baseline.
   - Pay last-card Koku cost when required by hand-floor rule.
2. Resource actions:
   - `Convert Koku -> Protection` (2 Koku => 1 Protection).
   - Converted protection must be placed before leaving `MAIN`.
   - Any Protection gained during turn procedures (conversion, error-fix rewards, effects) is placed immediately when gained.
   - Protection token pool per player is capped at 6 total tokens.
3. Build actions:
   - Place `Protection`.
   - Build `Market`, `Castle`, `Capital` on legal targets.
4. Placement/build limits:
   - No build in Imperial Zones.
   - No build on Daimyo card.
   - Build targets must follow connected-chain and card-type legality.
5. Secondary actions:
   - `Reveal` face-down cards (where legal).
   - `Declare / Fix Error` (where legal).
   - Reveal baseline: own face-down reveal is deferred to next `START`; opponent reveal resolves immediately when identity is tracked.
   - Error baseline: valid duplicate `Numbered` target flips face-down and grants `+1 Protection` (pending placement).
   - `Make / Break Alliances`.
6. Phase-exit gates (`MAIN -> END` blocked if any fails):
   - Hand must be reduced to legal floor (`2`, or `1` only with paid last-card rule).
   - Hand floor/last-card payment rules must be respected.
   - No pending converted protection placements.
   - No mandatory build still pending.
7. Transition action: `Begin End Phase`.

## 3. END phase
1. Resolve END steps:
   - End refill to hand size 3 (mandatory).
   - Collect Koku income (base + active bonuses).
   - Imperial income counts only for Imperial cards connected to your Chain of Command.
   - Apply Koku storage cap (`max 5`), discard excess.
2. Apply any end-window card effects, if present in the rules/effects implementation.
   - These effects may increase hand size above 3 after the mandatory refill.
3. Pass hand to next player.
4. Next player starts at `START`.
5. Simulator runtime option:
   - `autoPassHandOnEndResolve = ON` => END resolve immediately performs handoff.
   - `OFF` => END remains review state until explicit `Pass Hand`.

## 4. Round progression
1. A round ends after all players complete one turn and pass hand.
2. New round starts with next active player in `START`.

## 5. Endgame trigger (Capital)
1. When a player builds their `Capital`, that player arms the final cycle.
2. Play continues in normal turn order for the rest of the table.
3. The game ends when turn order returns to the same player who armed the final cycle.
4. At that point, no new turn starts for that player; proceed to final scoring.
5. Endgame reveal window rule:
   - only players in `Shogun` status may still spend gained `Koku` to reveal cards during the endgame resolution window.
   - there may be multiple `Shogun` players; each of them can use this reveal spending window.
   - non-Shogun players cannot spend Koku for reveal once endgame has been triggered.

## 6. Final scoring recap (current clarified formula)
1. `+1` point for each face-up card in play (including Daimyo).
2. `+1` point for each completed zone.
3. `+1` point for each completed line.
4. `+1` point for each controlled Imperial zone.
5. `+1` point for each Castle in play.
6. `+2` points for each Capital in play.
7. `+4` points if player is `Shogun`.

## Open decisions to lock
1. Final mandatory Castle trigger wording:
   - Must be tied to protected connected Numbered-card condition,
   - Not generic total protection on chain.
