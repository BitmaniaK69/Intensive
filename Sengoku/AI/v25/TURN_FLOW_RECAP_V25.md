# Sengoku v25 - Turn Flow Recap

## 1. Beginning of Turn
1. Open the active player's turn.
2. Setup reminder: each player starts with Daimyo Protection (`+P1` default, `+P2` only in declared variants).
3. Koku on the player board follows storage cap `max 5`.
4. Resolve any delayed hand effects that explicitly trigger at turn start, before refill.
5. Refill hand up to `3`.
6. Optional: `Visit the Emperor` (Expert Mode only; after refill and before the first played card).
7. There is no start-of-turn Shogun declaration in V25. `Imperial Summons` is triggered immediately when a valid connected `Capital` is formed.

## 2. Active Turn
1. Core card actions:
   - Play cards face-up or face-down where legal.
   - Stack/overlap where legal.
   - Use one Retainer Order Action (`A1` or `A2`) when a Retainer is used.
   - `Chajin A1` draw-2 remains limited to once per turn.
   - Pay the last-card Koku cost when the hand-floor rule requires it.
2. Resource actions:
   - `Convert Koku -> Protection` (`2 Koku -> 1 Protection`).
   - Converted Protection must be placed before leaving the Active Turn.
   - Any Protection gained during turn procedures or effects is placed immediately when gained; if no legal face-up map placement exists, it is discarded to supply.
   - Protection token pool per player is capped at `6`.
3. Build actions:
   - Place `Protection`.
   - Build `Market`, `Castle`, `Capital` on legal targets.
   - `Market = 2 Protection`, `Castle = 3 Protection`.
   - Mandatory Castle conversion applies only to Protection on connected Numbered cards in your Chain.
4. Legality reminders:
   - No build in Imperial Zones.
   - No build on the Daimyo card.
   - Remove/replace-style effects cannot target a protected top card unless a rule/card explicitly says otherwise.
5. Secondary actions:
   - `Reveal` face-down cards.
   - `Declare / Fix Error`.
   - `Make / Break Alliances` (Expert Mode).
   - Reveal resolves immediately: flip the chosen face-down card face-up and apply its identity at once.
   - Immediate illegal placements are corrected immediately by the acting player: place that card face-down in a legal face-down space, or discard it if no legal correction exists. No reward is gained.
   - Existing board Errors may be fixed on your own turn for `+1 Protection` per resolved Error.
6. Phase-exit gates:
   - Hand must be reduced to the legal floor (`2`, or `1` only with the paid last-card rule).
   - No pending converted Protection placements.
   - No mandatory build still pending.

## 3. Collect Resources
1. Collect Koku income (base + active bonuses).
2. Imperial income counts only for Imperial cards connected to your Chain / Chain of Command.
3. Apply Koku storage cap (`max 5`), discard excess.

## 4. End of Turn
1. Apply any end-window card effects that explicitly trigger here.
2. Refill hand to size `3` (mandatory).
3. Pass turn to the next player.

## 5. Endgame trigger (Capital)
1. Endgame begins immediately when a player legally forms a valid connected `Capital`.
2. That player immediately becomes the first `Shogun` for scoring and still finishes the current turn normally and in full.
3. After that turn, every player takes one final restricted turn in normal order, starting with the next player after the first Shogun and ending with the first Shogun.
4. During a restricted final turn, players cannot play or place cards.
5. During a restricted final turn, players may only spend `Koku` to `Reveal` face-down cards, or convert `Koku` into `Protection` and use those tokens for legal build progression, including `Castle` and `Capital` if requirements are met.
6. The normal Active Turn hand-size gate is suspended during restricted final turns.
7. Restricted final turns do not perform a normal End of Turn refill.
8. Building a `Capital` during a restricted final turn does not create a new Shogun turn and does not restart `Imperial Summons`.
9. If another player legally forms a connected `Capital` during the same `Imperial Summons`, that player also counts as `Shogun` for scoring by order of achievement.
10. All active alliances break immediately when `Imperial Summons` begins.
11. After all restricted final turns are completed, proceed to final scoring.

## 6. Final scoring recap
1. `+1` point for each face-up `Numbered` or `Retainer` card on board.
2. `+1` point for each full zone or line under control.
3. `+1` point for each `Castle`.
4. `+3` points for each `Capital`.
5. `Shogun` scoring is ordered by `Imperial Summons` achievement: first `+4`, second `+3`, third `+2`, all later players `+1`.
6. `+1` point in Expert Mode if the player never used the Emperor reshuffle right; automatic exhaustion loss counts as used.
7. Only connected cards/structures score; face-down cards do not score the direct `+1` card value but still count for control.

