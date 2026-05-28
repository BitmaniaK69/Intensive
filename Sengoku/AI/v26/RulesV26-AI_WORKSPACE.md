# Sengoku V26 - AI Workspace

This is a working file for Codex/AI assistance.

It is not the rulebook.
It is not player-facing.
It is not the source of truth for final rules.

Primary working rulebook:

- [RulesV26-Final.md](./RulesV26-Final.md)

Previous V25 baseline:

- [../v25/RulesV25-Final.md](../v25/RulesV25-Final.md)

Pedro original export/copy:

- [Sengoku V26 – Pedro's take.md](./Sengoku%20V26%20%E2%80%93%20Pedro's%20take.md)

Purpose of this file:

- Track future V26 design decisions.
- Track differences from V25.
- Track ambiguous or unresolved rules.
- Keep notes from playtests and conversations.
- Keep manual-writing notes separate from the actual rulebook.
- Prevent accidental loss of context when editing `RulesV26-Final.md`.

---

## 1) Working Authority

For V26 work, use this hierarchy:

1. `RulesV26-Final.md` - current V26 working rulebook.
2. Current conversation decisions explicitly approved by Gianluca.
3. `RulesV25-Final.md` - previous rules baseline, used only for comparison/recovery.
4. Pedro's original take - useful for understanding the rewrite, but not above `RulesV26-Final.md`.

If this workspace conflicts with `RulesV26-Final.md`, the rulebook wins unless the task is specifically to update the rulebook.

---

## 2) Current V26 Direction

V26 is not just a text cleanup of V25.

It is a streamlined version based on Pedro's manual rewrite, with several intended simplifications:

- Shorter and more teachable manual.
- Cleaner terminology.
- Fewer sub-phases.
- Koku capped at 5 physical tokens per player.
- Protection, Market, Castle, and Capital treated as token-like components.
- Disputed Spaces replace Imperial Zones as the shared central-space term.
- Rebellions replace Errors as the thematic illegal-state term.
- Prefecture cards replace Numbered cards as the thematic card term.
- Capital placement simplified by flipping one of the Castle cards face-down.

These are working directions, not all final balance decisions.

---

## 3) Known V25 -> V26 Differences To Track

### Terminology

- `Numbered cards` -> `Prefecture cards`.
- `Errors` -> `Rebellions`.
- `Imperial Zones` -> `Disputed Spaces`.
- `Line` and `Zone` may be merged under `Zone`.
- `Protection / Market / Castle / Capital` are described as tokens in V26.

### Setup

- V26 currently uses board Daimyo icons for setup.
- V25 used a broader Junbi setup with many legal starting locations.
- Need to decide whether V26 fixed icons are final.

### Turn Structure

V26 currently uses:

- perform actions in any order;
- free card play if you have 3+ cards;
- pay K1 to play when you have 2 cards;
- end turn with income, discard down to 2, draw to 3.

V25 used:

- Beginning of Turn;
- Active Turn;
- Collect Resources;
- End of Turn.

Need to confirm V26 turn structure after testing.

### Koku

V26 uses 5 Koku tokens per player as physical available/used tokens.

Open checks:

- Does paying Koku mean "set aside" until regained?
- Are Koku tokens ever unavailable due to component shortage? No, cap is 5.
- Does Koku still act as tie-breaker? V26 currently says no.

### Rebellions

V26 has two concepts:

- preventing a just-played Rebellion before the active player's turn ends;
- resolving existing/unpreventable Rebellions during your turn.

Needs clarification:

- Can multiple Rebellions be resolved in one turn?
- Does one removal resolving multiple Rebellions give one or multiple Protection rewards?
- Can a player profit from a Rebellion they created that turn? Intended: no.

### Disputed Spaces

V26 uses Disputed Spaces for:

- 6x6 / 9x9 central Imperial-area spaces;
- 5x5 Duel river/bridge spaces.

Current historical note direction:

```text
On the 6x6 and 9x9 boards, Disputed Spaces evoke Kyoto and the Imperial Court:
places of imperial influence and prestige, contested by Daimyo seeking recognition and control.

On the 5x5 board, they represent a river crossing or narrow battlefield,
evoking Sengoku rivalries such as Kawanakajima, where position, timing,
and control shaped the struggle for power.
```

### Building And Capital

Current V26:

- Market: 2 Protection tokens from cards in chain.
- Castle: 3 Protection tokens from cards in chain.
- Mandatory Castle if 3 Protection tokens are specifically on Prefecture cards in chain.
- Capital: remove 3 Castles in chain, flip one of the cards that had a Castle face-down, place Capital there.

Open checks:

- Is building allowed only right after playing a card/Protection, or anytime during your action sequence?
- Is broad relocation of tokens from the board intended when supply is empty?
- Should Capital be relocatable? Likely no.

### Game End

Current V26:

- first Capital triggers endgame;
- active player finishes current turn;
- Imperial Summons gives one final limited turn to each player;
- no cards drawn or played during Imperial Summons;
- allowed: flip face-down cards, play Protection, resolve Rebellions.

Open checks:

- Should Rebellions be allowed in Imperial Summons?
- Does a player who builds a later Capital during Imperial Summons score order VP? Current text: yes through scoring.

### Scoring

Current V26:

- Capital order VP: 4 / 3 / 2 / 1.
- Then within chain: +1 per face-up Prefecture/Retainer, +1 per controlled zone, +1 per Disputed space, +1 per Castle, +4 per Capital.
- Tie-breaker: first to build Capital.

Open checks:

- Capital may be worth too much: first Capital currently appears to be worth 8 VP total before board scoring.
- Tie-breaker fallback text is intentionally humorous but may need finalization.
- Expert scoring must include Destiny Path and unused Emperor Visit.

---

## 3b) Deep V25 -> V26 Change Map

This section tracks the practical differences between `RulesV25-Final.md` and the current `RulesV26-Final.md`.

Categories:

- `Editorial`: mainly wording/structure.
- `Simplification`: same intent, less rules overhead.
- `Gameplay Change`: changes what happens at the table.
- `Risk / Needs Decision`: unclear whether this is intentional or safe.

### A) Scope, Player Count, And Product Shape

V25:

- Base game described as 4 players.
- 2-player Duels and 5-6 player Grand Campaign are supported in the rules.
- Components list includes base + expansion clan references.

V26:

- Header says `2-4 players`.
- 5-6 players are moved to a short expansion section.
- 2-player is integrated into the main setup/rules rather than a separate Duel chapter.

Classification:

- `Gameplay Change`.

Impact:

- V26 is cleaner for a base-box manual.
- 5-6 player rules are currently under-specified.
- Duel loses some dedicated V25 detail unless the board icons carry that information.

Open decision:

- Is V26 officially a 2-4 player base game with 5-6 as expansion?
- Should the 5x5 board be a normal board variant or still a named Duel mode?

### B) Components

V25:

- 4 player decks of 20 cards: 12 Numbered, 6 Retainers, 1 Extra Special Retainer, 1 Daimyo.
- 36 Koku tokens listed, originally 9 per player.
- Emperor Visit markers are components.
- Markets, Castles, and Capitals are listed as pieces.

V26:

- 4 decks: 1 Daimyo, 7 Retainers, 12 Prefecture cards.
- 5 Koku per player.
- 6 Protection per player.
- Market, Castle, Capital called tokens.
- No Emperor Visit marker component.

Classification:

- `Simplification` for Koku count and component kit.
- `Gameplay Change` for Emperor Visit marker removal.
- `Risk / Needs Decision` for calling all buildings `tokens`.

Impact:

- 5 Koku per player matches the cap and production direction.
- Removing Emperor markers simplifies components, but requires clear deck/discard tracking.
- Calling Market/Castle/Capital `tokens` may blur the difference between Protection tokens and structure tokens.

Open decision:

- Keep `Market token`, `Castle token`, `Capital token`, or use `piece`/`marker` to avoid confusion?

### C) Setup And Junbi

V25:

- Daimyo is removed from deck and parked beside the player board.
- Starting Protection `+P1` on Daimyo by default.
- Determine only first player, then clockwise.
- Junbi phase: players place Daimyo on legal starting edge locations.
- 6x6 had many legal coordinates: B1, D1, C1, E1, A2, F2, A3, F3, A4, F4, A5, F5, B6, C6, D6, E6.
- Corner spaces invalid.
- Daimyo placement must respect row/column/zone restrictions.

V26:

- Board has printed Daimyo icons.
- In turn order, players place Daimyo with 1 Protection token on a Daimyo-icon space.
- Turn order may use player-board order number or random first player/clockwise.
- Expert Mode later allows broader edge setup.

Classification:

- `Gameplay Change`.

Impact:

- Basic setup becomes much faster and easier.
- Fixed icons remove much of the open-start Junbi metagame.
- Expert setup now contains the more flexible edge-placement idea.
- This may improve first-game clarity but changes balance/testing assumptions from V25.

Open decision:

- Is fixed-icon Daimyo setup intended for Basic Mode?
- Is flexible Junbi now Expert-only?
- Should order numbers be authoritative again, or remain optional/theme?

### D) Core Board Terms

V25:

- `Zone`: printed 3x2 area.
- `Line`: full row or column.
- `Imperial Zone`: special central Emperor-marked spaces.
- A prefecture could contribute to both Zone and Line.

V26:

- `Zone`: any row, column, or pre-determined area.
- `Disputed Spaces`: special central spaces.
- `Line` no longer appears as a separate term.
- `Imperial Zone` no longer appears as a rules term.

Classification:

- `Simplification` plus `Gameplay Change`.

Impact:

- Very clean wording: row, column, and printed area are all zones.
- It removes separate Line terminology.
- It may increase scoring/income if every row/column and printed area is a zone unless clearly illustrated.
- Players need a diagram to understand which zones count on each board.

Open decision:

- Does `controlled zone` include every complete row, every complete column, and every printed area?
- If yes, scoring/income density changed from V25 and must be tested.

### E) Disputed Spaces

V25:

- `Imperial Zones` were four central marked spaces on 6x6.
- They granted +K1 if controlled and connected to Chain.
- They could not receive face-down cards, Protection, buildings, or normal Numbered-on-Numbered overlap.

V26:

- `Disputed Spaces` are central special spaces.
- 6x6/9x9 theme: Kyoto / Imperial Court.
- 5x5 theme: river crossing / narrow battlefield.
- Each Disputed space in chain gives +K1.
- In 2-player, only the middle Disputed space gives +K1.
- Disputed spaces cannot have tokens, face-down cards, or stacked Prefecture cards; some Retainers can stack there.

Classification:

- `Simplification` and `Gameplay Change`.

Impact:

- `Disputed Spaces` works better across 5x5/6x6/9x9.
- Income requirement is now `in your chain`, not explicitly `controlled`.
- Scoring separately awards +1 VP per Disputed space within chain.

Open decision:

- Should Disputed spaces require full control, or only being in chain?
- Confirm 5x5: which Disputed spaces give Koku, score, both, or neither.

### F) Control And Chain

V25:

- Control explicitly uses top cards in stacks.
- Face-down top cards count as clan for control.
- Chain is orthogonal only from Daimyo.
- Only connected cards/structures score.

V26:

- Control: zone under control if all spaces are occupied by your cards, face up or down.
- Chain: starts at Daimyo and includes orthogonally connected cards.
- Stacks: only top card is relevant for effects, limitations, and scoring.

Classification:

- `Editorial` / `Simplification`.

Risk:

- V26 should explicitly connect these statements:
  - in a stack, only top card counts for control;
  - face-down top card counts for owner/control/chain.

Open decision:

- Add one sentence to Control or Cards to avoid ambiguity.

### G) Turn Structure

V25:

- Four phases:
  1. Beginning of Turn refill to 3.
  2. Active Turn: play down to 2, optionally pay K1 to play down to 1.
  3. Collect Resources.
  4. End of Turn refill to 3.
- Beginning refill mostly exists to recover from off-turn hand loss.
- Active Turn has a hand-size exit gate.

V26:

- Single action sequence.
- You may play a card for free if you have 3+ cards.
- You may pay K1 to play a card if you have 2 cards.
- At end, gain income, discard down to 2 if needed, draw to 3.
- No explicit beginning refill in Basic Mode.

Classification:

- `Gameplay Change`.

Impact:

- Much easier to teach.
- Makes extra cards drawn mid-turn playable if you still have 3+ cards.
- End-turn discard to 2 is new and may make draw effects less explosive.
- Off-turn hand destruction recovery depends on end/start timing; if a player starts with fewer than 3 due to off-turn effect, current V26 has no beginning refill unless end-turn refill already happened.

Open decision:

- Is V26 intentionally removing beginning-of-turn refill?
- If off-turn effects reduce your hand, how do you recover before actions?
- Does Samurai draw-one exist partly to solve this?

### H) Koku Handling

V25:

- Koku stored on player board, cap K5.
- End-of-turn counting cap max +K5.
- Spending and gaining use a storage model.
- Koku tie-breaker existed.

V26:

- Each player has exactly 5 physical Koku.
- Paying sets Koku aside away from supply.
- Gaining takes set-aside Koku back.
- Surplus ignored.
- Tie-breaker no longer uses Koku.

Classification:

- `Simplification` and likely improvement.

Impact:

- Clean component logic.
- Available/used Koku sides or spaces become possible.
- Koku no longer needs excess components.

Open decision:

- Confirm Koku cannot exceed 5 under any circumstance, including Alliances.

### I) Income

V25:

- Base +K1.
- Market +K1.
- Each controlled Zone +K1.
- Each controlled Imperial Zone +K1 if connected.
- Line income existed in play summary and tests, but source wording had some ambiguity.
- Income cap max +K5 per count.

V26:

- Base +1.
- +1 per Disputed space in chain.
- +1 per controlled zone in chain.
- +1 if Market is in chain.
- No separate income cap sentence because physical Koku cap handles surplus.

Classification:

- `Simplification` plus `Gameplay Change`.

Impact:

- Rows/columns/areas all being zones may increase income opportunities.
- Disputed income is tied to chain, not full control.
- Market must be in chain to provide income.

Open decision:

- Should all controlled zones in chain generate income, or only printed area zones plus rows/columns as intended?

### J) Card Types And Placement

V25:

- `Numbered Cards`.
- Numbered cards can be placed anywhere legal.
- Face-down Numbered placeholders can be placed anywhere legal except Imperial Zones.
- Retainers may coexist in row/column/zone.
- Numbered stack only on your own face-up Numbered if legal.
- Numbered cannot stack on Retainers.
- No stacking on face-down unless effect says so.

V26:

- `Prefecture Cards`.
- Face-up on empty space.
- Face-up stacked on top of one of your face-up Prefecture cards with no tokens on non-Disputed spaces.
- Face-down on empty non-Disputed space.
- Retainer placement is handled only by Retainer card text.

Classification:

- `Simplification`.

Gameplay Changes:

- Face-down Prefecture placement only on empty non-Disputed spaces.
- Prefecture stacking explicitly blocked by any token.
- Placement text no longer explicitly says Prefecture placement does not need Chain.

Open decision:

- Confirm Prefecture cards still do not need chain connection to be placed.
- Confirm face-down cards are only on empty spaces unless Retainer effect says otherwise.

### K) Rebellions / Errors

V25:

- `Errors - Rebellions`.
- Immediate illegal placement called before Collect Resources.
- Acting player corrected immediately by placing that card face-down legally or discarding.
- No reward for immediate correction.
- Existing errors can be fixed on your turn.
- Fixer chooses removal order and offending card.
- One removal may resolve multiple Errors; reward +1 Protection per Error resolved.
- Cannot create an Error and profit from fixing it in same turn.

V26:

- `Rebellion` if two face-up Prefecture cards of same number are within same zone.
- Preventing Rebellions: if a card causes rebellion immediately upon being played, anyone can force its player to play it elsewhere or discard it before turn ends.
- Resolving Rebellions: during your turn, if rebellion cannot be prevented, choose one of the cards to discard with tokens; reward play one Protection token.

Classification:

- `Simplification` plus `Gameplay Change`.

Impact:

- Immediate correction is now replay elsewhere or discard, not necessarily move face-down.
- Reward appears to be one Protection per resolution, not per Rebellion resolved.
- Needs explicit multi-Rebellion handling.
- V26's "cannot be prevented" language is good, but could be clearer.

Open decision:

- Reward per removed card, per resolved Rebellion, or per action?
- Can one player resolve multiple Rebellions in one turn?
- If one removal reveals another Rebellion, can it be resolved immediately?

### L) Protection And Tokens

V25:

- Protection tokens placed on Numbered or Retainer cards, max one piece per card: Protection or building.
- Face-down cards cannot receive Protection.
- Daimyo can hold up to 3 reserve Protection tokens but they do not protect Daimyo automatically.
- Gained Protection must be placed immediately if legal; otherwise discarded.
- Protection can contribute to building progression.

V26:

- Protection tokens placed on own face-up cards on non-Disputed spaces with no tokens, or Daimyo up to three Protection tokens.
- Cards with tokens are usually safe from most Retainer abilities.
- Surplus Protection ignored.

Classification:

- `Simplification`.

Gameplay Changes:

- V26 says Protection only on your own face-up cards.
- V26 treats Daimyo Protection placement more directly.
- V26 does not clearly separate Daimyo reserve from true protection.
- `Usually safe` is not precise enough.

Open decision:

- Do Protection tokens on Daimyo protect Daimyo or remain reserve only?
- Should Protection be placeable on Retainers as in V25? V26 says "your face-up cards", so yes unless unintended.
- What happens when gained Protection cannot be legally placed?

### M) Building Market / Castle

V25:

- Build through Protection-token progression.
- Market: 2 Protection from cards in Chain.
- Castle: 3 Protection from cards in Chain.
- Destination must be connected Numbered card with no building.
- Destination need not be token source.
- Market optional.
- Castle mandatory only if 3 Protection on connected Numbered cards and destination exists.
- Tokens from Retainers/Daimyo reserve can contribute but do not force mandatory conversion.
- Max 1 Market, max 3 Castles.
- 4th Castle handling allowed relocating existing Castle only under specific rules.

V26:

- Right after playing a card or Protection, discard 2 Protection from cards in chain to build Market or 3 to build Castle.
- Mandatory Castle if 3 Protection specifically on Prefecture cards in chain.
- Place Market/Castle token on face-up Prefecture in non-Disputed chain with no tokens.
- If supply empty, take one token of that kind from those already on board.

Classification:

- `Simplification` and `Gameplay Change`.

Impact:

- Timing is narrower: "right after playing a card or Protection token".
- Broad relocation rule replaces V25's specific Castle limit handling.
- Market relocation may become legal.
- Capital relocation might accidentally become legal if "something" includes Capital.

Open decision:

- Should build be an action available anytime during your action step?
- Should only Castle relocation be allowed, or all token types?
- Should Market be movable when rebuilding?

### N) Capital Formation

V25:

- 3 connected Castles in Chain.
- Remove 3 Castles and place Capital immediately.
- Capital always placed on a face-down base card.
- Could use existing face-down card in chain, or flip a face-up Numbered card.
- Current ruleset max 1 active Capital.

V26:

- If you have 3 Castles in chain, remove them.
- Flip face down one of the cards that had them.
- Place Capital there.
- Card with Capital cannot be flipped or discarded while Capital remains.

Classification:

- `Major Simplification`.

Impact:

- This is cleaner and likely better.
- Removes choice complexity and hidden trap/capital base weirdness.
- Ensures Capital comes from actual Castle line.

Open decision:

- Confirm this is accepted V26.
- Add explicit max 1 Capital or rely on component limit?

### O) Game End / Imperial Summons

V25:

- Valid connected Capital triggers Imperial Summons immediately.
- First Shogun finishes turn normally.
- Then every player takes one restricted final turn, starting after first Shogun and ending with first Shogun.
- Restricted turns: no card play/place; only Reveal and Koku->Protection/build progression.
- No Visit Emperor.
- No normal end refill.
- Later Capital counts for Shogun order but does not restart endgame.

V26:

- Once first Capital is built, active player continues current turn as normal.
- Imperial Summons round gives each player one final limited turn, including first Capital builder last.
- No cards drawn nor played.
- Allowed: pay K3 to flip face-down, pay K2 to play Protection, resolve Rebellions.

Classification:

- `Simplification` plus `Gameplay Change`.

Impact:

- Much clearer than V25.
- Allows Rebellion resolution in final round.
- Does not explicitly mention building Market/Castle/Capital in Imperial Summons, but Protection placement may trigger building rules if requirements are met.
- "Cards are no longer drawn nor played" interacts with Shinobi/Samurai draw effects if they can trigger.

Open decision:

- Are building conversions allowed during Imperial Summons after playing Protection?
- Are Rebellions intended to be resolvable during Imperial Summons?
- Can Retainer reactions happen during Imperial Summons?

### P) Scoring

V25:

- +1 face-up Numbered/Retainer.
- +1 each full zone or line under control.
- +1 each Castle.
- +3 each Capital.
- Shogun order: +4/+3/+2/+1.
- Expert: +1 unused Emperor.
- Tie-breaker: highest remaining Koku, then shared victory.

V26:

- Capital order VP: 4/3/2/1.
- Then in chain:
  - +1 face-up Prefecture/Retainer;
  - +1 controlled zone;
  - +1 Disputed space;
  - +1 Castle;
  - +4 Capital.
- 2-player: top/bottom row face-up cards do not score.
- Tie-breaker: first Capital.

Classification:

- `Gameplay Change`.

Impact:

- First Capital is now very high value: +4 order plus +4 Capital = 8 VP, before other board points.
- V25 first Shogun with Capital was +4 +3 = 7 VP, similar but not identical.
- Later Capitals also get Capital +4 plus order points.
- Tie-breaker by first Capital is clean and non-random.
- Expert bonus and Destiny Path are not integrated in this scoring section.

Open decision:

- Is Capital +4 final, or should it remain +3?
- Should first Capital order VP be +3/+2/+1/0 or +4/+3/+2/+1?
- Replace joke fallback tie-breaker with shared victory or another final rule.

### Q) Retainer Icon System

V25:

- Tags included `[DISCARD]`, `[PLACE]`, `[PLACE_CHAINED]`, `[COVER]`, `[TRAP]`.
- Some actions combined placement modes.
- Trap was partly tied to specific card text.

V26:

- Only three icons:
  - `[PLACE]`;
  - `[TRAP]`;
  - `[DISCARD]`.

Classification:

- `Strong Simplification`.

Impact:

- Much easier to teach and print.
- Places more burden on each action text to specify where/how placement works.

Open decision:

- Is `[COVER]` fully removed as an icon and folded into `[PLACE]` text?

### R) Retainers - Samurai

V25:

- Place near chain or cover own clan card.
- Kill 1 adjacent unprotected card OR remove 1 Token or 1 Market.
- A2 reaction cancels declared Retainer action before it resolves; discard that card too; cannot block Trap effects.

V26:

- Place on empty adjacent-to-chain space or on own face-up Prefecture.
- Discard up to one non-Daimyo card with no tokens around Samurai, or remove one Protection token from that card.
- A2 cancels a Retainer card just played face-up, discarding it with no effect, then draw one.

Classification:

- `Gameplay Change`.

Impact:

- Market removal removed.
- Target wording may imply the Protection token removed must be from the same card "around this Samurai".
- Samurai draw-one after cancel is new and may buff reactions.
- Cancel no longer clearly covers discard-mode Retainers like Chajin.

Open decision:

- Does Samurai cancel Retainer actions or only face-up Retainer cards?
- Can Samurai remove Market? Current V26 says no.

### S) Retainers - Ashigaru

V25:

- Place near chain or cover own-clan unprotected Numbered.
- Kill up to 2 adjacent unprotected Numbered or face-down cards.

V26:

- Place on empty adjacent-to-chain space or on own Prefecture.
- Discard up to 2 Prefecture or face-down cards with no token around Ashigaru.

Classification:

- `Simplification` with small `Gameplay Change`.

Impact:

- Similar role.
- "On top of one of your Prefecture cards" does not specify face-up or no tokens in the action text, though global token rule may imply no tokens.

Open decision:

- Should Ashigaru be allowed on face-down own Prefecture? Current text says Prefecture, but likely should be face-up/no-token.

### T) Retainers - Shinobi

V25:

- A1 removes 1 Retainer and any Token on it, or 1 face-down.
- A2 spy hand, choose 2 cards to discard, draw +1 at end; trap affects revealer.

V26:

- A1 discards up to one Retainer or face-down card, along with any Protection token it has.
- A2 is `[TRAP]`: when flipped, look at player's hand, choose up to 2 cards to discard, discard Shinobi, draw 1.

Classification:

- `Gameplay Change`.

Impact:

- Shinobi hand attack becomes trap-only.
- A1 now only mentions Protection token, not Market/Castle/Capital.
- Draw timing immediate after trap resolution.
- Owner self-reveal not defined.

Open decision:

- Latest design likely changes Shinobi trap self/opponent behavior; integrate when accepted.

### U) Retainers - Ronin

V25:

- A1 replace unprotected top non-Ronin; return target; discard/return rest.
- A2 steal up to 2 tokens from other clans, max 1 per clan, rest from supply; trap from revealer first.

V26:

- A1 choose non-Ronin, non-Daimyo card with no tokens; discard up to one card stacked there and return all others; place Ronin there.
- A2 `[TRAP]`: when flipped, remove up to one Protection from that player, discard Ronin, play up to two Protection.

Classification:

- `Major Gameplay Change`.

Impact:

- A1 is simpler but may return useful cards to opponent.
- A2 is trap-only and weaker/more abstract than latest discussion.
- It does not match current desired direction where Ronin may stay on board and steal/gain up to two Protection.

Open decision:

- Ronin needs dedicated redesign before V26 final.

### V) Retainers - Chajin / Sohei

Chajin:

- V26 mostly matches V25, with shorter wording.

Sohei:

- V26 mostly matches V25, with shorter wording.
- Ownership/target clan should be clarified.

Classification:

- `Editorial` / `Simplification`.

### W) Expert Mode - Emperor Visit

V25:

- Uses Emperor Visit marker.
- Proactive Visit after beginning refill and before action.
- Shuffle deck + discard + hand, draw 3.
- First required-draw deck exhaustion consumes unused Emperor right.
- If unused at scoring, +1 VP.

V26:

- No marker.
- Deck/discard position on player board tracks whether reshuffled.
- Once per game, during your turn, shuffle discard into deck.
- May discard hand before shuffling and draw 3.
- Cannot do during Imperial Summons.
- If never used, +1 VP.
- Cannot shuffle discard into deck in any other way, even if out of cards.

Classification:

- `Simplification` plus `Gameplay Change`.

Impact:

- Component reduction is good.
- The no-shuffle-if-empty rule may be harsh and needs clarity.
- Forced reshuffle handling is missing from main text.

Open decision:

- If deck empties before Emperor Visit, is the right automatically used/lost?
- If deck empties after Visit, does player simply stop drawing?

### X) Expert Mode - Alliances

V25:

- Alliance token is Protection token of allied player's color on Daimyo.
- Not spendable.
- Allied players cannot reveal each other's face-down cards unless allowed.
- Breaking/removal rules were playerboard-driven.
- 5-6 player Expert Mode allowed at most 2 simultaneous alliances.

V26:

- Each ally places one Protection token on the ally's Daimyo.
- These tokens only represent Alliance and cannot be spent.
- Allies cannot flip each other's face-down cards or target each other's cards with Retainer effects.
- Up to two alliances at a time.
- If one marker removed, remove the other too.
- If you end one of your alliances this way during your turn, claim playerboard break reward.

Classification:

- `Gameplay Change`.

Impact:

- Up to two alliances is now general, not only 5-6.
- Protection marker handling is cleaner, but "end this way during your turn" could create break-reward disputes.
- Latest Koku-based alliance reward direction is not stated.

Open decision:

- Max 1 or max 2 alliances?
- Are alliance rewards in Koku?
- If a third player removes an alliance token, who, if anyone, gets break reward?

### Y) 5x5 Duel

V25:

- Dedicated Duel mode chapter.
- 5x5 board "The Challenge".
- First player placed Daimyo and one connected Numbered card; this was legacy and likely removed.
- Bridge center had special rule.
- Dedicated scoring spaces +1/+2.

V26:

- 5x5 is simply the two-player side of the board.
- No extra Prefecture start.
- Top/bottom row face-up cards do not score.
- Middle space is a zone of its own.
- Only middle Disputed space provides Koku.
- Some board icon details are implied but not fully in main text.

Classification:

- `Simplification` and `Gameplay Change`.

Impact:

- Removing extra opening Prefecture is accepted/desired.
- Needs final board-icon support for no-score/no-Koku spaces.

Open decision:

- Does 5x5 use full middle row as Disputed spaces, with only center giving Koku?
- Are marked +1/+2 spaces removed from Duel scoring?

### Z) 9x9 / 5-6 Players

V25:

- 9x9 Grand Campaign mentioned with dedicated setup sheet, Imperial Zones, zone geometry.
- Expansion clans named.

V26:

- Very short expansion section.
- Uses 9x9 board and extra player boards/decks/kits.
- No details yet.

Classification:

- `Omission / Deferred`.

Open decision:

- Keep V26 final focused on 2-4 and leave 5-6 to expansion rulebook?
- If included, 9x9 needs full setup and card-number range.

---

## 4) Retainer Issues To Track

### Trap Direction Under Discussion

Several trap models have been discussed.

Current Pedro/V26 text:

- Shinobi A2 is `[TRAP]`: when flipped, look at revealer's hand, discard up to 2, discard Shinobi, draw 1.
- Ronin A2 is `[TRAP]`: when flipped, remove up to 1 Protection token from that player, discard Ronin, play up to 2 Protection.

Latest conversation direction under consideration:

- Shinobi trap:
  - if revealed by opponent: owner looks at victim's hand, chooses up to 2 cards to discard, draws 1, then discards Shinobi;
  - if revealed by owner: no discard effect, owner draws 1, then discards Shinobi.
- Ronin trap:
  - if revealed by opponent: steal up to 2 Protection tokens from that opponent's cards anywhere on the board; for missing tokens, take from owner's supply instead; place gained Protection immediately if legal; Ronin stays face-up on the board;
  - if revealed by owner: no token effect; Ronin stays face-up on the board.

Not yet integrated into `RulesV26-Final.md`.

### Ronin A1

Current V26 text:

```text
[PLACE]: Choose a space with a non-Ronin, non-Daimyo card with no tokens,
discard up to one card stacked there and return all others to their owners' hands,
then place this Ronin there.
```

Open issues:

- Is this intended to target any clan, including your own?
- Should it discard the top card, an opponent card, or one selected card?
- Does it help the opponent too much by returning cards?
- Needs final cleanup.

### Samurai

Current V26:

- A1 places adjacent to chain or on own face-up Prefecture, then discards one nearby non-Daimyo card with no tokens or removes one Protection token.
- A2 cancels a just-played face-up Retainer and draws one.

Open checks:

- Does Samurai cancel an action or the card itself?
- Can it cancel discard-mode Retainers like Chajin?
- It should not cancel Trap effects unless explicitly changed.

### Ashigaru

Current V26:

- A1 places adjacent to chain or on own Prefecture, then discards up to two nearby Prefecture/face-down cards with no token.

Open check:

- Adjacent still includes diagonal. Pedro suggested maybe using same zone/line instead. Not accepted yet.

### Shinobi

Current V26:

- A1 discards up to one Retainer or face-down card from the board, along with any Protection token.

Open check:

- It should not remove Market/Castle/Capital unless explicitly allowed.

### Sohei

Current V26:

- Place on top any Prefecture, Sohei, or face-down card with no tokens.

Open check:

- Any clan or own clan? Current likely means any.

---

## 5) Expert Mode Issues To Track

### Emperor Visit

Current V26:

- no Emperor token;
- deck/discard location marks whether reshuffle was used;
- once per game, shuffle discard into deck;
- may discard hand before shuffling and draw 3;
- if never used, +1 VP.

Open checks:

- Forced reshuffle when deck runs out should probably consume this right and lose +1 VP.
- What happens if deck runs out after Emperor Visit was already used?

### Alliances

Current V26:

- allies place Protection tokens on each other's Daimyo as Alliance markers;
- markers cannot be spent as Protection;
- allies cannot flip each other's face-down cards or target each other's cards with Retainer effects;
- up to two alliances at a time;
- alliances end during Imperial Summons;
- if one marker is removed, both are removed.

Open checks:

- Earlier playerboards often said one pact at a time.
- Latest V25.2 direction converted alliance rewards to Koku.
- Need to align playerboards and manual.
- Need to decide if third-party removal gives break reward to anyone.

---

## 6) Missing Or Deferred Content

Potentially missing from current `RulesV26-Final.md`:

- Unique Special Retainers.
- Full 9x9 / 5-6 player setup details.
- 9x9 card number range if using 1-9.
- Duel board special scoring/no-Koku/no-score spaces.
- Complete playerboard mission/Destiny Path integration.
- Final trap rules.
- Full examples/diagrams.

---

## 6b) Gianluca Clarifications - 2026-05-26

These notes capture Gianluca's answers during the V26 review pass. Use them when updating `RulesV26-Final.md` or when discussing open items with Pedro.

### Review With Pedro - Running List

Bring these points to Pedro before editing the final rulebook text:

- Ronin Trap: the effect is clear as written, but confirm whether Ronin should really be discarded after resolving or remain face-up on the board.
- Samurai vs Market: current manual does not mention the card-specific rule that Samurai can discard a Market but not a Castle. Align manual and card.
- Token reuse: current manual broadly allows taking a built token from the board if supply is empty. Rewrite to apply to Protection, Market, and Castle only; Capital is unique and immovable for now.
- Alliance markers: current manual uses Protection tokens as alliance markers. Gianluca's direction is that these should be Alliance markers/tokens, not normal Protection tokens.
- Breaking alliances: current manual removes both alliance tokens. Gianluca's direction is that if one marker is removed, the alliance ends, rewards resolve, and the other ally converts their remaining marker into one of their own tokens unless player-board text says otherwise.
- Alliance rewards: confirmed direction is Koku rewards, respecting the Koku cap of 5. This is not a question, only an alignment/update point.
- Player-board conditional alliance rewards: manual should not assume only "if you break the alliance"; rewards can also be "if your alliance is broken" or other board-specific conditions.
- Rebellion multi-resolution: add explicit wording that multiple Rebellions can be resolved in the same turn, one at a time, and that order matters.
- Deck exhaustion / reshuffle limit: current normal rules allow reshuffling whenever needed; Gianluca's direction is that the deck may be reused only once. If it runs out again, draw fewer/no cards; if nobody can draw anymore, final sequence begins. Align with Emperor Visit wording.
- Emperor Visit / no-reshuffle VP: clarify that +1 VP for no reshuffle applies in Basic Mode too if that remains the intended scoring rule; Expert Mode only adds the Visit the Emperor action.
- 9x9 rules are intentionally incomplete for now, but all 9x9 manual-relevant rules should be collected here as tests continue.

Do not bring these as questions unless Pedro wants readability edits:

- Cards with tokens: already covered across placement/building/Retainer rules.
- Face-down / Trap identity: mostly covered; optional short summary sentence only.
- Protection reward placement: already implied by "play one Protection token" plus the Protection Tokens section; optional cross-reference only.

### 1) Unique Special Retainers

Clarification:

- In the initial game version, the "exclusive" Retainer cards are not unique new abilities.
- They are duplicate versions of existing Retainers.
- Examples:
  - Oda Nobunaga has a second Samurai.
  - Akechi Mitsuhide has a second Shinobi.
  - Toyotomi Hideyoshi has a second Tea Master / Chajin.
  - Tokugawa Ieyasu has a second Ashigaru.
- These cards have slightly more amber coloring and a star that distinguishes them.
- They are relevant for endgame special missions / Destiny Path.

Manual implication:

- The manual does not need a full new rules appendix for exclusive Retainers if their abilities are identical to the standard card type.
- It should include one short sentence explaining that starred exclusive Retainers follow the normal rules for their Retainer type unless a card says otherwise.
- Destiny Path text should refer to starred / exclusive Retainers if needed by player boards.

Suggested rulebook wording:

```text
Some decks include a starred Retainer. A starred Retainer uses the same rules and abilities as the matching standard Retainer, but may be referenced by that clan's Destiny Path.
```

### 2) Trap Model / Ronin Board Presence

Clarification:

- Pedro's trap model is currently the most updated V26 direction.
- However, Ronin probably should not be removed from the board when its Trap resolves.
- Need to review the exact Ronin Trap text in `RulesV26-Final.md`.

Current V26 text to review:

```text
[TRAP]: When a player flips this face up, you remove up to one Protection token from that player. Then, discard this card and play up to two Protection tokens.
```

Issue:

- `discard this card` likely conflicts with the desired Ronin behavior.
- Ronin should probably remain face-up on the board after Trap reveal.

To clarify with Pedro:

- Should Ronin Trap stay on the board after resolving?
- Should Shinobi still be discarded after resolving?
- Should owner self-reveal have separate behavior?

### 3) Daimyo Global Rules

Clarification:

- Add to Pedro discussion / rulebook review.

Needed rule points:

- Daimyo starts the player's Chain.
- Daimyo cannot be discarded.
- Daimyo cannot be flipped face-down.
- Daimyo cannot be stacked on unless a future rule explicitly says otherwise.
- Protection tokens on Daimyo need clear status:
  - are they reserve/build tokens only?
  - or do they protect the Daimyo?

Status:

- To clarify with Pedro and then add to `RulesV26-Final.md`.

### 4) Deck Exhaustion / Emperor Visit / Reshuffle Limit

Clarification:

- The deck may be reused only once.
- If the deck runs out again after that, the player does not draw and plays if they can.
- If nobody can draw anymore, the game ends and Imperial Summons begins.

Manual implication:

- V26 must clearly state:
  - first reshuffle can happen through Emperor Visit / reshuffle right;
  - after that reshuffle is used, no further reshuffle is available;
  - if a player must draw and cannot, they simply draw fewer/no cards;
  - if no player can draw anymore, trigger Imperial Summons / final sequence.

To clarify with Pedro:

- Does a forced first reshuffle count as using/losing the Emperor Visit bonus?
- Does "nobody can draw anymore" trigger Imperial Summons immediately or after the current turn/round?
- If no Capital exists, how is Shogun/order scoring handled?

### 5) Emperor Visit Scoring Reminder

Clarification:

- The +1 VP for not reshuffling is not only an Expert Mode score concept.
- Visit the Emperor is an Expert Mode action/exception, but the +1 VP for not reshuffling should still be assigned in Basic Mode if the player never reshuffled.

Manual issue:

- Current V26 text places `+1 VP if never used Emperor Visit` only under Expert Mode.
- Scoring section should include or reference the +1 VP for no reshuffle if this applies to Basic Mode too.

To clarify with Pedro:

- Is the +1 VP officially "unused Emperor Visit" or "no reshuffle used"?
- Does Basic Mode track reshuffle in the same way?

### 6) 9x9 / 5-6 Players Expansion

Clarification:

- The 9x9 section can remain incomplete for now and be filled gradually after tests.
- For 5-6 player games, each player may have up to 2 alliances, including mixed alliance configurations.
- Any 9x9-specific rule that will belong in the manual should be collected here until integrated.

Current 9x9 notes to preserve:

- 9x9 uses extra player boards, decks, and kits.
- 5-6 player games can support 2 alliances per player.
- Need future tests for:
  - 9x9 setup;
  - Disputed Spaces;
  - zone geometry;
  - card number range;
  - alliance limits and rewards.

### 7) 5x5 Duel Board / River Spaces / Board Icons

Clarification:

- River spaces are Disputed Spaces.
- Because they are Disputed Spaces, they do not accept Koku/Protection/building placement according to Disputed rules.
- The board itself shows scoring marks that award +1 or +2 VP at final scoring.
- The board also marks which spaces are Disputed Spaces.
- The bottom row will include marks to indicate no Koku collected.

Manual implication:

- The manual can rely partly on board icons, but must explain what the icons mean.
- Need a short "Board Icons" or "5x5 Duel Board" paragraph.

To clarify / add:

- Which exact river spaces give Koku, if any?
- Which spaces are no-Koku?
- Are +1/+2 VP spaces scored only if connected to Chain?
- Are top/bottom no-score rows still part of current V26?

### 8) Rebellion Multi-Resolution

Clarification:

- This was already raised in comments.
- Players often ask whether they can resolve another Rebellion after one card is removed and the board opens/reveals a new Rebellion.
- This is especially common when face-down cards are revealed or when three or more cards create multiple Rebellions.
- The solving sequence matters because choosing the wrong card may solve fewer Rebellions.

Manual implication:

- Need explicit rule text.

Suggested direction:

```text
You may resolve multiple Rebellions during your turn, one at a time.
After each removed card, check the board again.
If the removal reveals or leaves another Rebellion, you may resolve another one.
If one removed card resolves multiple Rebellions, count how many Rebellions were resolved before assigning the reward.
```

Open design point:

- Reward should be confirmed:
  - +1 Protection per resolved Rebellion; or
  - +1 Protection per Rebellion action; or
  - +1 Protection per discarded card.

V25 used +1 Protection per Error/Rebellion resolved.

### 9) Face-Down Cards / Traps / Chain / Control

Clarification:

- A face-down card counts for control and Chain.
- The current `RulesV26-Final.md` already states that a zone is controlled if all spaces are occupied by your cards, face up or down.
- The Chain definition says it includes all connected cards; this should be read as including face-down cards.
- Any face-down Trap is only a face-down card while hidden. It is a mask/bluff state, not a visible card type.
- No player may peek at a face-down card, not even its owner.
- It is possible and legal for the owner to reveal their own face-down card by mistake, believing it was another card.
- Any player can reveal a face-down card by paying the reveal cost, but not during the same turn that card was played.

Manual implication:

- This is mostly covered already.
- The only useful improvement would be one explicit sentence linking all the pieces:

```text
Face-down cards still belong to their owner and count for Chain and control, but they have no number, do not score as face-up cards, and cannot be peeked at by anyone, including their owner.
```

### 10) Receiving / Playing Protection Tokens

Clarification:

- If a rule gives you a Protection token, you play/place it immediately.
- A played Protection token may be placed on eligible face-up cards, including Retainers and Prefecture cards, or on your Daimyo if it has fewer than three Protection tokens.
- The placement can immediately trigger Building if the Building requirements are met.
- This is why Rebellion reward, Ronin reward, and Koku-paid Protection should all use the same `play one Protection token` rules.

Current V26 status:

- `RulesV26-Final.md` already says played Protection tokens are placed on one of your face-up cards on non-Disputed spaces with no tokens, or on your Daimyo if it has fewer than three Protection tokens.
- `RulesV26-Final.md` also says that right after playing a Protection token, you may build.

Manual implication:

- The rule is functionally present.
- If test readers miss it, add a small cross-reference:

```text
Whenever an effect tells you to play a Protection token, follow the same placement rules above, then immediately check whether you can or must build.
```

### 11) Token Terminology Risk

Clarification:

- Pedro intentionally uses `tokens` as a general category for placed pieces, including Protection and building pieces.
- When a rule specifically concerns Protection, he uses `Protection tokens`.
- This is acceptable as an editorial system.
- The check is whether every generic `token/tokens` instance is intentionally broad.

Terminology convention to preserve:

- `Tokens`: broad term for pieces on cards/spaces when the rule should apply to any placed token.
- `Koku tokens`: currency, not placed on board spaces/cards.
- `Protection tokens`: protection/build-progress tokens.
- `Market token`, `Castle token`, `Capital token`: building tokens.
- `Alliance markers`: functionally represented by Protection tokens, but they are not normal spendable Protection.

Token terminology audit in `RulesV26-Final.md`:

| Line(s) | Text / Context | Status | Notes |
|---|---|---|---|
| 18-22 | Components list: Koku, Protection, Market, Castle, Capital tokens | OK | Clear specific component names. |
| 32 | Setup: Daimyo starts with one Protection token | OK | Specific and clear. |
| 69, 149 | Pay K2 to play one Protection token | OK | Specific and clear. |
| 78 | Koku tokens paid/gained/capped at five | OK | Specific and clear. |
| 98 | Prefecture stack on own face-up Prefecture with no tokens | OK | Broad token use is intentional: any existing token blocks stacking. |
| 115 | Rebellion discard chosen card along with any tokens on it | CONFIRMED | Rebellion removes the discarded card and any tokens on it, including Market/Castle. Capital is protected separately because the card with Capital cannot be discarded. |
| 119-124 | Protection placement rules | OK | Specific where needed. `do not already have tokens` is intentionally broad: no stacking Protection on cards with buildings or other tokens. |
| 126 | Cards with tokens of any kind are usually safe; Disputed spaces cannot have tokens of any kind | CONFIRMED / ADD CLARITY | Any token on a card blocks additional tokens, covering/stacking, and attacks such as Ashigaru or Ronin replace unless a rule/card explicitly says otherwise. Disputed spaces cannot receive Protection, Market, Castle, or Capital. Koku are only currency on the player board, not board-space tokens. |
| 130 | Discard two/three Protection tokens to build Market/Castle | OK | Specific and clear. |
| 132 | Place Market/Castle token on face-up Prefecture with no tokens | OK | Broad token use is intentional: building cannot be placed on any already-tokened card. |
| 134 | Capital token; Capital card cannot be flipped/discarded | OK | Specific and clear. Prevents Rebellion text from accidentally destroying Capital card. |
| 138 | You can only have as many tokens of a kind as in your kit; relocate if supply empty | CONFIRMED / REWRITE | Market, Castles, and Protection can be moved/reused if all copies are already on the board. Capital is unique and currently immovable. Rewrite to exclude Capital. |
| 181 | Ashigaru discards cards with no token around it | CONFIRMED | Any token blocks Ashigaru. Castle is the strongest protection and can only be destroyed through strategic Rebellion. |
| 193 | Ronin PLACE chooses non-Ronin, non-Daimyo card with no tokens | OK | Broad token use intentionally blocks targeting protected/built cards. |
| 195 | Ronin TRAP removes up to one Protection token; then play up to two Protection tokens | PARTLY CONFIRMED / PENDING BOARD PRESENCE | Effect is clear: remove up to one Protection token from any player if you want/can, return it to the box/supply, then take/play two Protection tokens from the box/supply. No token stealing or conversion. If owner reveals their own Ronin, they may remove their own token and still gain two. Still confirm with Pedro whether Ronin stays on board or is discarded. |
| 199 | Samurai discards non-Daimyo card with no tokens, or removes one Protection token | NEEDS CARD ALIGNMENT | Current manual says Samurai removes Protection only, but Gianluca notes the card allows discarding Market too, not Castle. Manual/card text must be aligned. |
| 205 | Shinobi discards Retainer or face-down card along with any Protection token | OK | Market/Capital/Castle cannot be built on Retainers, so building-token ambiguity is avoided. Face-down cards normally cannot have building tokens. |
| 211 | Sohei places on Prefecture, Sohei, or face-down card with no tokens | OK | Broad token use intentionally blocks stacking on tokened cards. |
| 243 | Alliance uses Protection tokens as Alliance markers; cannot spend as normal Protection | REWRITE | Because Daimyo does not need Protection, these should not be called normal Protection tokens. Use Alliance markers / tokens instead. |
| 247 | Alliance ends if effect removes one Alliance marker | REWRITE | If one ally loses their Alliance marker, the alliance ends and player-board rewards resolve. The other ally keeps their marker and converts it into one of their own usable tokens unless a specific player-board effect says otherwise. |

Summary:

- Most terminology is coherent.
- No global rewrite is needed.
- The main edits to consider are line 138, line 199, Alliance marker wording, and the pending Ronin Trap.
- Rebellion line 115 is confirmed: if a Rebellion removes a card with a Market/Castle, that building token is removed too. Capital remains protected by its own rule.

Gianluca responses to the numbered audit:

1. Confirmed: Rebellion removes the card and any token on it, including Market/Castle. Capital excluded by Capital protection rule.
2. Confirmed: cards with tokens cannot receive other tokens, cannot be covered/stacked, and are protected from attacks such as Ashigaru/Ronin replace unless a rule explicitly says otherwise.
3. Confirmed: Disputed spaces cannot receive Protection, Market, Castle, or Capital. Koku are only player-board currency.
4. Confirmed with rewrite: Castles, Market, and Protection can be moved/reused if all pieces are already on the board. Capital is unique and immovable for now.
5. Confirmed: any token blocks Ashigaru. Castle is the strongest protection and is mainly destroyed through Rebellion.
6. Confirmed: any token blocks Ronin PLACE / replace.
7. Partly confirmed: Ronin Trap removes up to one Protection token from any player if desired/possible, then gains/plays two Protection tokens from the box/supply. This also applies if the owner reveals their own Ronin. Still pending: whether Ronin stays on board or is discarded.
8. Not confirmed: Samurai can discard Market, but not Castle. This is specified on the card and must be reflected in the manual.
9. Confirmed root resolution: Market/Capital/Castle cannot be built on Retainers, so Shinobi building-token ambiguity does not arise.
10. Confirmed: any token blocks Sohei.
11. Confirmed rewrite: Alliance markers are not Protection tokens. They are markers/tokens on Daimyo.
12. Rewrite: if one ally loses the alliance marker, the alliance ends and rewards resolve. The other ally keeps their marker and converts it into one of their own tokens unless player-board text says otherwise.
13. Not confirmed: rewards depend on player-board conditions, such as "if you break the alliance" or "if your alliance is broken".
14. Confirmed: alliance rewards are in Koku and respect the Koku cap.

### 12) Alliance Rewards

Clarification:

- Alliance rewards are intended to be in Koku, or at least that is the current design direction.
- This should be aligned with the player boards.

Manual implication:

- Keep this as a pending alignment item until Pedro and the player boards converge.
- If confirmed, the rules should say that Alliance rewards grant Koku and are still limited by the Koku cap.

### 13) To Discuss With Pedro

Clarification:

- Gianluca can discuss this point with Pedro.
- Keep it on the running list until resolved.

---

## 7) Change Log

### 2026-05-26

- Created `RulesV26-Final.md` from Pedro's Markdown copy.
- Corrected obvious export/comment artifacts only.
- Created this AI workspace.
- Added deep V25 -> V26 change map.
- Added Gianluca clarifications for Unique Retainers, Trap/Ronin, Daimyo rules, reshuffle limit, Emperor scoring, 9x9, 5x5 board icons, and Rebellion multi-resolution.
