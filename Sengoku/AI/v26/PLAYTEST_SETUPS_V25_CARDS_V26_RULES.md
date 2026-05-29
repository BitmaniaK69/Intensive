# Sengoku Guided Playtest Setups

**Rules version:** V26 draft rules  
**Card version:** V25 physical cards  
**Document purpose:** reusable playtest setup file  
**Primary player count:** 4 players  
**Supported fallback:** 3 players  
**Default board:** 6x6 board  
**Default mode:** guided fast scenario  
**Alliances:** disabled

This document defines pre-built playtest scenarios for running short Sengoku games using V25 cards while testing selected V26 rules.

The document is organised for quick table use first. Detailed notes and design rationale are moved after the playable setup.

---

# QUICK USE - Read This First

## What we are doing

Run a short, strongly pre-set Sengoku scenario using V25 physical cards and selected V26 rules.

The setup starts from a partially developed board so players quickly face:

- 3-card hand pressure.
- Koku spending choices.
- Rebellion risk.
- Trap uncertainty.
- Protection placement.
- Market vs Castle decisions.
- Centre / Disputed Space pressure.
- Protected Retainers already on the board.
- Stacked cards already on the board.

## What we are not testing

Do not use:

- Alliances.
- Expert Mode.
- Destiny Path.
- Emperor Visit.
- 5x5 Duel rules.
- 9x9 rules.
- Fully random opening setup.

## Core V26 rules to remind players

```text
Hand size: normally 3 cards.
Play 1 card for free if you have 3+ cards in hand.
Pay K1 to play a card if you have 2 cards in hand.
Pay K2 to play 1 Protection token.
Pay K3 to flip 1 face-down card, if it was not played this turn.
End turn: gain Koku, discard down to 2 if needed, draw to 3.
Market: discard 2 Protection tokens from cards in chain.
Castle: discard 3 Protection tokens from cards in chain.
Only the top card of a stack matters until it is removed.
```

## Table timing

```text
Target: 35-40 minutes per game.
Hard stop: 5 rounds, or finish the current round when time is called.
```

---

# Scenario A - Four Fires Around Kyoto

## Scenario summary

```text
Players: 4
Clans/Daimyo: AM, ON, TH, TI
Starting player: AM - Akechi Mitsuhide
Alliances: OFF
Starting Koku: K3 per player
Starting hand: exactly 3 cards per player
First draw: predefined
Initial Protection: 2 Protection tokens already on board per player
Scenario length: 5 rounds maximum
Capital rule: normal V26, unless using Fast Capital Variant
```

## Main test goals

Use this scenario to observe:

1. Do players feel the pressure of only having 3 cards?
2. Do they spend Koku to play a second card, or save it for Protection/reveal?
3. Do they notice possible Rebellions before playing or flipping cards?
4. Do Traps make face-down cards interesting?
5. Does anyone seriously consider Market instead of Castle?
6. Does the centre become contested?
7. Are V25 cards still understandable under V26 terminology?
8. Is it clear that Retainers can be on the board and can be protected?
9. Is it clear that only the top card of a stack matters?

---

## Scenario A - Initial Board

### Colour mapping

```text
AM = Blue   🔵 / 🟦
ON = Red    🔴 / 🟥
TH = Green  🟢 / 🟩
TI = Yellow 🟡 / 🟨
```

### Board notation

The token order is:

```text
TYPE + COLOUR + PROTECTION
```

Examples:

```text
⬛   = empty normal space
⬜   = empty Disputed Space / Imperial-style space if needed
D🔵  = AM Daimyo, unprotected
D🔵* = AM Daimyo, protected
5🟦  = AM face-up Prefecture 5, unprotected
5🟦* = AM face-up Prefecture 5, protected
?🟦  = AM face-down card, always unprotected
S🟥* = ON Samurai, protected
M🟩  = TH Sohei / Warrior Monk, unprotected, top card of a stack
```

Same pattern for the other colours:

```text
D🔴  / D🔴* / 5🟥  / 5🟥* / ?🟥
D🟢  / D🟢* / 5🟩  / 5🟩* / ?🟩
D🟡  / D🟡* / 5🟨  / 5🟨* / ?🟨
```

Face-down cards are always unprotected, so they use `?` and do not need a Protection marker.

### Visual board after setup

This version gives each player one branch toward the outer row and one branch toward the centre. ON starts with a protected Samurai already on the board. TH starts with a Sohei / Warrior Monk stacked on top of a Prefecture card, reducing his occupied spaces while keeping the same number of physical cards.

```text
|   | 1  | 2  | 3 | 4  | 5  | 6  |
|---|----|----|---|----|----|----|
| A | ⬛ |2🟦*| ⬛| ⬛ |4🟥*| ⬛ |
| B |?🟦 |D🔵*| ⬛|S🟥*|D🔴*|?🟥 |
|---|----|----|---|----|----|----|
| C | ⬛ |5🟦 | ⬛| ⬛ |1🟥 | ⬛ |
| D | ⬛ |M🟩 | ⬛| ⬛ |2🟨 | ⬛ |
|---|----|----|---|----|----|----|
| E | ⬛ |D🟢*| ⬛| ⬛ |D🟡*|?🟨 |
| F | ⬛ |6🟩*| ⬛| ⬛ |5🟨*| ⬛ |
```

Disputed Spaces:

```text
C3, C4, D3, D4
```

At setup there should be **no active Rebellion** among face-up Prefecture cards.

---

## Scenario A - Player Packs

Prepare one pack per player before the session.

Important Retainer rule for this scenario:

```text
Most players start with the non-star copy of their clan-special Retainer in hand.
ON is the exception: his non-star Samurai starts protected on the board.
The star/special copy remains shuffled in that player's deck.
Confirm the clan-special Retainer assignment against the physical V25 cards before play.
```

Current assumed clan-special mapping:

```text
ON - Oda Nobunaga: Samurai
AM - Akechi Mitsuhide: Shinobi
TH - Toyotomi Hideyoshi: Tea Master / Chajin
TI - Tokugawa Ieyasu: Ashigaru
```

This mapping is currently marked as **TO CONFIRM AGAINST PHYSICAL CARDS**.

---

## AM - Akechi Mitsuhide / Blue

Role: first player, centre pressure, trap/facedown tension.

Starting board:

```text
A2: 2🟦*  AM Prefecture 2 + 1 Protection
B1: ?🟦   AM face-down card
B2: D🔵*  AM Daimyo + 1 Protection
C2: 5🟦   AM Prefecture 5
```

Starting Koku:

```text
K3
```

Starting hand:

```text
1. AM Prefecture 4
2. AM Prefecture 1
3. AM Shinobi - non-star copy
```

First draw:

```text
AM Prefecture 2
```

Expected dilemma:

```text
AM can expand inward, consolidate the upper-left area, use Shinobi, or spend Koku to accelerate.
AM should be tempted to play a second card, but doing so competes with Protection/reveal spending.
```

---

## ON - Oda Nobunaga / Red

Role: visible military pressure, protected Retainer, Castle path.

Starting board:

```text
A5: 4🟥*  ON Prefecture 4 + 1 Protection
B4: S🟥*  ON Samurai + 1 Protection
B5: D🔴*  ON Daimyo + 1 Protection
B6: ?🟥   ON face-down card
C5: 1🟥   ON Prefecture 1
```

Starting Koku:

```text
K3
```

Starting hand:

```text
1. ON Prefecture 2
2. ON Prefecture 6
3. ON Sohei / Warrior Monk
```

First draw:

```text
ON Prefecture 5
```

Expected dilemma:

```text
ON already has protected military pressure on the board.
Instead of simply playing Samurai on turn 1, ON must decide whether to expand, build, protect further, recover/stack with Sohei, or spend Koku for tempo.
```

Facilitator note:

```text
ON intentionally starts with 5 cards on the board because the protected Samurai is part of the scenario demonstration.
This is deliberate asymmetry, not a normal game setup rule.
```

---

## TH - Toyotomi Hideyoshi / Green

Role: economy, Market pressure, compact chain, stacking demonstration.

Starting board:

```text
D2: M🟩   TH Sohei / Warrior Monk, unprotected, stacked on top of TH Prefecture 3
E2: D🟢*  TH Daimyo + 1 Protection
F2: 6🟩*  TH Prefecture 6 + 1 Protection
```

Stack detail:

```text
D2 stack:
Top: TH Sohei / Warrior Monk, unprotected
Bottom: TH Prefecture 3
Only the top card matters until it is removed.
```

Starting Koku:

```text
K3
```

Starting hand:

```text
1. TH Prefecture 1
2. TH Prefecture 5
3. TH Tea Master / Chajin - non-star copy
```

First draw:

```text
TH Prefecture 4
```

Expected dilemma:

```text
TH has the same number of physical cards as the others, but occupies fewer spaces because two cards are stacked.
TH has two Protection tokens in chain, one on the Daimyo and one on Prefecture 6.
This makes Market possible after development, but TH has less board spread than the others.
```

---

## TI - Tokugawa Ieyasu / Yellow

Role: defensive control, Rebellion awareness, tactical punishment.

Starting board:

```text
D5: 2🟨   TI Prefecture 2
E5: D🟡*  TI Daimyo + 1 Protection
E6: ?🟨   TI face-down card
F5: 5🟨*  TI Prefecture 5 + 1 Protection
```

Starting Koku:

```text
K3
```

Starting hand:

```text
1. TI Prefecture 3
2. TI Prefecture 6
3. TI Ashigaru - non-star copy
```

First draw:

```text
TI Prefecture 1
```

Expected dilemma:

```text
TI can play safely, punish exposed cards, or wait for others to create Rebellions.
TI should feel active while choosing whether to secure the lower-right area or push inward.
```

---

## Scenario A - Hidden Face-Down Cards

Players must not inspect their own face-down cards once the scenario begins.

Recommended first run:

```text
B1: ?🟦 = AM Ronin Trap
B6: ?🟥 = ON Prefecture 5
E6: ?🟨 = TI Shinobi Trap
```

Purpose:

```text
Two real Traps.
One numbered face-down card.
No initial Rebellion.
Enough uncertainty to make K3 flip decisions matter.
TH has no face-down card in this version because his fourth physical card is the Prefecture under the Sohei stack.
```

---

## Scenario A - Fast Setup Checklist

Before starting, check:

```text
[ ] Board positions match the visual map.
[ ] Each player has K3 available.
[ ] Each player has exactly 3 cards in hand.
[ ] AM, TH, and TI hands include their non-star clan-special Retainer.
[ ] ON non-star Samurai is protected on B4.
[ ] Each star/special copy remains in the player's deck.
[ ] AM, TH, and TI each have 4 physical cards on the board.
[ ] ON has 5 physical cards on the board by scenario design.
[ ] TH D2 is a stack: Sohei on top, Prefecture 3 underneath.
[ ] Hidden cards are placed face down and not inspected.
[ ] First draw cards are placed on top of each player deck.
[ ] No active Rebellion exists at setup.
[ ] Alliances are disabled.
```

---

## Scenario A - Success Criteria

The scenario is doing its job if by round 3 at least some of these happen:

```text
[ ] A player pays K1 to play a second card.
[ ] A player pays K2 to place Protection.
[ ] A player pays K3 to flip a face-down card.
[ ] A Trap is triggered or seriously feared.
[ ] A Market is built or strongly considered.
[ ] A Castle is built or nearly built.
[ ] A Rebellion is prevented or resolved.
[ ] At least two players contest or threaten Disputed Spaces.
[ ] Players understand that ON's Samurai is protected.
[ ] Players understand that TH's D2 stack only counts the top card.
```

If none of these happen, the scenario is too passive.

---

# 3-Player Variant

Use AM, ON, and TI.

Remove TH from the game:

```text
Remove TH deck, kit, hand, first draw, and all TH board cards.
Remove:
D2: M🟩 stack, including TH Sohei / Warrior Monk and TH Prefecture 3 underneath
E2: D🟢*
F2: 6🟩*
```

3-player visual board after removing TH:

```text
|   | 1  | 2  | 3 | 4  | 5  | 6  |
|---|----|----|---|----|----|----|
| A | ⬛ |2🟦*| ⬛| ⬛ |4🟥*| ⬛ |
| B |?🟦 |D🔵*| ⬛|S🟥*|D🔴*|?🟥 |
|---|----|----|---|----|----|----|
| C | ⬛ |5🟦 | ⬛| ⬛ |1🟥 | ⬛ |
| D | ⬛ | ⬛ | ⬛| ⬛ |2🟨 | ⬛ |
|---|----|----|---|----|----|----|
| E | ⬛ | ⬛ | ⬛| ⬛ |D🟡*|?🟨 |
| F | ⬛ | ⬛ | ⬛| ⬛ |5🟨*| ⬛ |
```

Keep AM, ON, and TI as written for the first test.

3-player note:

```text
With TH removed, Market pressure is weaker and the stacking example is removed.
If stacking must be tested in a 3-player game, move the Sohei stack concept to ON or TI in a later variant.
```

Optional 3-player tweak:

```text
ON first draw: ON Chajin / Tea Master instead of ON Prefecture 5.
```

Use this only if you want ON to face a stronger build/economy choice.

---

# Quick Variants

Use only one variant at a time.

## Variant A2 - More Activity

Use if the scenario feels too slow or too defensive.

```text
AM first draw: AM Chajin / Tea Master instead of AM Prefecture 2.
TI starting hand: replace TI Prefecture 6 with TI Shinobi.
```

## Variant A3 - Market Test

Use if Market is ignored.

Option 1:

```text
Market income is +2 Koku instead of +1 Koku.
```

Option 2:

```text
The first player to build a Market immediately gains K1.
```

Do not use both at the same time.

## Variant A4 - More Rebellion Pressure

Use if Rebellions are not happening often enough.

Replace hidden cards with:

```text
B1: ?🟦 = AM Prefecture 3
B6: ?🟥 = ON Prefecture 5
E6: ?🟨 = TI Prefecture 1
```

This removes the initial Traps and makes face-down cards more likely to become numbered Rebellion threats when flipped.

## Variant A5 - Fast Capital

Use only if the session specifically needs to test Imperial Summons and final scoring.

```text
2 Castles in chain -> remove them, flip one Castle card face down, place Capital.
```

Mark all feedback from this variant as `Fast Capital Variant`, because it is not the normal V26 rule.

---

# Quick Feedback Sheet

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
Protected Retainer clarity: Unclear / Good / Very clear
Stacking clarity: Unclear / Good / Very clear / Not tested
Overall pace: Too slow / Good / Too fast
Fun: 1 / 2 / 3 / 4 / 5
One sentence from players:
```

---

# Reference Notes

## Board coordinates

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

Printed 3x2 areas on the 6x6 board:

```text
Z1 = A1-C2
Z2 = A3-C4
Z3 = A5-C6
Z4 = D1-F2
Z5 = D3-F4
Z6 = D5-F6
```

## Initial Rebellion check

Face-up Prefecture cards on board:

```text
AM2 at A2
AM5 at C2
ON4 at A5
ON1 at C5
TH3 at D2 under TH Sohei / Warrior Monk, currently not relevant while covered
TH6 at F2
TI2 at D5
TI5 at F5
```

Visible top face-up Prefecture cards at setup:

```text
AM2 at A2
AM5 at C2
ON4 at A5
ON1 at C5
TH6 at F2
TI2 at D5
TI5 at F5
```

Duplicated visible numbers at setup:

```text
AM2 at A2 and TI2 at D5: not same row, column, or printed area.
AM5 at C2 and TI5 at F5: not same row, column, or printed area.
```

TH3 is under a Sohei stack and is not currently relevant for Rebellion checking.

## Main V26 assumptions used here

- A Zone is any row, column, or printed area.
- A Rebellion exists when two face-up Prefecture cards with the same number are in the same Zone.
- Face-down cards have no number.
- Only the top card of a stack matters for effects, limitations, and scoring.
- Protection tokens can be placed only on valid face-up cards or Daimyo.
- Retainers can be protected if they are valid face-up cards and the current rules allow Protection on that card.
- Disputed Spaces cannot receive tokens, face-down Prefecture cards, or stacked Prefecture cards.

---

# Future Scenario Slots

## Scenario B - To Be Defined

Purpose:

```text
TBD
```

Suggested direction:

```text
Same board as Scenario A.
Same hands as Scenario A.
Change only first draws and hidden cards.
Use if we want a comparable test with minimal reset overhead.
```

## Scenario C - To Be Defined

Purpose:

```text
TBD
```

Suggested direction:

```text
More aggressive Rebellion setup.
Fewer starting Protection tokens.
More face-down numbered cards.
Use if Scenario A is too safe.
```
