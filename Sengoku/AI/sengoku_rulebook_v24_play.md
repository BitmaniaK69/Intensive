# Sengoku — Rulebook v24.1 (Play Edition)
_Last updated: 2026-02-22 - V24.1_

This edition is **optimized for readability at the table**.  
All edge cases, Duels, and long-form explanations are in the **Reference Edition**.

---

## 1) Goal
1. **Build a Capital** connected to your **Chain of Command**.
2. On your turn, **declare Shogun**.
3. Finish the **Shogunate Final Cycle** (everyone gets one last turn).
4. **Highest score wins** (being Shogun helps, but does not guarantee victory).

> **Win trigger (endgame starts):** the first player who declares Shogun with **1 connected Capital**.

---

## 2) What You Do on Your Turn
You always manage **two resources**:

- **Koku (K#)** = currency (stored on your player board, **cap 6**).
- **Protection tokens** = map resource (defense + building progress).

### Spend Koku vs Spend Protection (table helper)
| You want to… | Spend… | Cost |
|---|---:|---:|
| Reveal any face-down card | Koku | **K3** |
| Convert currency into protection | Koku → Protection | **K2 → 1 token** |
| Protect a card on the map | Protection | **1 token** |
| Build a Castle or Market | Protection | **3 tokens → 1 building** |
| Progress to a Capital | Castles | **3 Castles → 1 Capital** |

---

## 3) Core concepts
### 3.1 Sudoku validity
Every **face-up Numbered card** must respect the Sudoku rule (row/column/zone uniqueness).  
If you create an illegal state, you created an **Error (Rebellion)**.

### 3.2 Chain of Command
Your **Chain of Command** is the orthogonally connected group (no diagonals) that includes your **Daimyō**.
- Only **connected** cards/buildings score.
- Many actions/builds require being connected.

### 3.3 Control
A Zone/Line/Imperial Zone is considered yours if it is fully controlled by your clan:
- In a **stack**, only the **top visible** card counts for control.
- **Face-down** cards still count as your clan for control, but do **not** score as cards.

### 3.4 Imperial Zones
**Imperial Zones** are the **4 marked central spaces** with the Emperor symbol.
- Each controlled Imperial Zone adds **+1 Koku** during Collection.
- Imperial Zones cannot receive Protection tokens and cannot host Buildings (Market/Castle/Capital).
- Face-down cards cannot be placed in Imperial Zones.

---

## 4) Setup (Standard)
1. Each player chooses a clan color and takes: deck (20 cards), player board, tokens, and buildings.
2. Remove the **Daimyō** card from your deck and keep it face-up beside your player board (not on the player board).
3. Shuffle the remaining cards and draw **3**.
4. If those 3 cards contain no Numbered card, reshuffle that hand into the deck and redraw 3 (repeat until at least one Numbered card).
5. This setup redraw is **not** Visit the Emperor and does not consume the Emperor marker.
6. During **Junbi**, place your **Daimyō** on the game board in a legal starting prefecture (corners are not valid on 6x6).
7. Determine first player; play clockwise.

---

## 5) Turn structure
### Beginning of turn
- **Draw up to 3 cards** (if you already have 3, draw 0).
- **Expert Mode (Visit the Emperor):** after this refill and before your first played card, if your Emperor marker is unused, you may reshuffle deck+discard and optionally include your entire hand (all cards or none), then mark the Emperor marker as used.
- If you included your hand, draw back up to **3** immediately after the reshuffle. If you did not include hand cards, this action grants no additional draw.

### Main section
1. **Play cards** down to **2 cards in hand**. You may play one additional last card by paying **1 Koku** (ending with 1 card).
2. **Convert Koku → Protection** (K2 → 1 token), any amount, at any time in your main section.
3. **Place Protection tokens** on eligible cards.
4. **Build** (Market/Castles/Capital) if requirements are met.
5. **Reveal** (pay K3 to reveal any face-down card, including your own).
6. **Fix Errors** (earn rewards).
7. **Declare Shogun** if you have a connected Capital.

### End of turn
1. **Draw back up to 3**.
2. **Collect Koku** (see Player Board values; summary below).
3. Discard Koku above the **cap 6**.
4. Pass the turn.
5. If your deck runs out:
   - Standard: reshuffle discard to form a new deck.
   - Expert (Emperor enabled): at first required-draw exhaustion, do the same reshuffle and mark Emperor Visit as lost if it was unused.
   - If this happens during beginning refill, you cannot declare proactive Visit the Emperor later in that same turn.

> **Koku Collection (summary)**: base income + bonuses from **Market**, **Zones**, **Lines**, and **Imperial Zones**.  
> **Zones and Lines both count** if you control both (they stack).
> **Quick formula**: +1 base, +1 if Market built, +1 per controlled Zone, +1 per controlled Imperial Zone (apply all valid sources; use the Player Board cap for this counting step).

---

## 6) Cards and Placement
### 6.1 Daimyō
- Placed on the game board during Junbi setup placement.
- Cannot be removed or played face-down.
- Can hold up to **3 reserved build tokens** (not automatic protection).

### 6.2 Numbered cards (1–6)
You may:
- Place them anywhere legal (respecting Sudoku validity).
- **Stack** them if the resulting top face-up state is still valid.
- Use them as the main **base** for Protection/buildings.
- Place them **face-down** as placeholders (see Face-down rules).

### 6.3 Retainers (Special cards)
Each Retainer offers **two actions (A1 / A2)**; when used you choose **one**.
Depending on icon/text, a Retainer is either:
- **Placed** on the map (with placement rules), or
- **Discarded** to resolve an effect.

Some Retainers can stack or cover cards if their text allows it.

> Full Retainer action list is in the **Reference Edition** appendix.

---

## 7) Face-down cards, Reveal, and traps
Face-down play exists to keep the map moving (chain extension, zone contests, bluff).

Rules:
- **Numbered** cards may be placed **face-down** as hidden placeholders.
- Some Retainers may be placed **face-down** as hidden **traps** (current set includes Shinobi and Ronin; expansions may add more).
- Face-down cards may be placed on top of Retainer/Special cards when stacking is otherwise legal.
- Face-down cards cannot be placed in Imperial Zones.
- **Face-down cards cannot receive Protection tokens.**
- A **Capital is always placed on a face-down base card**.
- While a Capital remains on top, its base card cannot be attacked, revealed, or destroyed by effects.

### Reveal (Bribery)
Pay **K3** to reveal any face-down card.

- If it’s a normal card: flip it face-up and apply legality checks.
- If it’s a trap: resolve its trap effect once, then remove it from the map and discard it.
- Reveal can also fix/trigger Errors (see Errors).

---

## 8) Errors (Rebellions)
An **Error** is an illegal Sudoku state (typically a forbidden duplicate).

Timing:
- If an illegal placement is spotted **before turn handoff**, anyone may call it.
- The acting player fixes it immediately by moving the card or choosing another legal play/card; if they change card, the originally attempted illegal card is not lost (it returns to hand).
- On **your turn**, you may fix any detected Errors.

Fixing:
- The fixer chooses which offending card to remove (and removal order).
- If removing a card reveals another Error, the same fixer may continue fixing.

Rewards:
- The fixer gains **+1 Protection token per Error fixed**.
- Each gained token is placed immediately on a legal eligible **face-up** map card.
- If no legal map placement exists, the token may be parked on your Daimyō reserve (max 3).
- If no legal map placement exists and Daimyō reserve is full, that token is lost and returned to supply.
- Removed cards also remove any attached protection/building on that layer.

---

## 9) Protection tokens, Market, Castles, Capital
### 9.1 Protection tokens
- Place 1 token on an eligible **face-up** card (max **one** piece per card: token **or** Castle **or** Market).
- Protected cards cannot be removed unless protection is removed first, or an effect bypasses it.
- In stacks, protection applies to the **top** visible layer.

### 9.2 Build a Market or Castle
Buildings are made by **progression**, not by paying Koku directly.
- If you have **3 Protection tokens** on connected cards in your Chain of Command and a valid connected Numbered destination exists, conversion is **mandatory**.
- Remove any **3 eligible Protection tokens** from your connected chain.
- Place **1 Castle or 1 Market** on any eligible connected Numbered card (it does not need to be one of the source cards).

Notes:
- Max **1 Market** per player.
- Max **3 Castles** per player.
- If a Castle conversion would create a 4th Castle, you may relocate one of your existing Castles to a legal connected Numbered destination.
- If no legal relocation is possible, that Castle conversion cannot resolve and the 3 tokens remain in place.
- If you have 3 connected Castles, Capital conversion remains mandatory.

### 9.3 Form a Capital
Requirements:
- **3 Castles** in your Chain of Command.
- Continuous connectivity to your Daimyō.

Process:
- Remove the 3 Castles.
- Choose a connected Numbered card space as the Capital base:
  - If the base is face-up, turn it face-down.
  - If a face-down card already exists there, use it.
- Place the **Capital** on top.

---

## 10) Shogun and endgame
When you have a **connected Capital**, you may **declare Shogun** during your turn.
- The game enters the **Shogunate Final Cycle**: all other players take one final turn.
- If your Capital becomes disconnected from your Chain of Command before endgame closes, your Shogun status is revoked until reconnected.
- Anchor edge case: if the first Shogun (anchor) loses status, then restores it, they must declare again and wait one full rotation before closure.

All alliances (Expert Mode) end immediately when the Final Cycle begins.

---

## 11) Scoring (Standard)
Score connected elements only:

- **+1** each face-up card on the map (Numbered or Retainer).
- **+1** each fully controlled **Zone** or **Line**.
- **+1** each **Castle**.
- **+3** each **Capital**.
- **+4** if you are **Shogun**.
- **+1** (Expert Mode) if you never used your Emperor reshuffle right.
- Automatic Emperor-right loss from required-draw deck exhaustion counts as "used" (no +1 bonus).

Rules:
- Face-down cards do **not** score the +1 card value.
- Face-down cards still count for Zone/Line control if they belong to your clan.
- Tie-break: highest remaining Koku on the player board wins; if still tied, the game is a shared victory.

---

## 12) What’s in the Reference Edition
- Full Retainer actions and timing notes
- Expert Mode (Alliances, Visit the Emperor, Destiny Path)
- Duels (2 players)
- Glossary + edge cases

---

## 13) Key Differences vs v23 Play
- Terminology standardized: **Imperial Zones** (replacing older mixed wording).
- **Imperial Zones** are explicitly restricted: no Protection tokens and no Buildings.
- **Imperial Zones** also block face-down placement.
- End-of-turn flow now explicitly includes deck exhaustion handling (Standard reshuffle vs Expert Emperor flow).
- Reveal/trap wording is clarified for face-down cards and trap resolution.
- Shogun closure includes the anchor edge case (loss and restore of Shogun status).
- Scoring now states a clear tie-break (highest remaining Koku on Player Board, then shared victory).
- Koku collection is summarized with a quick formula for table use.
- Hand-floor rule updated: play down to 2, then pay 1 Koku to play the last card.
- Koku storage cap reduced to 6.
- Capital scoring increased to +3.
- Error fix reward now has Daimyō-reserve fallback (and discard overflow when no slot is available).
- Build progression now clarifies mandatory 3-token conversion and 4th-Castle relocation handling.
- Duels tie-break now follows the same global tie-break rule (highest remaining Koku on Player Board).

---

## 14) Pending Mode Definitions (Reference)
- 5x5 (2 Players, The Duel): starting coordinates + zone geometry still pending final definition.
- 9x9 (5-6 Players, The Grand Campaign): starting coordinates + zone geometry still pending final definition.
