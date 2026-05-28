# Sengoku V25 9x9 Junbi Opening Classes

This study uses the provisional 9x9 Grand Campaign start layout from [SENGOKU_V25_9X9_BOARD_STUDY.md](./SENGOKU_V25_9X9_BOARD_STUDY.md).

## Count summary

Counts ignore which clan/player occupies each Daimyo position.

| Level | Count | Meaning |
| --- | ---: | --- |
| Legal start candidates | 12 | Start cells on the 9x9 board. |
| Raw 6-player choices without constraints | 924 | Choose any 6 of 12 candidates. |
| Raw choices with one-per-zone cap | 248 | Choose 6 starts, maximum one from each non-central zone. |
| Raw valid position combinations | 8 | One-per-zone, no shared row, and no shared column. |
| Geometric classes | 3 | Valid combinations after whole-board rotations/reflections. |
| Tactical groups | 1 | Grouped by the two non-central zones left without a Daimyo. |

If player/Daimyo identity matters, multiply raw valid position combinations by `6! = 720`.

## Hashing rule

Each `Symmetry hash` is computed from the sorted coordinate list after reducing the board to its canonical form under full square symmetries; the 9x9 3x3 zone grid and Imperial cross are symmetry-preserving. This means mirrored/rotated versions that are the same opening class produce the same hash.

## Notation

- 🔴 = close starting Daimyo position, with at least one other Daimyo at orthogonal distance 3
- 🟠 = isolated starting Daimyo position, with no other Daimyo at orthogonal distance 3
- 🟦 = legal start candidate not used in this layout
- 🟡 = Imperial space
- ⬜ = normal playable space
- each row is split as `ABC DEF GHI`

Validity constraints used for the classes below:

- exactly 6 Daimyo start positions;
- at most one Daimyo in each non-central 3x3 zone;
- no two Daimyo share a row;
- no two Daimyo share a column.

For the current 9x9 start layout, close/isolated coloring uses a distance-3 threshold. Nearest-neighbor distances in the valid class set are 3, 5, 6, or 8, so this cleanly separates local pressure from isolation.

## Start layout used

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
East: I4, I6
Southwest: B8
South: D9, F9
Southeast: H8
```

## Tactical groups

| Tactical group | Canonical excluded-zone pattern | Classes |
| --- | --- | ---: |
| TG-01 Long diagonal gap (NE + SW) | NE + SW | 3 |

## Opening classes

### TG-01 Long diagonal gap (NE + SW)

#### 9X9-01 - A4, B2, D1, F9, H8, I6

Symmetry hash: `D2A5972E65EF8601`.

Tactical group: `TG-01 Long diagonal gap (NE + SW)`.
Excluded zones: Northeast, Southwest.
Raw position coverage: 2.

```text
⬜⬜⬜ 🔴⬜🟦 ⬜⬜⬜
⬜🔴⬜ ⬜⬜⬜ ⬜🟦⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
🔴⬜⬜ ⬜🟡⬜ ⬜⬜🟦
⬜⬜⬜ 🟡🟡🟡 ⬜⬜⬜
🟦⬜⬜ ⬜🟡⬜ ⬜⬜🔴
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜🟦⬜ ⬜⬜⬜ ⬜🔴⬜
⬜⬜⬜ 🟦⬜🔴 ⬜⬜⬜
```

#### 9X9-02 - A4, B2, D9, F1, H8, I6

Symmetry hash: `114F3ADF223EE45E`.

Tactical group: `TG-01 Long diagonal gap (NE + SW)`.
Excluded zones: Northeast, Southwest.
Raw position coverage: 4.

```text
⬜⬜⬜ 🟦⬜🟠 ⬜⬜⬜
⬜🔴⬜ ⬜⬜⬜ ⬜🟦⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
🔴⬜⬜ ⬜🟡⬜ ⬜⬜🟦
⬜⬜⬜ 🟡🟡🟡 ⬜⬜⬜
🟦⬜⬜ ⬜🟡⬜ ⬜⬜🔴
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜🟦⬜ ⬜⬜⬜ ⬜🔴⬜
⬜⬜⬜ 🟠⬜🟦 ⬜⬜⬜
```

#### 9X9-03 - A4, B8, D1, F9, H2, I6

Symmetry hash: `957C87B512AB2F29`.

Tactical group: `TG-01 Long diagonal gap (NE + SW)`.
Excluded zones: Northwest, Southeast.
Raw position coverage: 2.

```text
⬜⬜⬜ 🟠⬜🟦 ⬜⬜⬜
⬜🟦⬜ ⬜⬜⬜ ⬜🟠⬜
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
🟠⬜⬜ ⬜🟡⬜ ⬜⬜🟦
⬜⬜⬜ 🟡🟡🟡 ⬜⬜⬜
🟦⬜⬜ ⬜🟡⬜ ⬜⬜🟠
⬜⬜⬜ ⬜⬜⬜ ⬜⬜⬜
⬜🟠⬜ ⬜⬜⬜ ⬜🟦⬜
⬜⬜⬜ 🟦⬜🟠 ⬜⬜⬜
```
