# Koku Balance Ideas Backlog (V24.x)

Working file for Koku-economy balancing ideas and playtest variants.

## How to Use This File
- Use `- [ ]` for ideas not tested yet.
- Use `- [x]` for tested ideas.
- Use `~~text~~` for discarded ideas.
- Add a triage tag before the idea when reviewing it:
  - `[YES]` = strong candidate, likely worth testing
  - `[MAYBE]` = interesting but uncertain / needs combo or more thought
  - `[NO]` = not suitable for current V24.x direction
  - `[TEST NEXT]` = selected for the next playtest
- Add short notes at the end of a line, for example: `-> too fast`, `-> good`, `-> retest`.
- Keep "Packages" at the bottom updated with the combinations actually tested.

Example:
- `- [ ] [MAYBE] Market bonus outside counting cap -> maybe too strong with +2 Market`

## Triage Board (YES / MAYBE / NO -> Test Decision)
Use this section to shortlist ideas before touching the rules.

### YES (Strong candidates)
- [ ] Proactive Visit the Emperor: choose either reshuffle (current effect) OR gain `+2 Koku` and lose the Visit right. (Emperor Visit)
- [ ] Proactive Visit the Emperor gives `+1 Koku` in addition to reshuffle. (Emperor Visit)
- [ ] Error correction reward = `1 Protection token` (not `+1 Koku`). (Errors/Rebellions)
- [ ] Daimyo reserve full (`3` Protection tokens on Daimyo) grants `+1 Koku` at end of turn. (Daimyo reserve)
- [ ] With 1 Castle -> No pay the koku for last card. (Castle / hand-flow)
- [ ] Domain size bonus: if your connected Chain of Command has at least `X` cards, gain `+1 Koku` (test `X = 7/8/9`). (Board presence)

### MAYBE (Needs combination / numbers / risk check)
- [ ] Build rebate: when creating a Castle, immediately park `+1 Koku`. (Build rebate)
- [ ] Market construction costs `2 Protection token` (instead of 3 like castles). (Mixed Koku+Token / build pacing)
- [ ] `Market = +2 Koku` (instead of +1). (Income)
- [ ] Increase storage cap from `6` to `7`. (Global)
- [ ] Market increases storage cap in Player board (`+1 storage for Koku`). (Income)
- [ ] Occupy a "Rice Zone" on the Game Board with a Market or Castle grant `+1 Koku`. (Map zones)
- [ ] Attack pressure reward: removing any opponent token/building grants `+1 Koku` [watch aggression spikes]. (Attacks / aggression economy)
- [ ] Error correction before the turn is over `+1 Koku` (other than correction after end of turn). (Errors timing)
- [ ] `+1 Koku` at setup for all players (flat). (Global, symmetry risk)
- [ ] Line emphasis: Lines give `+2 Koku` while Zones remain `+1` (push expansion over turtling). (Map control income)
- [ ] Create a Zone or a Line gives `+1 Protection Token` immediately. (Map control income)
- [ ] Controlling all 4 Imperial Zones grants `+1 Koku` extra. (Imperial Zones)

### NO (Discard for now)
- [ ] Idea:
- [ ] Idea:

### TEST NEXT (Final pick for next match)
- [ ] Package / idea:
- [ ] Package / idea:

### Decision Notes (why we picked these)
- Meta goal for this test:
- What we are trying to improve:
- What we must avoid (too fast / turtle / symmetry / etc.):

## POLL (Short List for Voting)
Multiple choice allowed. More than one option may be combined in the same test.

- [ ] Emperor Visit (proactive): choose `reshuffle` OR `+2 Koku` (lose Visit right)
- [ ] Emperor Visit (proactive): reshuffle + `+1 Koku`
- [ ] Keep error fix reward as `1 Protection token` (not `+1 Koku`)
- [ ] Full Daimyo reserve (`3` tokens) = `+1 Koku` at end of turn
- [ ] If you have `1 Castle`, the paid last card costs `0 Koku`
- [ ] Domain size bonus: `+1 Koku` if connected chain reaches `X` cards (`7/8/9`)
- [ ] Build rebate: when building a Castle, immediately get `+1 Koku`
- [ ] All 4 Imperial Zones controlled = `+1 Koku`
- [ ] Market costs `2 Protection tokens` (instead of `3`)
- [ ] Market income gives `+2 Koku` (instead of `+1`)
- [ ] Increase Koku storage cap: `6 -> 7`
- [ ] Market increases Koku storage cap by `+1`
- [ ] Rice Zone rule: Market or Castle on a Rice Zone grants `+1 Koku`
- [ ] Attack reward: remove an opponent token/building = `+1 Koku`
- [ ] Error fixed before end of turn = `+1 Koku` (special timing bonus)
- [ ] Setup bonus: all players start with `+1 Koku`
- [ ] Line bonus: Lines = `+2 Koku` (Zones stay `+1`)
- [ ] Create a Zone or Line: gain `+1 Protection token` immediately

## Current Baseline (Context)
- V24.x goal: increase average Koku availability (roughly +1 Koku per turn on average) and improve Protection-token flow without returning to V22 "turtle / everyone progresses together" behavior.
- Avoid flat `+2 Koku` default at setup.
- Avoid repeated rules with trigger style "the first time that..." (low preference).
- Current/known adopted changes around V24.1 (for context):
  - Paid last card: play to 2 in hand, then pay 1 Koku to play the last card.
  - No face-down cards in Imperial Zones.
  - Face-down cards allowed on top of Special/Retainer cards.
  - Koku storage cap reduced to 6.
  - Capital final scoring increased to +3.
  - Error correction reward changed from `1 Koku` to `1 Protection token` per corrected Error.

## Problem Framing (What We Want)
- More Koku liquidity without making constructions explode too early.
- More Protection-token availability / circulation without covering the map too fast.
- Preserve interaction (reveals, attacks, pressure on Capital candidates).
- Avoid symmetric openings where everyone makes the same moves and reaches milestones together.
- Keep Market / Castle / map control strategically meaningful.

## Ideas: Income / Economy Rules (Direct Koku)
- [MAYBE] `Market = +2 Koku` (instead of +1).
- [NO] Market bonus does not count toward the end-of-turn counting cap.
- [NO] Base income (`+1`) does not count toward the end-of-turn counting cap.
- [NO] Market increases end-of-turn counting cap (`5 -> 6`) while connected/controlled.
- [MAYBE] Market increases storage cap (`6 -> 7`) while connected/controlled.
- [NO] Castle increases end-of-turn counting cap by `+1` (only if connected).
- [NO] Castle increases storage cap by `+1` (limit total Castle bonus to +1 or +2).
- [NO] Market + Castle synergy: Market gives `+2` only if the player also has at least 1 connected Castle.
- [NO] Income floor: minimum `2 Koku` gained at end of turn (if total counting would be lower).

## Ideas: Koku-Equivalent (Reduce Koku Pressure Instead of Adding Koku)
- [NO] Reveal (Bribery) costs `2 Koku` instead of `3`.
- [NO] With Market, Reveal costs `2 Koku` (otherwise remains `3`).
- [NO] With Market, the paid last card (play from 2 cards to 1) costs `0 Koku` instead of `1`.
- [NO] With Market, Koku conversion improves from `2 Koku -> 1 Protection` to `3 Koku -> 2 Protection`.
- [NO] Allow a Daimyo reserve Protection token to pay `1 Koku` worth of cost for Reveal / paid last card (spend token instead of Koku).
- [NO] Allow Reveal / paid last card to be paid with either `Koku` or `1 Daimyo reserve Protection token`.

## Ideas: Castles / Protection / Daimyo Reserve (New Economic Roles)
- [MAYBE] Daimyo reserve full (`3` Protection tokens on Daimyo) grants `+1 Koku` at end of turn.
- [NO] Daimyo reserve with at least `2` tokens grants `+1 storage cap` (logistics effect).
- [NO] Daimyo reserve tokens can be converted back into Koku at a poor rate (for example `2 reserve tokens -> 1 Koku`) [HIGH RISK].
- [NO] Castle provides `+1 Koku` only if it is connected and on a face-up Numbered card (anti-hidden stacking abuse).
- [NO] Castle provides `+1 Koku` only if the Castle space is in a non-Imperial Zone (pushes expansion).
- [MAYBE] Protection density bonus: if you have `X` connected Protection tokens on map cards, gain `+1 Koku` (test threshold).
- [NO] Daimyo reserve as emergency economy: during your turn you may move 1 reserve token back to supply to reduce one Koku cost by `1` (not for building conversion).
- [MAYBE] With 1 castle -> No pay the koku for last card.

## Ideas: Emperor Visit (Preventive Visit) as Koku Valve
- [YES] Proactive Visit the Emperor: choose either reshuffle (current effect) OR gain `+2 Koku` and lose the Visit right.
- [MAYBE] Proactive Visit the Emperor gives `+1 Koku` in addition to reshuffle.
- [NO] Proactive Visit the Emperor gives `+1 Koku` only if the player includes the entire hand in the reshuffle.
- [NO] Proactive Visit the Emperor raises storage cap by `+1` until end of turn (temporary logistics boost).

## Ideas: Imperial Zones / Map Zones
- [MAYBE] Controlling all 4 Imperial Zones grants `+1 Koku` extra.
- [NO] Controlling all 4 Imperial Zones increases counting cap by `+1` (instead of direct Koku).
- [NO] Controlling all 4 Imperial Zones reduces Reveal cost by `1` (while maintained).
- [MAYBE] Add 1-2 marked non-Imperial "Trade Zones" that grant `+1 Koku` when controlled.
- [MAYBE] Add rotating "Rice Zone" markers for scenarios (selected legal map zones grant `+1 Koku` when controlled).
- [NO] Zone diversity bonus: controlling at least `2` non-Imperial Zones grants `+1 Koku`.
- [MAYBE] Line emphasis: Lines give `+2 Koku` while Zones remain `+1` (push expansion over turtling).

## Ideas: Attacks / Plunder / Interaction-Based Economy
- [MAYBE] Plunder rule: when you destroy/remove an opponent Market, gain `+1 Koku`.
- [NO] Plunder rule: when you destroy/remove an opponent Castle, gain `+1 Koku`.
- [NO] Plunder rule (combined): when you remove an opponent building (Market/Castle), gain `+1 Koku`.
- [NO] When an effect removes a Protection token from an opponent Daimyo reserve, the attacker may take `+1 Koku` instead of taking that token.
- [NO] When an effect removes a Protection token from an opponent Daimyo reserve, gain both the token and `+1 Koku` [HIGH RISK].
- [NO] Siege reward: removing protection from a card that has a building grants `+1 Koku`.
- [MAYBE] Attack pressure reward: removing any opponent token/building grants `+1 Koku` [watch aggression spikes].

## Ideas: Board Presence / Number of Cards in Play
- [MAYBE] Domain size bonus: if your connected Chain of Command has at least `X` cards, gain `+1 Koku` (test `X = 7/8/9`).
- [YES] Domain size bonus counts only connected face-up Numbered cards (avoid stack/trap inflation).
- [NO] Board presence cap bypass: above `X` connected cards, increase counting cap by `+1`.
- [NO] Board presence by zones + cards: if you control at least 1 Zone and have at least `X` connected Numbered cards, gain `+1 Koku`.
- [MAYBE] Retainer-light economy: only Numbered cards count for domain Koku bonus (discourages "pile spam").

## Ideas: Missions / Objectives
- [NO] Completing a Mission grants `+1 Koku` immediately (VP reward unchanged).
- [NO] Mission reward split: Mission gives `+1 VP +1 Koku` instead of `+2 VP`.
- [NO] Mission reward becomes `+2 VP or +2 Koku` (player choice) [HIGH VARIANCE].
- [NO] Mission completion increases storage cap by `+1` (instead of direct Koku).

## Ideas: Errors / Rebellions (After Reward Changed to Protection Token)
- [YES] Error correction reward = `1 Protection token OR 2 Koku` (player chooses per corrected Error).
- [NO] Error correction reward stays `1 Protection token`; if token cannot be legally placed and Daimyo reserve is full, gain `1 Koku` instead of losing it.
- [NO] Error correction reward = `1 Protection token` plus `+1 Koku` only when correcting an opponent-created Error [HIGH RISK / bookkeeping].
- [MAYBE] Error correction before the turn is over `+1 Koku`. 

## Ideas: Protection Token Flow (Direct Token Increase / Better Token Access)
- [NO] Daimyo reserve full (`3`) grants `+1 Protection token` to personal supply at end of turn [watch snowball].
- [NO] Connected Castle grants `+1 Protection token` to personal supply during end-of-turn collection (max 1 from Castles total).
- [MAYBE] Market grants `+1 Protection token` instead of extra Koku [alternative economy model].
- [NO] Market gives a choice during collection: `+1 Koku` OR `+1 Protection token`.
- [MAYBE] Controlling all 4 Imperial Zones grants `+1 Protection token` (placed legally or parked on Daimyo reserve if needed).
- [NO] Controlling a marked non-Imperial trade/rice zone grants `+1 Protection token` instead of Koku (scenario lever).
- [NO] Domain size bonus pays `+1 Protection token` instead of `+1 Koku` (or choose one).
- [MAYBE] Proactive Visit the Emperor grants `+1 Protection token` (legal placement or Daimyo reserve) instead of / in addition to Koku.
- [NO] Build rebate: when creating a Market, immediately gain `+1 Protection token` to personal supply.
- [NO] Build rebate: when creating a Castle, immediately park `+1 Protection token` on Daimyo reserve (if space).
- [MAYBE] Build rebate: when creating a Castle, immediately park `+1 Koku`
- [NO] Attack plunder token mode: removing an opponent building grants `+1 Protection token` instead of `+1 Koku`.
- [NO] Daimyo reserve logistics: increase Daimyo reserve capacity from `3` to `4` [simple but risky for build pacing].

## Ideas: Token Conversion / Efficiency (Not More Koku, More Useful Koku)
- [NO] Improve conversion rate globally to `3 Koku -> 2 Protection` [HIGH RISK, likely fast].
- [NO] With Market, improve conversion rate to `3 Koku -> 2 Protection`.
- [NO] With at least 1 connected Castle, improve conversion rate to `3 Koku -> 2 Protection`.
- [NO] Allow split conversion `1 Koku + 1 parked Daimyo reserve token -> 1 new Protection token` [complex].
- [NO] Convert Koku normally (`2 -> 1`) but converted tokens may always be parked on Daimyo reserve if legal map placement is not desired.
- [NO] Add a "construction action" option: spend `3 Koku` directly to gain `1 Protection token` on Daimyo reserve + `1 Protection token` in supply [test only].

## Ideas: Protection Token Placement Flexibility (Increases Effective Token Use, Not Raw Generation)
- [NO] Tokens gained from error correction may be parked on Daimyo reserve even if a legal map placement exists (player choice).
- [ALREADY] Converted Protection tokens may be placed on Daimyo reserve directly (up to cap) instead of immediately on map.
- [NO] Allow moving 1 Protection token from a connected card to Daimyo reserve during your turn (once per turn optional bookkeeping note) [trigger-like].
- [NO] Allow redistributing 1 Protection token between connected cards in chain during your turn (no net gain, but smoother building setup).
- [ALREADY] Building commitment may include tokens from Daimyo reserve first (priority wording clarification; likely already legal).

## Ideas: Mixed Koku + Token Levers (Choice-Based, Flexible, Lower Symmetry)
- [MAYBE] Market construction costs `2 Protection token`.
- [NO] Market collection choice: `+2 Koku` OR `+1 Koku +1 Protection token`.
- [NO] Castle collection choice: `+1 Koku` OR `+1 Protection token` (connected only).
- [NO] Mission completion reward choice: `+2 VP` OR `+1 VP +1 Koku +1 Protection token`.
- [YES] Error correction reward choice per error: `1 Protection token` OR `1 Koku`; if correcting 2+ errors, choices may mix.
- [NO] Imperial domination (all 4): choose `+1 Koku` OR `+1 Protection token` OR `+1 counting cap until end of turn`.

## Ideas: Global / Simple Levers (Easy to Test, Higher Risk of Symmetry)
- [MAYBE] `+1 Koku` at setup for all players (flat).
- [NO] `+1 Protection token` in Daimyo reserve at setup for all players (flat).
- [NO] `+1 Koku +1 Protection token` at setup for all players (flat) [watch symmetry strongly].
- [NO] `+2 Koku` at setup for all players (flat) [usually too much].
- [NO] Increase base income from `+1` to `+2` [likely too fast].
- [MAYBE] Increase storage cap from `6` to `7`.
- [NO] Increase storage cap from `6` to `8` [watch hoarding].

## Low-Preference / Trigger-Style Ideas (Keep for Reference, Probably Skip)
- [NO] If you start your turn with `0 Koku`, gain `+1 Koku` (catch-up smoothing).
- [NO] First Reveal each turn costs `2` instead of `3`.
- [NO] First offensive interaction each turn grants `+1 Koku`.

## Recommended Test Packages (Combinations)
- [ ] Package A (minimal / clean):
  - `Market = +2 Koku`
- [ ] Package B (strong recommendation, controlled):
  - `Market = +2 Koku`
  - Market bonus outside counting cap
- [ ] Package C (interaction-focused):
  - `Market = +2 Koku`
  - Reveal costs `2 Koku`
- [ ] Package D (build acceleration via Market, not direct Koku):
  - `Market = +2 Koku`
  - OR (alternative) `With Market: 3 Koku -> 2 Protection` (do not combine both in first test)
- [ ] Package E (anti-turtle / conflict economy):
  - `Market = +2 Koku`
  - Plunder on Market/Castle removal = `+1 Koku`
  - All 4 Imperial Zones -> counting cap `+1`
- [ ] Package F (Daimyo reserve economy):
  - `Market = +2 Koku`
  - Daimyo reserve token may pay `1 Koku` worth of Reveal / paid-last-card cost
  - Daimyo reserve full (`3`) grants `+1 Koku` at end of turn
- [ ] Package G (very conservative, no new triggers):
  - `Market = +2 Koku`
  - Base income outside counting cap
- [ ] Package H (token flow via existing systems, minimal board flood):
  - Error correction reward = `1 Protection token` (current)
  - Tokens gained from error correction may be parked on Daimyo reserve even if legal map placement exists
  - Market gives collection choice: `+1 Koku` OR `+1 Protection token`
- [ ] Package I (mixed economy, interaction pressure):
  - `Market = +2 Koku`
  - Plunder on building removal = choose `+1 Koku` OR `+1 Protection token`
  - All 4 Imperial Zones = choose `+1 Koku` OR `+1 Protection token`
- [ ] Package J (construction pace without raw Koku buff):
  - With Market, conversion = `3 Koku -> 2 Protection`
  - Build rebate on Market OR Castle (`+1 Protection token`, choose one rule only)

## Test Notes Template (Copy Per Match)
- [ ] Rule package tested:
- [ ] Avg turn Koku feel (low / ok / high):
- [ ] Token availability feel (low / ok / high):
- [ ] Daimyo reserve usage (low / ok / high):
- [ ] Construction pace (slow / ok / too fast):
- [ ] Map token saturation (low / ok / too high):
- [ ] Turtle behavior observed? (yes/no):
- [ ] Symmetric openings observed? (yes/no):
- [ ] Reveal/trap interaction level (low / ok / high):
- [ ] First Castle timing felt:
- [ ] First Capital timing felt:
- [ ] Mission completion rate:
- [ ] Winner / why:
- [ ] Adopt / retest / reject:
