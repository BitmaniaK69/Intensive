# Sengoku Guided Playtest Setups

**Rules version:** V26 draft rules  
**Card version:** V25 physical cards  
**Document purpose:** reusable playtest setup file  
**Primary player count:** 4 players  
**Supported fallback:** 3 players  
**Default board:** 6x6 board  
**Default mode:** guided fast scenario  
**Alliances:** disabled

This document defines pre-built playtest scenarios for running short Sengoku games using V25 physical cards while testing selected V26 rules.

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

---

## Scenario A - Initial Board

### Colour / clan mapping

The board uses one-letter colour codes to keep every cell at **max 2 characters**.

```text
B = Blue   = AM - Akechi Mitsuhide
R = Red    = ON - Oda Nobunaga
G = Green  = TH - Toyotomi Hideyoshi
Y = Yellow = TI - Tokugawa Ieyasu
```

### Two-character board notation

```text
.. = empty normal space
@@ = empty Disputed Space / Imperial-style centre marker
B● = Blue / AM Daimyo, not protected
b● = Blue / AM Daimyo, protected
B5 = Blue / AM face-up Prefecture 5, not protected
b5 = Blue / AM face-up Prefecture 5, protected
B? = Blue / AM face-down card
```

Protection is encoded by lowercase clan letter:

```text
B5 = unprotected Blue Prefecture 5
b5 = protected Blue Prefecture 5
B● = unprotected Blue Daimyo
b● = protected Blue Daimyo
```

Face-down cards do not show Protection in this scenario because face-down cards cannot receive Protection.

### Visual board after setup

This version deliberately gives each player one branch toward the outer row and one branch toward the centre. The centre is threatened but not fully occupied at setup.

```text
|  |1 |2 |3 |4 |5 |6 |
|--|--|--|--|--|--|--|
|A |..|b2|..|..|r4|..|
|B |B?|b●|..|..|r●|R?|
|--+--+--+--+--+--+--|
|C |..|B5|@@|@@|R1|..|
|D |..|G6|@@|@@|Y2|..|
|--+--+--+--+--+--+--|
|E |G?|g●|..|..|y●|Y?|
|F |..|g3|..|..|y5|..|
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
Each player starts with the non-star copy of their clan-special Retainer in hand.
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

## AM - Akechi Mitsuhide / Blue / B

Role: first player, centre pressure, trap/facedown tension.

Starting board:

```text
A2: b2  AM Prefecture 2 + 1 Protection
B1: B?  AM face-down card
B2: b●  AM Daimyo + 1 Protection
C2: B5  AM Prefecture 5
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

## ON - Oda Nobunaga / Red / R

Role: military pressure, direct expansion, Castle path.

Starting board:

```text
A5: r4  ON Prefecture 4 + 1 Protection
B5: r●  ON Daimyo + 1 Protection
B6: R?  ON face-down card
C5: R1  ON Prefecture 1
```

Starting Koku:

```text
K3
```

Starting hand:

```text
1. ON Prefecture 6
2. ON Prefecture 2
3. ON Samurai - non-star copy
```

First draw:

```text
ON Prefecture 5
```

Expected dilemma:

```text
ON can attack, protect, build toward Castle, or expand inward from the upper-right side.
ON should demonstrate whether Samurai pressure is clear and whether building is tempting enough.
```

---

## TH - Toyotomi Hideyoshi / Green / G

Role: economy, Market pressure, flexible card flow.

Starting board:

```text
D2: G6  TH Prefecture 6
E1: G?  TH face-down card
E2: g●  TH Daimyo + 1 Protection
F2: g3  TH Prefecture 3 + 1 Protection
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
TH starts with exactly two Protection tokens in chain.
This makes Market relevant after a card/Protection play, but TH can also aim toward Castle by adding a third Protection.
```

---

## TI - Tokugawa Ieyasu / Yellow / Y

Role: defensive control, Rebellion awareness, tactical punishment.

Starting board:

```text
D5: Y2  TI Prefecture 2
E5: y●  TI Daimyo + 1 Protection
E6: Y?  TI face-down card
F5: y5  TI Prefecture 5 + 1 Protection
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
B1: B? = AM Ronin Trap
B6: R? = ON Prefecture 5
E1: G? = TH Prefecture 4
E6: Y? = TI Shinobi Trap
```

Purpose:

```text
Two real Traps.
Two numbered face-down cards.
No initial Rebellion.
Enough uncertainty to make K3 flip decisions matter.
```

---

## Scenario A - Fast Setup Checklist

Before starting, check:

```text
[ ] Board positions match the visual map.
[ ] Each player has K3 available.
[ ] Each player has exactly 3 cards in hand.
[ ] Each player's hand includes the non-star copy of their clan-special Retainer.
[ ] Each star/special copy remains in the player's deck.
[ ] Each player has 2 Protection tokens already on board.
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
```

If none of these happen, the scenario is too passive.

---

# 3-Player Variant

Use AM, ON, and TI.

Remove TH from the game:

```text
Remove TH deck, kit, hand, first draw, and all TH board cards.
Remove:
D2: G6
E1: G?
E2: g●
F2: g3
```

3-player visual board after removing TH:

```text
|  |1 |2 |3 |4 |5 |6 |
|--|--|--|--|--|--|--|
|A |..|b2|..|..|r4|..|
|B |B?|b●|..|..|r●|R?|
|--+--+--+--+--+--+--|
|C |..|B5|@@|@@|R1|..|
|D |..|..|@@|@@|Y2|..|
|--+--+--+--+--+--+--|
|E |..|..|..|..|y●|Y?|
|F |..|..|..|..|y5|..|
```

Keep AM, ON, and TI as written for the first test.

3-player note:

```text
With TH removed, Market pressure is weaker.
Observe ON and TI carefully to see whether either player still considers Market.
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
B1: B? = AM Prefecture 3
B6: R? = ON Prefecture 5
E1: G? = TH Prefecture 4
E6: Y? = TI Prefecture 1
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
TH6 at D2
TH3 at F2
TI2 at D5
TI5 at F5
```

Duplicated visible numbers at setup:

```text
AM2 at A2 and TI2 at D5: not same row, column, or printed area.
AM5 at C2 and TI5 at F5: not same row, column, or printed area.
```

## Main V26 assumptions used here

- A Zone is any row, column, or printed area.
- A Rebellion exists when two face-up Prefecture cards with the same number are in the same Zone.
- Face-down cards have no number.
- Only the top card of a stack matters for effects, limitations, and scoring.
- Protection tokens can be placed only on valid face-up cards or Daimyo.
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
