# Sengoku V25 6x6 Junbi Opening Classes

Corrected study of 4-player Junbi start-position classes for the current 6x6 board.

Important correction: only symmetries that preserve the fixed 3x2 zone layout are merged. These are vertical reflection, horizontal reflection, and 180-degree rotation. 90-degree rotations and diagonal reflections are not valid reductions because they turn the 3x2 zones into a different orientation.

## Count summary

Counts ignore which clan/player occupies each Daimyo position.

| Level | Count | Meaning |
| --- | ---: | --- |
| Legal start cells | 16 | Edge cells excluding corners. |
| Raw valid position combinations | 80 | Four Daimyo positions satisfying no shared row, column, or 3x2 zone. |
| Raw valid player-assigned setups | 1920 | `80 x 4!`, if four player/Daimyo seats are distinct. |
| Geometric classes under zone-preserving symmetries | 23 | Valid combinations after vertical/horizontal/180 reductions. |
| H-label tactical classes | 9 | Classes after collapsing positions by the H1-H4 start-band labels. |
| Strategic families | 5 | Based on how many starts are close to the Imperial Zone. |

Raw-combination coverage by geometric class:

```text
01=4, 02=4, 03=4, 04=4, 05=4, 06=2, 07=4, 08=4, 09=2, 10=4, 11=4, 12=4, 13=4, 14=4, 15=4, 16=4, 17=4, 18=2, 19=4, 20=4, 21=2, 22=2, 23=2
```

## Hashing rule

Each `Symmetry hash` is computed from the sorted coordinate list after reducing the board to its canonical form under zone-preserving symmetries only: vertical mirror, horizontal mirror, and 180-degree rotation. This hash identifies the exact legal opening class.

Each `H-label hash` is computed from the sorted H1-H4 label signature. The signature tokens are always written in ascending label order, preserving repeated labels, for example `H1+H2+H3+H4`, never `H1+H3+H4+H2`. This is useful for tactical grouping by start bands, but it is not guaranteed unique: the 23 legal board classes collapse to 9 H-label hashes, with 6 shared hashes.

## Single-cell position labels

For a more readable start-cell map, the legal starts can be labelled by mirrored left/right pairs while also treating top and bottom bands as equivalent:

```text
⬛H1H2 H2H1⬛
H3⬛⬛ ⬛⬛H3
H4⬛🟡 🟡⬛H4
H4⬛🟡 🟡⬛H4
H3⬛⬛ ⬛⬛H3
⬛H1H2 H2H1⬛
```

Cell groups:

```text
H1 = B1, E1, B6, E6
H2 = C1, D1, C6, D6
H3 = A2, F2, A5, F5
H4 = A3, F3, A4, F4
```

These labels are useful for discussing position bands, mirrored left/right pairs, and top/bottom tactical equivalence.
They are not unique board hashes.
Across the 23 legal board classes, H-only signatures collapse to 9 signatures, so different openings can still share the same H-label multiset.

## H-label tactical classes

If `H1...H4` are used as the tactical equivalence hash, the 23 geometric classes collapse into these 9 groups:

| H-label signature | H-label hash | Board classes |
| --- | --- | --- |
| H1+H1+H3+H3 | `5E2692C94F3AD0D5` | 6X6-15 |
| H1+H1+H3+H4 | `57B7AD5EC70439F5` | 6X6-13, 6X6-14 |
| H1+H1+H4+H4 | `06208342E57D2BBB` | 6X6-10, 6X6-11 |
| H1+H2+H3+H3 | `643B2A6606E6D8C6` | 6X6-12 |
| H1+H2+H3+H4 | `78C4263F070F5B86` | 6X6-01, 6X6-02, 6X6-04, 6X6-05, 6X6-06, 6X6-07, 6X6-08, 6X6-09 |
| H1+H2+H4+H4 | `67693B5F3D559E7A` | 6X6-18, 6X6-19, 6X6-20, 6X6-21 |
| H2+H2+H3+H3 | `024CC13A5A29D961` | 6X6-03 |
| H2+H2+H3+H4 | `41E166BA5024D886` | 6X6-16, 6X6-17 |
| H2+H2+H4+H4 | `2B2216057D36C5F2` | 6X6-22, 6X6-23 |

## First-Daimyo anchored view

Because the first Daimyo can be placed anywhere and then normalized by symmetry into the upper-left fundamental area, the first-Daimyo representative can be one of `B1`, `C1`, `A2`, or `A3`.

With the first Daimyo anchored this way, there are 80 exact coordinate solutions for the remaining setup. These collapse to 9 tactical H-label signatures.

| Fixed first Daimyo representative | H-label | Exact coordinate solutions | Distinct H-label signatures |
| --- | --- | ---: | ---: |
| B1 | H1 | 20 | 6 |
| C1 | H2 | 20 | 6 |
| A2 | H3 | 16 | 6 |
| A3 | H4 | 24 | 6 |
| Total | - | 80 | 9 |

Possible H-label signatures by first-Daimyo representative:

| Fixed first Daimyo | Possible signatures |
| --- | --- |
| B1 / H1 | `H1+H1+H3+H3`, `H1+H1+H3+H4`, `H1+H1+H4+H4`, `H1+H2+H3+H3`, `H1+H2+H3+H4`, `H1+H2+H4+H4` |
| C1 / H2 | `H1+H2+H3+H3`, `H1+H2+H3+H4`, `H1+H2+H4+H4`, `H2+H2+H3+H3`, `H2+H2+H3+H4`, `H2+H2+H4+H4` |
| A2 / H3 | `H1+H1+H3+H3`, `H1+H1+H3+H4`, `H1+H2+H3+H3`, `H1+H2+H3+H4`, `H2+H2+H3+H3`, `H2+H2+H3+H4` |
| A3 / H4 | `H1+H1+H3+H4`, `H1+H1+H4+H4`, `H1+H2+H3+H4`, `H1+H2+H4+H4`, `H2+H2+H3+H4`, `H2+H2+H4+H4` |

## Notation

- 🔴 = close Daimyo start, with at least one other Daimyo at orthogonal distance 3 or less
- 🟠 = isolated Daimyo start, with no other Daimyo at orthogonal distance 3 or less
- 🟡 = Emperor / Imperial Zone
- ⬜ = legal Junbi start position not used in this layout
- ⬛ = normal non-start cell
- each row is split as `ABC DEF`

## Validity constraints

- legal Daimyo starts are edge cells excluding corners;
- no two Daimyo share a row;
- no two Daimyo share a column;
- no two Daimyo share a fixed 3x2 zone;
- only zone-preserving board symmetries are merged.

## Strategic families

Close-to-Imperial starts are C1, D1, A3, F3, A4, F4, C6, and D6.

| Family | Pattern | Classes |
| --- | --- | ---: |
| F3 Balanced Gate | 2 close starts | 11 |
| F4 Wide Spear | 1 close start | 3 |
| F5 Outer Ring | 0 close starts | 1 |
| F2 Inner Net | 3 close starts | 6 |
| F1 Central Clamp | 4 close starts | 2 |

## Opening classes

### F3 Balanced Gate

#### 6X6-01 - A2, B6, D1, F3

Symmetry hash: `96DB6C74A7C7B2C0`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

#### 6X6-02 - A2, B6, D1, F4

Symmetry hash: `41CAB856582728BA`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

#### 6X6-03 - A2, C6, D1, F5

Symmetry hash: `76323435D9276074`.
H-label signature: `H2+H2+H3+H3`.
H-label hash: `024CC13A5A29D961`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 2.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛🟠
⬛⬜🟠 ⬜⬜⬛
```

#### 6X6-04 - A2, C6, E1, F3

Symmetry hash: `223208DC976B2015`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ ⬜🔴⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛🔴
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛⬜🟠 ⬜⬜⬛
```

#### 6X6-05 - A2, C6, E1, F4

Symmetry hash: `0DA45B9231F06097`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ ⬜🟠⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜🟠 ⬜⬜⬛
```

#### 6X6-06 - A2, D1, E6, F3

Symmetry hash: `DCF8F441C3EE0BD8`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ ⬜🟠⬛
```

#### 6X6-07 - A2, D1, E6, F4

Symmetry hash: `2806B7CABE74E2F3`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🔴
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ ⬜🔴⬛
```

#### 6X6-08 - A2, D6, E1, F3

Symmetry hash: `4D5DFCBDDA8BB50B`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ ⬜🔴⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛🔴
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ 🟠⬜⬛
```

#### 6X6-09 - A2, D6, E1, F4

Symmetry hash: `6DDF3FF74D096DA6`.
H-label signature: `H1+H2+H3+H4`.
H-label hash: `78C4263F070F5B86`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 4.

```text
⬛⬜⬜ ⬜🟠⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ 🟠⬜⬛
```

#### 6X6-10 - A3, B1, E6, F4

Symmetry hash: `D3545D8BFB50C5A4`.
H-label signature: `H1+H1+H4+H4`.
H-label hash: `06208342E57D2BBB`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 2.

```text
⬛🔴⬜ ⬜⬜⬛
⬜⬛⬛ ⬛⬛⬜
🔴⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🔴
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ ⬜🔴⬛
```

#### 6X6-11 - A3, B6, E1, F4

Symmetry hash: `305BD8839BF76AE2`.
H-label signature: `H1+H1+H4+H4`.
H-label hash: `06208342E57D2BBB`.

Strategic family: `F3 Balanced Gate`.
Raw position coverage: 2.

```text
⬛⬜⬜ ⬜🟠⬛
⬜⬛⬛ ⬛⬛⬜
🟠⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

### F4 Wide Spear

#### 6X6-12 - A2, B6, D1, F5

Symmetry hash: `91CE1EDA75C97AC5`.
H-label signature: `H1+H2+H3+H3`.
H-label hash: `643B2A6606E6D8C6`.

Strategic family: `F4 Wide Spear`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛🟠
⬛🟠⬜ ⬜⬜⬛
```

#### 6X6-13 - A2, B6, E1, F3

Symmetry hash: `F74F3B9D7417E167`.
H-label signature: `H1+H1+H3+H4`.
H-label hash: `57B7AD5EC70439F5`.

Strategic family: `F4 Wide Spear`.
Raw position coverage: 4.

```text
⬛⬜⬜ ⬜🔴⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛🔴
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

#### 6X6-14 - A2, B6, E1, F4

Symmetry hash: `D25DD46E7F13697F`.
H-label signature: `H1+H1+H3+H4`.
H-label hash: `57B7AD5EC70439F5`.

Strategic family: `F4 Wide Spear`.
Raw position coverage: 4.

```text
⬛⬜⬜ ⬜🟠⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

### F5 Outer Ring

#### 6X6-15 - A2, B6, E1, F5

Symmetry hash: `D608B86CB10E3FFF`.
H-label signature: `H1+H1+H3+H3`.
H-label hash: `5E2692C94F3AD0D5`.

Strategic family: `F5 Outer Ring`.
Raw position coverage: 2.

```text
⬛⬜⬜ ⬜🟠⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛🟠
⬛🟠⬜ ⬜⬜⬛
```

### F2 Inner Net

#### 6X6-16 - A2, C6, D1, F3

Symmetry hash: `7991749142FE4589`.
H-label signature: `H2+H2+H3+H4`.
H-label hash: `41E166BA5024D886`.

Strategic family: `F2 Inner Net`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛⬜🟠 ⬜⬜⬛
```

#### 6X6-17 - A2, C6, D1, F4

Symmetry hash: `3AB88B385BDF30CB`.
H-label signature: `H2+H2+H3+H4`.
H-label hash: `41E166BA5024D886`.

Strategic family: `F2 Inner Net`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
🟠⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜🟠 ⬜⬜⬛
```

#### 6X6-18 - A3, B1, C6, F4

Symmetry hash: `96CB684CDFD3FBB0`.
H-label signature: `H1+H2+H4+H4`.
H-label hash: `67693B5F3D559E7A`.

Strategic family: `F2 Inner Net`.
Raw position coverage: 4.

```text
⬛🔴⬜ ⬜⬜⬛
⬜⬛⬛ ⬛⬛⬜
🔴⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜🟠 ⬜⬜⬛
```

#### 6X6-19 - A3, B1, D6, F4

Symmetry hash: `2EB470EEA0E8EC10`.
H-label signature: `H1+H2+H4+H4`.
H-label hash: `67693B5F3D559E7A`.

Strategic family: `F2 Inner Net`.
Raw position coverage: 4.

```text
⬛🔴⬜ ⬜⬜⬛
⬜⬛⬛ ⬛⬛⬜
🔴⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ 🟠⬜⬛
```

#### 6X6-20 - A3, B6, C1, F4

Symmetry hash: `AE89EEB5D00D24A7`.
H-label signature: `H1+H2+H4+H4`.
H-label hash: `67693B5F3D559E7A`.

Strategic family: `F2 Inner Net`.
Raw position coverage: 4.

```text
⬛⬜🟠 ⬜⬜⬛
⬜⬛⬛ ⬛⬛⬜
🟠⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

#### 6X6-21 - A3, B6, D1, F4

Symmetry hash: `FDB9BB15F61AB253`.
H-label signature: `H1+H2+H4+H4`.
H-label hash: `67693B5F3D559E7A`.

Strategic family: `F2 Inner Net`.
Raw position coverage: 4.

```text
⬛⬜⬜ 🟠⬜⬛
⬜⬛⬛ ⬛⬛⬜
🟠⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛🟠⬜ ⬜⬜⬛
```

### F1 Central Clamp

#### 6X6-22 - A3, C1, D6, F4

Symmetry hash: `DC6E640B37D069B6`.
H-label signature: `H2+H2+H4+H4`.
H-label hash: `2B2216057D36C5F2`.

Strategic family: `F1 Central Clamp`.
Raw position coverage: 2.

```text
⬛⬜🟠 ⬜⬜⬛
⬜⬛⬛ ⬛⬛⬜
🟠⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ 🟠⬜⬛
```

#### 6X6-23 - A3, C6, D1, F4

Symmetry hash: `AB932381B4F88548`.
H-label signature: `H2+H2+H4+H4`.
H-label hash: `2B2216057D36C5F2`.

Strategic family: `F1 Central Clamp`.
Raw position coverage: 2.

```text
⬛⬜⬜ 🟠⬜⬛
⬜⬛⬛ ⬛⬛⬜
🟠⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛🟠
⬜⬛⬛ ⬛⬛⬜
⬛⬜🟠 ⬜⬜⬛
```






⬛⬜⬜ ⬜⬜⬛
⬜⬛⬛ ⬛⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛🟡 🟡⬛⬜
⬜⬛⬛ ⬛⬛⬜
⬛⬜⬜ ⬜⬜⬛ 