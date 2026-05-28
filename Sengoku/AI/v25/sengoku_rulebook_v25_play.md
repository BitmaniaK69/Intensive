# Sengoku — Rulebook v25 (Play Edition)
_Last updated: 2026-04-23_

This edition is **optimized for readability at the table**.  
All edge cases, Duels, and long-form explanations are in the official rules: **`AI/v25/RulesV25-Final.md`**.

---

## 1) Goal
1. **Build a Capital** connected to your **Chain of Command**.
2. The player who legally forms that Capital immediately triggers **Imperial Summons**.
3. Finish that current turn in full, then every player gets one final restricted turn, including the first Shogun.
4. **Highest score wins** (being Shogun helps, but does not guarantee victory).

> **Win trigger (endgame starts):** the first player who legally forms **1 connected Capital**.

---

## 2) What You Do on Your Turn
You always manage **two resources**:

- **Koku (K#)** = currency (stored on your player board, **cap 5**).
- **Protection tokens** = map resource (defense + building progress).

### Spend Koku vs Spend Protection (table helper)
| You want to… | Spend… | Cost |
|---|---:|---:|
| Reveal a legal face-down card | Koku | **K3** |
| Convert currency into protection | Koku → Protection | **K2 → 1 token** |
| Protect a card on the map | Protection | **1 token** |
| Build a Castle | Protection | **3 tokens → 1 Castle** |
| Build a Market | Protection | **2 tokens → 1 Market** |
| Progress to a Capital | Castles | **3 Castles → 1 Capital** |

---

## 3) Core concepts
### 3.1 Sudoku validity
Every **face-up Numbered card** must respect the Sudoku rule (row/column/zone uniqueness).  
If you create an illegal state, you created an **Error (Rebellion)**.

### 3.2 Chain of Command
Your **Chain of Command** is the orthogonally connected group (no diagonals) that includes your **Daimyō**.
- **Chain** means your **Chain of Command**.
- **Near your chain** means in a space orthogonally adjacent to your Chain of Command.
- **Adjacent** means a target space/card at distance 1, orthogonally or diagonally.
- Only **connected** cards/buildings score.
- Many actions/builds require being connected.

### 3.3 Control
A Zone/Line/Imperial Zone is considered yours if it is fully controlled by your clan:
- In a **stack**, only the **top** card counts for control.
- A **face-down top card** still counts as your clan for control, but has no revealed number.
- Face-down cards still do **not** score as cards.

### 3.4 Imperial Zones
**Imperial Zones** are the **4 marked central spaces** with the Emperor symbol.
- Each controlled Imperial Zone adds **+1 Koku** during Collect Resources, only if it is connected to your **Chain of Command**.
- Imperial Zones cannot receive Protection tokens and cannot host Buildings (Market/Castle/Capital).
- Face-down cards cannot be placed in Imperial Zones.

---

## 4) Setup (Standard)
1. Each player chooses a clan color and takes: deck (20 cards), player board, tokens, and buildings.
2. Remove the **Daimyō** card from your deck and keep it face-up beside your player board (not on the player board).
3. Shuffle the remaining cards and draw **3**.
4. If those 3 cards contain no Numbered card, reshuffle that hand into the deck and redraw 3 (repeat until at least one Numbered card).
5. This setup redraw is **not** Visit the Emperor and does not consume the Emperor marker.
6. Place starting Protection on the **Daimyō** card: default setup is **+P1** on each Daimyō.
7. During **Junbi**, place your **Daimyō** on the game board in a legal starting prefecture (corners are not valid on 6x6).
8. Determine first player; play clockwise.

---

## 5) Turn structure
### Beginning of Turn
- **Draw up to 3 cards** (if you already have 3, draw 0).
- **Expert Mode (Visit the Emperor):** after this refill and before your first played card, if your Emperor marker is unused, shuffle your deck, discard pile, and entire hand together, then mark the Emperor marker as used.
- Draw back up to **3** immediately after the reshuffle.

### Active Turn
1. **Play cards** down to **2 cards in hand**. You may play one additional last card by paying **1 Koku** (ending with 1 card).
2. **Convert Koku → Protection** (K2 → 1 token), any amount, as a **Turn Procedure** in your Active Turn.
3. **Place Protection tokens** on eligible cards immediately as they are gained.
4. **Build** (Market/Castles/Capital) if requirements are met.
5. **Reveal** (pay K3 to reveal any legal face-down card; you cannot reveal your own face-down card in the same turn you placed it).
6. **Fix Errors** (earn rewards).

### End of Turn
1. **Collect Koku** (see Player Board values; summary below).
2. Discard Koku above the **cap 5**.
3. Resolve end-of-turn effects that explicitly trigger here.
4. **Draw back up to 3**.
5. Pass the turn.
6. If your deck runs out:
   - Standard: reshuffle discard to form a new deck.
   - Expert (Emperor enabled): at first required-draw exhaustion, do the same reshuffle and mark Emperor Visit as lost if it was unused.
   - If this happens during beginning refill, you cannot declare proactive Visit the Emperor later in that same turn.

> **Collect Resources summary**: base income + bonuses from **Market**, **Zones**, **Lines**, and **Imperial Zones**.  
> **Zones and Lines both count** if you control both (they stack).
> **Quick formula**: +1 base, +1 if Market built, +1 per controlled Zone or Line, +1 per controlled Imperial Zone connected to your Chain of Command (apply all valid sources; use the Player Board cap for this counting step).
> In normal flow, end-of-turn refill usually restores hand to 3; beginning refill mainly covers off-turn hand loss.

---

## 6) Cards and Placement
### 6.1 Daimyō
- Placed on the game board during Junbi setup placement.
- Cannot be removed or played face-down.
- Can hold up to **3 reserve Protection tokens** (not Koku; not automatic protection).

### 6.2 Numbered cards (1–6)
You may:
- Place them anywhere legal (respecting Sudoku validity).
- **Stack** them on your own face-up Numbered cards if the resulting top face-up state is still valid.
- Use them as the main **base** for Protection/buildings.
- Place them **face-down** as placeholders (see Face-down rules).

### 6.3 Retainers
Each Retainer offers **two Order Actions (A1 / A2)**; when used you choose **one**.
Depending on icon/text, a Retainer is either:
- **Placed** on the map (with placement rules), or
- **Discarded** to resolve an effect.

Some Retainers can stack or cover cards if their text allows it.
- Retainer **Order Actions** are separate from turn procedures (Reveal, Convert Koku, Build, Error Fix).

> Full Retainer action list is in **`AI/v25/RulesV25-Final.md`**.

---

## 7) Face-down cards, Reveal, and traps
Face-down play exists to keep the map moving (chain extension, zone contests, bluff).

Rules:
- **Numbered** cards may be placed **face-down** as hidden placeholders.
- A face-down Numbered placeholder has **no active number** while hidden.
- While hidden, it does **not** create Sudoku duplicates until revealed.
- Some Retainers may be placed **face-down** as hidden **traps** (current set includes Shinobi and Ronin; expansions may add more).
- Face-down placement follows the normal placement rules and the printed Retainer text. A card cannot be placed on top of a face-down card unless an effect explicitly says otherwise.
- Face-down cards cannot be placed in Imperial Zones.
- **Face-down cards cannot receive Protection tokens.**
- A **Capital is always placed on a face-down base card**.
- While a Capital remains on top, its base card cannot be attacked, revealed, or destroyed by effects.

### Reveal (Bribery)
Pay **K3** to reveal any legal face-down card. You cannot reveal your own face-down card in the same turn you placed it.

- If it’s a normal card: flip it face-up and apply legality checks.
- If a revealed Numbered card creates a forbidden duplicate, an **Error** is created immediately.
- If it’s a trap: resolve its trap effect once, targeting the revealer first whenever the trap text allows it, then remove it from the map and discard it.
- Reveal can also fix/trigger Errors (see Errors).

---

## 8) Errors (Rebellions)
An **Error** is an illegal Sudoku state (typically a forbidden duplicate).

Timing:
- If an illegal placement is spotted during the acting player's turn before Collect Resources, anyone may call it.
- The acting player corrects it immediately by placing that card face-down in any legal face-down space of their choice, or discarding it if no legal face-down correction exists.
- This immediate correction gives no reward.
- On **your turn**, you may fix any detected Errors.

Fixing:
- The fixer chooses which offending card to remove (and removal order).
- If removing a card reveals another Error, the same fixer may continue fixing.

Rewards:
- The fixer gains **+1 Protection token per Error fixed**.
- If one removal resolves multiple Errors at once, gain **+1 token per Error resolved**.
- Each gained token is placed immediately on a legal eligible **face-up** map card.
- If no legal map placement exists, that token is lost and returned to supply.
- Removed cards also remove any attached protection/building on that layer.

---

## 9) Protection tokens, Market, Castles, Capital
### 9.1 Protection tokens
- Place 1 token on an eligible **face-up** card (max **one** piece per card: token **or** Castle **or** Market).
- Protected cards (**Protected / Unprotected**) cannot be removed unless protection is removed first, or an effect bypasses it.
- In stacks, protection applies to the **top** visible layer.
- A card with any current protection layer on its top active state is not a legal target for remove/replace-style effects unless a rule or card explicitly says otherwise.
- For example, Ronin can target only an unprotected top non-Ronin card; Ronin replaces that target and remains in that space.

### 9.2 Build a Market or Castle
Buildings are made by **progression**, not by paying Koku directly.
- **Castle:** remove **3 Protection tokens** from your Chain (**Chain / Chain of Command**) and place **1 Castle** on an eligible Numbered card in that Chain.
- **Market:** remove **2 Protection tokens** from your Chain (**Chain / Chain of Command**) and place **1 Market** on an eligible Numbered card in that Chain.
- Castle conversion is **mandatory only** if you have **3 Protection tokens on Numbered cards in your Chain** and a valid Numbered destination in that Chain exists.
- If the committed tokens include one or more tokens from Retainers and/or Daimyō reserve, the conversion is legal but **not mandatory**.
- Mandatory conversions resolve immediately when their condition is met.

Notes:
- Max **1 Market** per player.
- Max **3 Castles** per player.
- If a Castle conversion would create a 4th Castle, you may relocate one of your existing Castles to a legal Numbered destination in your Chain (**Chain / Chain of Command**).
- If no legal relocation is possible, that Castle conversion cannot resolve and the 3 tokens remain in place.
- If you have 3 connected Castles, Capital conversion is immediate and mandatory.

### 9.3 Form a Capital
Requirements:
- **3 Castles** in your Chain of Command.
- Continuous connectivity to your Daimyō.

Process:
- Remove the 3 Castles immediately.
- Choose a Numbered card space in your Chain (**Chain / Chain of Command**) as the Capital base:
  - If the base is face-up, turn it face-down.
  - If a face-down card already exists there, use it.
- Place the **Capital** on top.
- The Capital transition always resolves immediately when the third connected Castle is completed.

---

## 10) Shogun and endgame
If you legally form a **valid connected Capital**, you immediately trigger **Imperial Summons** and become the **first Shogun** for scoring.
- You then finish that current turn normally and in full.
- After that turn, every player takes one final **restricted** turn, starting with the next player after the first Shogun and ending with the first Shogun.
- In a restricted final turn, players cannot play or place cards.
- They may only spend Koku to **Reveal** face-down cards, or convert Koku into Protection tokens and use those tokens for legal build progression, including Castles and Capital if requirements are met.
- Restricted final turns suspend the normal hand-size gate and do not perform a normal End of Turn refill.
- Building a Capital during a restricted final turn does not create a new Shogun turn and does not restart Imperial Summons.
- If another player legally forms a connected Capital during Imperial Summons, they also count as a later Shogun for scoring.
- After all restricted final turns are completed, the game ends immediately and scoring begins.

All alliances (Expert Mode) end immediately when Imperial Summons begins.

---

## 11) Scoring (Standard)
Score connected elements only:

- **+1** each face-up card on the map (Numbered or Retainer).
- **+1** each fully controlled **Zone** or **Line**.
- **+1** each **Castle**.
- **+3** each **Capital**.
- **Shogun scoring** uses order of achievement during Imperial Summons: first Shogun = **+4**, second = **+3**, third = **+2**, all later Shoguns = **+1**.
- **+1** (Expert Mode) if you never used your Emperor reshuffle right.
- Automatic Emperor-right loss from required-draw deck exhaustion counts as "used" (no +1 bonus).

Rules:
- Face-down cards do **not** score the +1 card value.
- Face-down cards still count for Zone/Line control if they belong to your clan.
- Tie-break: highest remaining Koku on the player board wins; if still tied, the game is a shared victory.

---

## 12) What’s in `AI/v25/RulesV25-Final.md`
- Full Retainer actions and timing notes
- Expert Mode (Alliances, Visit the Emperor, Destiny Path)
- Duels (2 players)
- Glossary + edge cases

Expert-mode reminder:
- Allied players may not Reveal each other's face-down cards unless a card or rule explicitly allows it.

---

## 13) Key Differences vs v23 Play
- Terminology standardized: **Imperial Zones** (replacing older mixed wording).
- **Imperial Zones** are explicitly restricted: no Protection tokens and no Buildings.
- **Imperial Zones** also block face-down placement.
- End-of-turn flow now explicitly includes deck exhaustion handling (Standard reshuffle vs Expert Emperor flow).
- Reveal/trap wording is clarified for face-down cards and trap resolution.
- Shogun endgame now uses **immediate Capital trigger + restricted final turns** timing.
- Shogun scoring now scales by Imperial Summons order: **+4 / +3 / +2 / +1 / +1 / ...**.
- Scoring now states a clear tie-break (highest remaining Koku on Player Board, then shared victory).
- Collect Resources is summarized with a quick formula for table use.
- Hand-floor rule updated: play down to 2, then pay 1 Koku to play the last card.
- Koku storage cap reduced to 5.
- Capital scoring increased to +3.
- Error-fix tokens and other gained Protection must be placed immediately or are discarded if no legal placement exists.
- Build progression now distinguishes **Castle = 3 tokens** and **Market = 2 tokens**.
- Mandatory building conversion now applies only to 3 tokens on connected **Numbered** cards; Retainer/Daimyō-source tokens remain optional.
- Protected-target legality is clarified for remove/replace effects.
- Glossary terms are clarified for **Chain / Chain of Command**, **Near your chain**, **Adjacent**, and **Protected / Unprotected**.
- Duels tie-break now follows the same global tie-break rule (highest remaining Koku on Player Board).

---

## 14) Mode Definitions (Reference)
- 5x5 (2 Players, The Duel): use the current Duel setup sheet and Duel rules in `RulesV25-Final.md`.
- 9x9 (5-6 Players, The Grand Campaign): use the current Grand Campaign setup sheet and the standard rules unless a setup sheet states otherwise.

