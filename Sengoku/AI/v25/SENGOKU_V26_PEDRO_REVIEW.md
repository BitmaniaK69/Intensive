# Sengoku V26 - Pedro Manual Review

Source reviewed:

- `Sengoku_V26_Pedro_take.txt`, exported from Pedro's Google Doc on 2026-05-26.
- Baseline comparison: `RulesV25-Final.md`.

Review goals:

1. Check flow, clarity, and ambiguity.
2. Identify differences from V25.
3. Identify V25 rules that may be missing because of omission rather than intentional simplification.

---

## 1) General Assessment

Pedro's version is much more readable than the V25 source.

The structure is strong:

- components are brief;
- setup is fast;
- definitions are early;
- the gameplay loop is easy to follow;
- most rules are written in player-facing language;
- many edge-case-heavy V25 passages are successfully compressed.

However, the document is not just a manual rewrite. It changes several gameplay systems:

- turn structure;
- Rebellions / Errors;
- Koku handling;
- setup positions;
- Retainer effects;
- traps;
- Duel board treatment;
- Capital scoring;
- tie-break;
- Expert Mode reshuffle;
- Alliances.

Some of these changes are good simplifications. Others need explicit approval and testing before becoming V26.

---

## 2) Flow, Clarity, And Ambiguity

### Strong Improvements

- `Zone` as a unified rule term is elegant, because it includes row, column, and board areas.
- `Rebellion` is easier to theme than `Error`.
- The setup is much shorter and easier to teach.
- The turn loop is easy to understand: actions first, then income/cleanup/refill.
- The new Capital placement rule is cleaner: flip one of the cards that had a Castle.
- The component list reflects the current Koku cap better: 5 Koku per player.
- Removing long historical/design notes from the main flow improves readability.

### Clarity Issues

#### Duplicate title

The document starts with:

```text
Sengoku
Sengoku
```

Remove the duplicate.

#### Typo

`Daymio card` should be `Daimyo card`.

#### "Zone" may be too broad without a diagram

The definition says:

```text
Any row, column, or pre-determined area on the main board.
```

This is concise, but players may confuse:

- row zone;
- column zone;
- printed area zone;
- Disputed space;
- controlled zone for income/scoring.

Recommendation: keep the simplified term, but add a diagram immediately.

#### Control definition needs top-card language

Current:

```text
A zone is under your control if all of its spaces are occupied by your cards (face up or down).
```

Potential ambiguity:

- What if a space has a stack?
- Does a lower card count?
- Does a face-down top card count?

Suggested clarification:

```text
In a stack, only the top card counts for control. A face-down top card still counts as its owner's card.
```

#### Chain definition should say face-down cards count

The Chain definition is readable, but should explicitly confirm that face-down cards can be part of a Chain.

#### "Usually safe" is too vague

Current:

```text
Cards with tokens of any kind are usually safe from most Retainer card abilities.
```

This is not rules language. Use exact wording:

```text
Cards with tokens cannot be targeted by Retainer effects unless that effect explicitly allows it.
```

If there are exceptions, list them.

#### "Discard down to two cards" changes the hand rule

Pedro's wording:

```text
Gain Koku according to your income, discard down to two cards (if you still have more than that), and draw cards until you have three in hand.
```

This is clean, but it is different from V25's active hand gate. It means cards drawn during the turn can be kept until end-of-turn cleanup and then discarded. That may be fine, but it is a gameplay change.

#### Rebellion resolution needs repeat/sequence rule

Pedro already left a note asking this.

The rule should confirm:

- one resolution may solve multiple Rebellions;
- the active player may resolve multiple Rebellions in the same turn;
- the chosen removal order matters;
- if removing one card reveals another Rebellion, it can also be resolved.

#### Imperial Summons currently allows Rebellion resolution

Pedro's Imperial Summons allows:

```text
Resolve rebellions.
```

V25 restricted final turns did not clearly allow full Error/Rebellion resolution. This is a major gameplay difference and should be explicit.

#### Tie-break text is not suitable for final manual

Current:

```text
In the rare case no tied player has a Capital, their factions battle to exhaustion, and whoever got 2nd place wins!
```

This is funny, but not usable as final rules text. Replace with a real rule, such as shared victory.

---

## 3) Major Differences From V25

### Player Count

V25 supported 2 players through Duels, 3-4 standard, and 5-6 Grand Campaign.

Pedro's main title says:

```text
2–4 players
```

5-6 players are moved to expansion.

This is fine if intentional.

### Components

Pedro uses:

- 5 Koku per player;
- 6 Protection tokens;
- Market, Castle, Capital as tokens;
- no Emperor Visit marker.

Differences:

- V25 had Emperor Visit markers as components.
- V25 separated building pieces from Protection tokens more explicitly.
- Pedro calls buildings `tokens`, which simplifies components but may blur the difference between Protection tokens and building tokens.

### Setup

Pedro's setup uses printed Daimyo icons on the board.

V25 had a wider Junbi setup with multiple legal starting edge positions on the 6x6 board.

This is a major board/setup change.

Pedro's footnote diagram shows only four Daimyo icons on 6x6, which is not the same as V25's broader starting coordinate list.

### Turn Structure

V25:

- Beginning refill to 3.
- Active Turn.
- Collect Resources.
- End refill to 3.
- Hand gate: play down to 2, or pay K1 to play down to 1.

Pedro:

- No separate beginning refill in the main turn.
- Any number of actions.
- Play from hand for free if you have 3+ cards.
- Pay K1 to play a card if you have 2 cards.
- At end: gain Koku, discard down to 2, draw to 3.

This is cleaner but changes how extra cards behave.

### Koku System

Pedro treats 5 Koku as available/used tokens:

- pay by setting aside;
- gain by taking them back;
- surplus ignored.

This is compatible with the K5 cap and is production-friendly.

But it is different from V25's storage language.

### Income

Pedro:

- base +1;
- +1 per Disputed space in your chain;
- +1 per controlled zone in your chain;
- +1 if Market is in your chain.

Differences:

- `Line` no longer exists separately because rows/columns are now zones.
- Disputed spaces give income if in chain, not through control language.
- Two-player board has special Disputed/no-Koku treatment.

### Card Terms

Pedro uses:

- `Prefecture cards` instead of `Numbered cards`;
- `Rebellion` instead of `Error`;
- `Disputed Spaces` instead of `Imperial Zones`;
- `tokens` broadly for Protection/Market/Castle/Capital.

These are major terminology changes, mostly cleaner, but they require all cards/playerboards to match.

### Face-Down Rules

Pedro keeps:

- face-down cards have no number;
- no one may peek;
- no face-down on Disputed spaces.

Potentially missing:

- whether face-down Retainers follow the same control/Chain rules;
- whether a player may reveal their own face-down card next turn;
- whether a card played this turn cannot be revealed by any player or only its owner.

### Rebellions / Errors

Pedro creates a better distinction:

- prevent a just-played Rebellion before turn end;
- resolve existing/uncovered/flipped Rebellions during your turn.

This is a good simplification, but it needs exact repeat/sequence language.

### Protection

Pedro:

- Protection can go on face-up own cards on non-Disputed spaces with no tokens;
- Protection can go on Daimyo up to 3;
- tokens block most Retainer abilities;
- Disputed spaces cannot have tokens.

Important difference:

- V25 said gained Protection must be placed immediately if legal, otherwise discarded.
- Pedro says surplus ignored, but should specify what happens if a reward Protection cannot be legally placed.

### Building

Pedro:

- build right after playing a card or Protection token;
- Market = 2 Protection from cards in chain;
- Castle = 3 Protection from cards in chain;
- mandatory Castle if 3 Protection are specifically on Prefecture cards in chain;
- Capital = remove 3 Castles, flip one of those cards face-down, place Capital.

Good simplification:

- Capital placement is much cleaner than V25.

Potential issue:

- `Right after playing a card or Protection token` may be too narrow. V25 allowed build procedures during the active turn whenever requirements were met.

Major issue:

```text
If you build something you no longer have in your supply, take one from those you already have on the main board.
```

This general relocation rule may unintentionally allow relocating Market, Castle, or Capital. V25 only had specific handling for Castle limit. This needs review.

### Capital And Scoring

Pedro:

- first Capital triggers game end;
- Capital card cannot be flipped/discarded while Capital remains;
- Capital scores 4 VP;
- first/second/third/later Capital scores 4/3/2/1 VP.

V25:

- Capital scored +3;
- Shogun scoring was 4/3/2/1;
- no extra +4 Capital value.

Pedro's scoring makes Capital much more valuable.

Example: first Capital is worth 8 VP total before counting the card/position implications.

This must be tested.

### Imperial Summons

Pedro's version is very readable:

- first Capital player finishes current turn;
- then one limited turn per player;
- no cards drawn or played;
- actions are Reveal, Protection, Rebellions.

Differences from V25:

- Rebellions are allowed.
- Protection is paid directly by Koku rather than phrased as Convert Koku.
- No end refill.

### Retainers

Pedro rewrites several Retainers.

#### Ashigaru

V25:

- place near chain or cover own-clan unprotected Numbered;
- kill up to 2 adjacent unprotected Numbered or face-down cards.

Pedro:

- place on empty adjacent-to-chain space or on one of your Prefecture cards;
- discard up to two Prefecture or face-down cards with no token around Ashigaru.

This is close but not identical.

#### Samurai

V25:

- place near chain or cover own clan card;
- kill 1 unprotected adjacent card or remove 1 Token or 1 Market.
- A2 cancels declared Retainer action and discards that card; cannot block traps.

Pedro:

- place empty adjacent-to-chain or on own face-up Prefecture;
- discard up to one non-Daimyo card with no tokens around Samurai, or remove one Protection token from that card;
- A2 cancels a face-up Retainer card just played, then draw one.

Differences:

- Market removal is gone.
- Cancel timing/effect changed.
- Draw one after cancel is new.
- It may not cancel trap effects.

#### Shinobi

V25:

- A1 removes 1 Retainer and any Token on it, or 1 face-down.
- A2 spy hand/discard 2/draw +1; trap affects revealer.

Pedro:

- A1 discards up to one Retainer or face-down card, along with any Protection token it has.
- A2 is only `[TRAP]`: when flipped, look at revealer's hand, discard up to two, discard Shinobi, draw one.

This is a major change.

It does not match the latest design discussion where Shinobi self-reveal would draw one and discard Shinobi, and opponent reveal would let Shinobi owner choose up to 2 cards.

#### Ronin

V25:

- A1 replaces unprotected top non-Ronin, returns target, then discard/return rest of stack.
- A2 steals up to 2 Tokens from cards of other clans; trap from revealer first, max 1 per clan, rest from supply.

Pedro:

- A1 choose a space with non-Ronin, non-Daimyo card with no tokens, discard up to one card stacked there and return all others, then place Ronin.
- A2 trap removes up to one Protection token from the revealer, then discards Ronin and plays up to two Protection tokens.

This differs from both V25 and the latest design direction.

Latest design discussion was closer to:

- Ronin trap steals up to 2 Protection tokens from the revealer's cards anywhere on the board;
- if not enough can be stolen, take remaining Protection from your supply;
- Ronin stays face-up on the board;
- self-reveal: no effect, Ronin stays face-up.

#### Sohei

Pedro's Sohei is close but simplified.

Potential issue:

- `Place on top any Prefecture, Sohei, or face-down card with no tokens` should clarify ownership: any clan or own only?

### Expert Mode

#### Emperor Visit

Pedro removes Emperor Visit tokens and uses deck/discard placement around the player board.

This is elegant but changes handling:

- once per game, shuffle discard into deck;
- may discard hand and draw 3;
- if never done, +1 VP;
- cannot shuffle discard in any other way, even if deck runs out.

This needs clarification:

- What happens if a player runs out of cards after already using Emperor Visit?
- Do they simply fail to draw?
- Does forced reshuffle consume the right, as V25 did?

Pedro's footnote says this invalidates the Emperor bonus too, but the main text does not state that clearly.

#### Alliances

Pedro:

- allies place Protection tokens on each other's Daimyo;
- these only represent Alliance;
- allies cannot flip each other's face-down cards or target each other's cards with Retainer effects;
- up to two alliances at a time;
- alliances end during Imperial Summons;
- if an effect removes one Alliance token, remove both.

Differences:

- V25/playerboards often used one pact at a time.
- The latest Koku-based alliance rewards are not integrated.
- Breaking/reward timing may differ.
- Third-party removal needs more clarity.

---

## 4) Possible Missing Rules Or Omissions

These are not necessarily wrong. They are items present in V25 or later discussion that do not appear clearly in Pedro's current text.

### Unique Special Retainers

Components say each deck has 7 Retainers including one exclusive card.

But the Retainer section only lists:

- Ashigaru;
- Chajin;
- Ronin;
- Samurai;
- Shinobi;
- Sohei.

Missing:

- Unique Special Retainers by clan.

### Latest Trap Direction

The latest design discussion after V25 is not integrated.

Pedro's current trap rules still use:

- Shinobi trap discards itself;
- Ronin trap discards itself;
- Ronin trap removes only up to one Protection token.

This does not match the more recent direction being discussed.

### Daimyo Immunities

The text does not clearly state globally:

- Daimyo cannot be removed;
- Daimyo cannot be flipped face-down;
- Daimyo cannot be stacked on;
- Daimyo starts the Chain.

Some Retainer effects exclude Daimyo, but a global rule would help.

### Capital Limit And Relocation

The broad token relocation rule may unintentionally cover Capital.

Need explicit:

- max 1 Capital;
- what happens if a player would build another Capital;
- whether Capital can ever move.

### Market Limit

Pedro implies limits through kit contents, but because he allows taking tokens from board when supply is empty, Market relocation may become possible.

Need explicit if intended.

### Castle Limit

V25 had specific 4th Castle handling.

Pedro's broad token rule replaces it, but may be too broad.

### Rebellion Resolution Chain

Needs explicit multi-error/multi-resolution rules.

Pedro's note already identifies this.

### Face-Down Retainer Rules

Need explicit:

- only `[TRAP]` Retainers may be played face-down;
- while face-down they count for owner/control/Chain;
- they have no Retainer type/effect until flipped;
- they cannot receive tokens.

### Owner Revealing Own Trap

Pedro's text says:

```text
When a player flips this face up...
```

But it does not define owner reveal separately.

Latest design discussion wanted self-reveal behavior to be explicit.

### Endgame Expert Scoring

Pedro's scoring section does not include:

- +1 VP for unused Emperor Visit;
- Destiny Path VP.

These are in Expert Mode and footnotes, but should be in scoring or cross-referenced.

### Alliances Rewards In Koku

The latest playerboard direction converted alliance rewards to Koku.

Pedro leaves alliance effects entirely to playerboards.

That is acceptable if playerboards are final, but the manual should say:

```text
Alliance rewards and penalties are paid as printed on the player board.
```

If Koku is final, state it.

### One Pact / Two Alliances

Earlier playerboard text often said:

```text
One pact at a time.
No renewal with the same Daimyo.
```

Pedro says up to two alliances.

This needs a design decision.

### 9x9 / 5-6 Player Rules

The 5-6 player expansion section is very thin.

Missing or postponed:

- 9x9 card numbers 1-9;
- 9x9 zone geometry;
- 9x9 setup positions;
- 9x9 Disputed spaces;
- 5-6 alliance limits;
- 5-6 component counts.

Pedro notes this in footnote `[k]`.

### 5x5 Duel Board

Pedro's text integrates 2-player into the main rules rather than a full Duel mode.

Potential missing:

- bridge/river special scoring;
- marked +1/+2 spaces;
- top/bottom row no-score icon explanation;
- no-Koku icons on river spaces;
- whether the full middle row is Disputed or only the center bridge space grants something.

### Retainer Targeting Around / Adjacent

Ashigaru and Samurai still use orthogonal + diagonal adjacency.

If the design is considering row/column/zone targeting, it is not integrated.

### Ronin A1 Owner/Target Intent

Pedro's Ronin footnote asks:

```text
Wasn't it an opponent card?
```

This remains unresolved in the document.

---

## 5) Highest-Priority Decisions Before V26

These should be resolved before editing the final manual.

1. Is Pedro's turn structure replacing V25's Beginning / Active / Collect / End flow?
2. Are printed starting Daimyo icons replacing Junbi's wider legal-start system?
3. Are `Line` and `Zone` officially merged into the single term `zone`?
4. Are buildings officially called tokens in final components/rules?
5. Is Capital scoring now 4 VP, in addition to first/second/third Capital VP?
6. Is Koku tie-breaker replaced by first Capital?
7. Are Rebellions allowed during Imperial Summons?
8. Is Emperor Visit represented by deck/discard position instead of a token?
9. Are alliances max 2 for all Expert Mode games, or only 5-6 player games?
10. What is the final Trap model for Shinobi and Ronin?
11. What is the final Ronin A1 resolution?
12. Are Unique Special Retainers included in this manual or deferred to cards/playerboards?

---

## 6) Recommendation

Use Pedro's document as the base for V26 manual structure. It is much easier to read.

But do not treat it as only an editorial rewrite. It should be promoted to V26 only after the major gameplay changes above are accepted or corrected.

Recommended workflow:

1. Mark each V25-to-V26 gameplay change as `Accepted`, `Test`, or `Reject`.
2. Update Pedro's document with the accepted design decisions.
3. Add missing rules that were omitted only because V25 was too long.
4. Keep the V26 manual short, but add precise rule sentences where ambiguity would create table disputes.

