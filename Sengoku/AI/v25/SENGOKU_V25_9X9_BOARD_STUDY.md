# Sengoku V25 - 9x9 Grand Campaign Board Study

This note studies a provisional 9x9 board for 5-6 players.
It is not locked rules text.

Notation:

- 🟡 = Imperial space
- 🟦 = legal Daimyo start candidate
- 🔴 = recommended Daimyo start already selected for the shown setup
- ⬜ = normal playable space
- rows and columns are split visually by 3x3 zones

## Design Risks

The 9x9 board must avoid two opposite problems:

- runaway leader: one player captures the center early and converts it into too much income/control;
- turtling/camping: players stay safely on the edge because the center is too costly or too dangerous to contest.

The opening layout should make every Daimyo feel close enough to the Imperial area to contest it, but not so close that first-player order decides the center.

## Recommended Imperial Shape

Use a 5-space cross, not a 3x3 block.

```text
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜

⬜⬜⬜ ⬜🟡⬜ ⬜⬜⬜
⬜⬜⬜ 🟡🟡🟡 ⬜⬜⬜
⬜⬜⬜ ⬜🟡⬜ ⬜⬜⬜

⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
```

Imperial coordinates:

```text
E4, D5, E5, F5, E6
```

Reasoning:

- 5 Imperial spaces scale up from the 6x6 board without creating a 9-space central scoring engine.
- The cross creates four approach lanes and one central prize.
- The shape encourages conflict around the center without making the entire middle 3x3 block special.
- The corners of the central 3x3 remain normal spaces, so players can build around or through the Imperial area instead of only occupying it.

## Zone Geometry

Use 9 normal 3x3 zones:

```text
A1-C3 | D1-F3 | G1-I3
A4-C6 | D4-F6 | G4-I6
A7-C9 | D7-F9 | G7-I9
```

The central 3x3 zone contains the 5 Imperial spaces.
For balance testing, Imperial spaces should still keep their normal restrictions:

- no face-down cards;
- no Protection tokens;
- no Markets, Castles, or Capitals;
- Imperial income only if controlled and connected to the Chain of Command.

## Empty Start-Candidate Layout

Before any Daimyo is placed, every non-central 3x3 zone should offer legal start candidates.
The central zone has no Daimyo start candidates.

This is the recommended symmetric empty layout.
The corner zones have one start candidate each.
The four cardinal zones have two start candidates each.
For setup generation, choose at most one Daimyo start from any non-central zone.

```text
⬜⬜⬜ 🟦⬜🟦 ⬜⬜⬜
⬜🟦⬜ ⬜⬜⬜ ⬜🟦⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜

🟦⬜⬜ ⬜🟡⬜ ⬜⬜🟦
⬜⬜⬜ 🟡🟡🟡 ⬜⬜⬜
🟦⬜⬜ ⬜🟡⬜ ⬜⬜🟦

⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜🟦⬜ ⬜⬜⬜ ⬜🟦⬜
⬜⬜⬜ 🟦⬜🟦 ⬜⬜⬜
```

Start candidates by zone:

```text
Northwest: B2
North: D1, F1
Northeast: H2
West: A4, A6
Center: no Daimyo start candidates
East: I4, I6
Southwest: B8
South: D9, F9
Southeast: H8
```

This pool has 12 start candidates.
If setup allows any 6 of the 12, it creates 924 raw position combinations.
That is too much and also allows invalid same-row or same-column starts.

If setup enforces at most one Daimyo per non-central zone, no shared row, and no shared column, it creates 8 raw valid position combinations.
These collapse to 3 geometric classes after whole-board rotations/reflections.
This is very compact, but may be too restrictive if we want more opening variety.

Audit note:

```text
Current symmetric 12-candidate layout: 8 raw valid combinations, 3 geometric classes.
Previous 16-candidate blue layout: 28 raw valid combinations, 9 geometric classes.
Expanded 20-candidate symmetric tests: 64 raw valid combinations, 12 geometric classes.
```

Conclusion: the low count is not a hash/counting collision; it comes from the candidate layout being too constrained once the required row, column, and zone restrictions are all applied.
If the 9x9 board should offer more opening variety than the 6x6 board, this 12-candidate layout should not be final.

## Recommended 6-Player Start Ring

Use 6 starting positions from the blue candidate pool.
The default should cover six different non-central zones.

Proposed default hex ring:

```text
⬜⬜⬜ ⬜⬜🔴 ⬜⬜⬜
⬜🔴⬜ ⬜⬜⬜ ⬜🟦⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜

🟦⬜⬜ ⬜🟡⬜ ⬜⬜🔴
⬜⬜⬜ 🟡🟡🟡 ⬜⬜⬜
🔴⬜⬜ ⬜🟡⬜ ⬜⬜🟦

⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜🟦⬜ ⬜⬜⬜ ⬜🔴⬜
⬜⬜⬜ 🔴⬜🟦 ⬜⬜⬜
```

Starting coordinates:

```text
B2, F1, I4, H8, D9, A6
```

Distances to the nearest Imperial space:

```text
B2 = 5
F1 = 4
I4 = 4
H8 = 5
D9 = 4
A6 = 4
```

This keeps every player close enough to contest the center, while preventing any player from starting on a distance-3 lane.
The unused blue candidates remain available for seeded/random Junbi or alternate setup templates.

## Alternative 6-Player Start Ring

If the default setup feels too axis-aligned, test this complementary ring:

```text
D1, H2, I6, F9, B8, A4
```

Distances to the nearest Imperial space:

```text
D1 = 4
H2 = 5
I6 = 4
F9 = 4
B8 = 5
A4 = 4
```

This variant uses the same distance profile as the default ring, but shifts which outer zones are active.

## Start Rules To Test

For 5-6 players, do not reuse the 6x6 constraint set unchanged.
The rule "no two Daimyo share a row, column, or zone" is too restrictive on a 9x9 edge-start board.

Recommended provisional constraints:

- every non-central 3x3 zone contains at least one start candidate;
- the central 3x3 zone has no Daimyo start candidates;
- no Daimyo starts at orthogonal distance 3 or less from the nearest Imperial space;
- for 6 players, choose six start candidates, with at most one Daimyo start from each non-central zone;
- no two Daimyo may share a row;
- no two Daimyo may share a column;
- for 5 players, remove one start from the 6-player ring and rotate the missing seat between games or seed setups.

## Balance Hypothesis

The cross should reduce runaway leader risk compared with a 3x3 Imperial block.
It gives fewer Imperial income spaces and leaves normal central spaces available for contesting, blocking, and building.

The distance-4/5 start ring should reduce camping because every player can reach central lanes without crossing the whole board.
The same ring also reduces first-player center rush because nobody begins directly on the fastest distance-3 approach.

## Open Test Questions

- Is 5 Imperial income too much on 9x9, or should only the center E5 score income while the four arms provide placement restrictions only?
- Should controlling the full central 3x3 zone count as normal zone income if Imperial spaces inside it are controlled by different players?
- Should 5-player setup use one neutral blocked start lane, or simply remove one Daimyo start from the 6-player ring?
- Should distance-3 starts be banned entirely, or kept for asymmetric scenarios?
- Are 3 geometric 6-player opening classes enough for the 9x9 board, or should the start-candidate layout be loosened to create more variety while preserving row/column legality?
