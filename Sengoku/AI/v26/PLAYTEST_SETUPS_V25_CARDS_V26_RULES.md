# Sengoku Guided Playtest Setups

**Rules version:** V26 draft rules  
**Card version:** V25 physical cards  
**Document purpose:** reusable playtest setup file  
**Primary player count:** 4 players  
**Supported fallback:** 3 players  
**Default board:** 6x6 board  
**Default mode:** guided fast scenario  
**Alliances:** disabled

This document defines pre-built playtest scenarios for running short Sengoku games using V25 cards while testing selected V26 rules. It is intended to be readable months later without needing the original conversation.

The goal is not to simulate a fully open game from turn 1. The goal is to start from a partially developed board state so that the table quickly reaches the interesting V26 decisions: Koku pressure, Rebellions, Traps, Protection, Market, Castle, and Capital timing.

---

## 1. What This Playtest Is Testing

### Main questions

1. Does the V26 turn structure feel faster and easier to teach?
2. Does the 3-card hand pressure create good choices?
3. Are Koku decisions interesting?
   - Spend Koku to play a second card?
   - Spend Koku to place Protection?
   - Spend Koku to flip a face-down card?
4. Do Rebellions create tension without slowing the game too much?
5. Do Traps matter enough when face-down cards are present from the start?
6. Is the Market a real alternative to rushing Castles?
7. Are Castles reachable quickly enough in a short game?
8. Does the first Capital/endgame pressure feel exciting or too sudden?
9. Does the centre/Disputed Spaces matter in a 4-player fast scenario?
10. Do V25 cards remain usable under the V26 rules framework?

### Secondary observations

- Which rules need repeated explanation?
- Which card abilities are confusing with V26 terminology?
- Whether players forget to check row/column/area Rebellions.
- Whether players understand that only the top card of a stack matters.
- Whether Protection/Market/Castle/Capital being token-like components is clear.

---

## 2. What This Playtest Is Not Testing

The following systems are intentionally excluded or reduced to keep the session fast and focused.

### Not testing

- Alliances.
- Expert Mode.
- Destiny Path scoring.
- Emperor Visit.
- Flexible Junbi edge setup.
- 5x5 Duel balance.
- 9x9 rules.
- Full open-game deck randomness.
- Long-term deck exhaustion balance.
- Full campaign pacing from an empty board.

### Partially testing

- Scoring, but only as a fast end-state check.
- Capital timing, but from an accelerated board state.
- Market value, but only through a short scenario.
- Rebellion resolution, but with seeded opportunities.

---

## 3. V26 Rules Assumptions Used In These Setups

Use the current V26 draft unless changed by a scenario-specific note.

### Hand and turn structure

- Each player normally has **3 cards in hand**.
- A player may play a card for free if they have **3 or more cards** in hand.
- A player may pay **K1** to play a card if they have **2 cards** in hand.
- At end of turn, the player gains Koku, discards down to 2 if needed, then draws up to 3 cards.

### Koku

- Each player has a maximum of **5 Koku**.
- Paid Koku are set aside.
- Gained Koku return from the set-aside area.
- Extra Koku beyond 5 are ignored.

### Standard action costs

- **K1** = play a card from hand when at 2 cards.
- **K2** = play 1 Protection token.
- **K3** = flip face up 1 face-down card, if it was not played this turn.

### Building

- Right after playing a card or Protection token, a player may build.
- **Market** = discard 2 Protection tokens from cards in chain.
- **Castle** = discard 3 Protection tokens from cards in chain.
- If a player has 3 Protection tokens specifically on Prefecture cards in chain, building a Castle is mandatory.
- Market/Castle must be placed on a face-up Prefecture card in chain, on a non-Disputed space, with no token already on it.
- Capital normally requires 3 Castles in chain, unless a scenario says otherwise.

### Rebellions

- A Rebellion exists when two face-up Prefecture cards with the same number are within the same Zone.
- A Zone means a row, a column, or a printed 3x2 area on the 6x6 board.
- Face-down cards have no number and do not cause Rebellions until flipped.

---

## 4. Board Reference

Use coordinates A-F horizontally and 1-6 vertically.

```text
      1   2   3   4   5   6
A   A1  A2  A3  A4  A5  A6
B   B1  B2  B3  B4  B5  B6
C   C1  C2  C3  C4  C5  C6
D   D1  D2  D3  D4  D5  D6
E   E1  E2  E3  E4  E5  E6
F   F1  F2  F3  F4  F5  F6
```

### Printed 3x2 areas on the 6x6 board

```text
Z1 = A1-C2
Z2 = A3-C4
Z3 = A5-C6
Z4 = D1-F2
Z5 = D3-F4
Z6 = D5-F6
```

### Disputed Spaces for this setup

```text
C3, C4, D3, D4
```

Disputed Spaces cannot receive tokens, face-down Prefecture cards, or stacked Prefecture cards. They can still become important for income and scoring if they are in a player's chain.

---

## 5. Session Structure Recommendation

For a 3-hour session with explanation and feedback:

```text
00:00-00:20  Explain V26 fast scenario and setup
00:20-00:55  Game 1
00:55-01:00  Micro-feedback and reset
01:00-01:35  Game 2 or Variant 1
01:35-01:40  Micro-feedback and reset
01:40-02:15  Game 3 or Variant 2
02:15-03:00  Final feedback, discussion, notes
```

Hard-stop each game after **5 rounds** or about **35 minutes**, whichever comes first. Finish the current round if needed.

---

# Scenario A - Four Fires Around Kyoto

## Scenario summary

**Players:** 4  
**Clans/Daimyo:** AM, ON, TH, TI  
**Starting player:** AM - Akechi Mitsuhide  
**Alliances:** disabled  
**Starting hand:** exactly 3 cards per player  
**First draw:** predefined  
**Initial Koku:** K3 per player  
**Initial Protection:** 2 Protection tokens already on board per player  
**Scenario length:** 5 rounds maximum  
**Capital rule:** use normal V26 unless testing a fast-Capital variant

## Scenario purpose

This setup creates four different roles:

- **AM** starts first and pressures the centre.
- **ON** has strong military pressure and a clean Castle path.
- **TH** is pushed toward the Market vs Castle decision.
- **TI** plays a defensive/control role and can punish Rebellions.

The board starts without any active Rebellion, but several cards and first draws create **latent Rebellion risks**. Players should be forced to check rows, columns, and printed areas before placing or flipping cards.

---

## Scenario A - Initial Board

### Board map

Use this compact board view after setup.

Legend:

```text
AM-D = AM Daimyo
AM2  = AM face-up Prefecture 2
AM?  = AM face-down card
[P]  = Protection token on that card
```

```text
      1        2        3        4        5        6
A   .        .        .        .        .        .
B   .        AM-D[P]  AM?      ON?      ON-D[P]  .
C   .        AM2[P]   AM5      ON1      ON4[P]   .
D   .        TH3[P]   TH6      TI2      TI5[P]   .
E   .        TH-D[P]  TH?      TI?      TI-D[P]  .
F   .        .        .        .        .        .
```

### Initial Rebellion check

At setup, there should be **no active Rebellion** among face-up Prefecture cards.

Face-up Prefecture cards on board:

```text
AM2 at C2
AM5 at C3
ON1 at C4
ON4 at C5
TH3 at D2
TH6 at D3
TI2 at D4
TI5 at D5
```

The duplicated numbers currently visible are:

- AM2 at C2 and TI2 at D4: not in the same row, column, or printed area.
- AM5 at C3 and TI5 at D5: not in the same row, column, or printed area.

---

## Scenario A - Player Packs

Each player pack should be prepared before the session.

Use real V25 cards, but label them here using V26 terminology.

---

## AM - Akechi Mitsuhide

### Role

First player, centre pressure, early face-down tension.

AM should feel tempted to:

- push into the centre,
- flip a suspicious face-down card,
- spend Koku to accelerate,
- prepare for Market/Castle by adding Protection,
- create or expose a Rebellion if careless.

### Starting board

```text
B2: AM Daimyo + 1 Protection
B3: AM face-down card
C2: AM Prefecture 2 + 1 Protection
C3: AM Prefecture 5
```

### Starting Koku

```text
K3
```

### Starting hand - 3 cards

```text
1. AM Prefecture 4
2. AM Samurai
3. AM Shinobi
```

### First draw

```text
AM Prefecture 1
```

### Seeded dilemma

AM can play aggressively, but the obvious central expansion may become dangerous later. AM also has access to Shinobi pressure and Samurai interaction, but playing a second card usually costs Koku.

### Notes for the facilitator

- If AM uses Koku to flip a face-down card early, observe whether the table understands the K3 cost.
- If AM plays Samurai early, observe whether players understand protection and unprotected targets.
- AM should not automatically be the strongest player; AM is meant to demonstrate tempo pressure.

---

## ON - Oda Nobunaga

### Role

Military pressure, direct expansion, Castle path.

ON should feel tempted to:

- attack or remove an exposed card,
- add Protection and build toward Castle,
- punish central overextension,
- choose between protecting territory or expanding.

### Starting board

```text
B4: ON face-down card
B5: ON Daimyo + 1 Protection
C4: ON Prefecture 1
C5: ON Prefecture 4 + 1 Protection
```

### Starting Koku

```text
K3
```

### Starting hand - 3 cards

```text
1. ON Prefecture 6
2. ON Ashigaru
3. ON Ronin
```

### First draw

```text
ON Prefecture 2
```

### Seeded dilemma

ON has aggressive tools, but must decide whether to spend Koku on a second card, Protection, or flipping a suspicious card. ON can become the first player to threaten a Castle if they protect the right card.

### Notes for the facilitator

- Watch whether Ashigaru feels too strong from this starting position.
- Watch whether ON players prefer attacking over building.
- If ON ignores building, the Market/Castle incentives may be too weak or unclear.

---

## TH - Toyotomi Hideyoshi

### Role

Economy and Market pressure.

TH should feel tempted to:

- build the Market early,
- delay the Castle race for better income,
- use utility cards to shape the next turn,
- benefit from central presence without directly starting a fight.

### Starting board

```text
D2: TH Prefecture 3 + 1 Protection
D3: TH Prefecture 6
E2: TH Daimyo + 1 Protection
E3: TH face-down card
```

### Starting Koku

```text
K3
```

### Starting hand - 3 cards

```text
1. TH Prefecture 1
2. TH Chajin
3. TH Sohei
```

### First draw

```text
TH Prefecture 5
```

### Seeded dilemma

TH starts with exactly two Protection tokens in chain. This makes the Market reachable if TH plays a card or Protection and builds immediately after. TH can also aim for a Castle by adding a third Protection instead.

### Notes for the facilitator

- Observe whether TH understands that Market costs 2 Protection tokens from cards in chain.
- Observe whether Market feels attractive compared with Castle preparation.
- If TH always chooses Castle over Market, consider testing a Market buff in a future variant.

---

## TI - Tokugawa Ieyasu

### Role

Defensive control, punishment, Rebellion awareness.

TI should feel tempted to:

- protect a stable position,
- flip a face-down card at the right time,
- resolve a Rebellion created by others,
- build patiently rather than overextend.

### Starting board

```text
D4: TI Prefecture 2
D5: TI Prefecture 5 + 1 Protection
E4: TI face-down card
E5: TI Daimyo + 1 Protection
```

### Starting Koku

```text
K3
```

### Starting hand - 3 cards

```text
1. TI Prefecture 3
2. TI Samurai
3. TI Ronin
```

### First draw

```text
TI Prefecture 6
```

### Seeded dilemma

TI can play safely or wait for others to create Rebellions. TI has enough defensive structure to remain relevant, but not enough momentum to ignore the centre.

### Notes for the facilitator

- Watch whether TI feels too passive.
- TI should have meaningful turns even when not attacking.
- If TI feels slow, replace one starting hand card with Shinobi or Chajin in Variant A2.

---

# Scenario A - Hidden Face-Down Cards

Use these cards as the initial face-down cards.

Important: players must not inspect their own face-down cards once the scenario starts. Prepare these before play, place them face down, and remind players that face-down cards have no number until flipped.

```text
AM face-down at B3: AM Ronin Trap or AM Prefecture 3
ON face-down at B4: ON Shinobi Trap or ON Prefecture 5
TH face-down at E3: TH Prefecture 4 or TH Ronin Trap
TI face-down at E4: TI Shinobi Trap or TI Prefecture 1
```

## Recommended first run

For the first version of Scenario A, use this exact set:

```text
AM B3: AM Ronin Trap
ON B4: ON Prefecture 5
TH E3: TH Prefecture 4
TI E4: TI Shinobi Trap
```

This creates:

- two real Traps,
- two numbered face-down cards,
- no initial Rebellion,
- enough uncertainty to make K3 flip decisions matter.

---

# Scenario A - Expected Early Events

The setup is successful if at least some of these happen by round 3:

```text
- One player spends K1 to play a second card.
- One player spends K2 to place Protection.
- One player spends K3 to flip a face-down card.
- One Market is built or seriously considered.
- One Castle is built or set up.
- One Rebellion is prevented or resolved.
- At least two players contest or threaten the Disputed Spaces.
```

If none of these happen, the scenario is too passive.

---

# Scenario A - Fast End Options

Use one of these, depending on what you want to test.

## Option 1 - Normal V26 Capital

Use the normal V26 rule:

```text
3 Castles in chain -> remove them, flip one Castle card face down, place Capital.
```

Use this if the playtest focuses on the early/mid game and not necessarily the Capital.

## Option 2 - Fast Capital Variant

For a 35-minute sprint only:

```text
2 Castles in chain -> remove them, flip one Castle card face down, place Capital.
```

Use this if you specifically want to test the Imperial Summons and final scoring.

Mark all feedback clearly as `Fast Capital Variant`, because it is not the normal V26 rule.

---

# Scenario A - 3-Player Variant

If only 3 players are available, use AM, ON, and TI.

## Remove TH

Remove the following from the board:

```text
D2: TH Prefecture 3 + Protection
D3: TH Prefecture 6
E2: TH Daimyo + Protection
E3: TH face-down card
```

Remove TH's deck, kit, starting hand, and first draw.

## Adjust TI starting position

To keep the lower-right side relevant while avoiding too much empty space, move TI slightly toward the centre:

```text
D4: TI Prefecture 2
D5: TI Prefecture 5 + 1 Protection
E4: TI face-down card
E5: TI Daimyo + 1 Protection
```

No change is required for TI in the first run. If TI feels isolated, use this alternative:

```text
D3: TI Prefecture 2
D4: TI Prefecture 5 + 1 Protection
E4: TI face-down card
E5: TI Daimyo + 1 Protection
```

Important: if using the alternative, re-check Rebellions before starting.

## 3-player objectives

With TH removed, the scenario tests less Market pressure. To compensate, give ON or TI a stronger Market temptation:

```text
ON starts with 2 Protection in chain and should be reminded that Market costs exactly 2.
```

Optional 3-player change:

```text
Replace ON first draw with ON Chajin.
```

This makes ON choose between military pressure and resource development.

---

# Scenario A - Minimal Variant A2

Use this if Scenario A feels too slow or too defensive.

Change only the following:

```text
AM first draw: AM Chajin instead of AM Prefecture 1
TH first draw: TH Prefecture 2 instead of TH Prefecture 5
TI starting hand: replace TI Ronin with TI Shinobi
```

Purpose:

- AM sees more card flow.
- TH gets a more dangerous Rebellion-related number.
- TI becomes more active and less passive.

Do not change the board.

---

# Scenario A - Minimal Variant A3

Use this if Market is ignored.

Change only the following rule for this variant:

```text
Market income is +2 Koku instead of +1 Koku.
```

Alternative, less aggressive Market test:

```text
The first player to build a Market immediately gains K1.
```

Do not test both Market buffs at the same time.

---

# Scenario A - Minimal Variant A4

Use this if Rebellions are not happening often enough.

Change only the hidden face-down cards:

```text
AM B3: AM Prefecture 3
ON B4: ON Prefecture 5
TH E3: TH Prefecture 4
TI E4: TI Prefecture 1
```

This removes the starting Traps and makes face-down cards more likely to become numbered Rebellion threats when flipped.

Use this only after testing the Trap version once.

---

# Feedback Sheet

After each game, record only quick answers.

```text
Scenario / Variant:
Players:
Duration:
Rounds completed:
Winner:
Capital built? Y/N
Market built? Y/N / By whom:
Castles built:
Face-down flips used:
Traps triggered:
Rebellions prevented:
Rebellions resolved:
Most confusing rule:
Best moment:
Koku pressure: Too low / Good / Too high
Market value: Weak / Good / Too strong / Not tested
Castle timing: Too slow / Good / Too fast
Centre pressure: Ignored / Good / Too crowded
Overall pace: Too slow / Good / Too fast
Fun: 1 / 2 / 3 / 4 / 5
One sentence from players:
```

---

# Future Scenario Slots

Use the sections below for future setup variants.

---

# Scenario B - To Be Defined

Purpose:

```text
TBD
```

Expected focus:

```text
TBD
```

Suggested direction:

- Same board as Scenario A.
- Same hands as Scenario A.
- Change only first draws and hidden cards.
- Use if we want a comparable test with minimal reset overhead.

---

# Scenario C - To Be Defined

Purpose:

```text
TBD
```

Expected focus:

```text
TBD
```

Suggested direction:

- More aggressive Rebellion setup.
- Fewer starting Protection tokens.
- More face-down numbered cards.
- Use if Scenario A is too safe.
