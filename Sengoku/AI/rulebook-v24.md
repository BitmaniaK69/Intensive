# Sengoku — Rulebook v24 (Unified Draft)
_Last updated: 2026-02-16_

This is a **unified v24 rulebook draft** based on the full conversation history in this thread.  
It contains **Setup → Turn → Placement → Economy (Koku) → Protection tokens → Buildings → Errors → Reveal/Face-down → Shogun → Scoring**, and it **highlights differences vs v22 and v23**.

> **Notation**
> - **Koku** is written as **K#** (e.g., K1, K3) for clarity.
> - **Protection token** = the physical token you place on the map (also used as building progress).

---

## 0) Design Principles
- The game already contains many interacting systems (Sudoku constraint, errors, chain of command, economy, protection, buildings, stacking, face-down play, retainers, alliances in advanced mode).
- v24 aims to **simplify the economy and make responsibilities clear**:
  - **Koku (K#)** = currency (mainly Reveal + rewards + end-of-turn income).
  - **Protection tokens** = map resource used for **protection** and **building progress** (Castles/Market).

---

## 1) Components

### 1.1 Cards
- **Daimyō**: 1 per clan/deck.
- **Numbered cards**: numbers **1–6**, **2 copies per number**.
- **Retainers / Special cards**:
  - 1 per retainer type in the deck, plus
  - 1 extra unique special per character (per deck/clan).

### 1.2 Buildings / markers
- **Market** (building)
- **Castles** (up to the point where the 3rd becomes the Capital; see Buildings)
- **Capital**
- **Shogun status** (implicit; triggered by Capital condition)

### 1.3 Tokens
- **Protection tokens** (physical tokens placed on the map; also used as build progress)
- **Koku** tracked on the player board (reserve cap: **K9**)

---

## 2) Board, Zones, and Central Spaces

### 2.1 Board
- The main board is a **6×6 grid**.

### 2.2 Zones
- The board is divided into **Zones** (e.g., Z1–Z6).
- Zones matter for **income and/or scoring** (see Economy and Scoring).

### 2.3 Central spaces
- There are **4 central spaces** (the “central” area) designed to be contested.

---

## 3) Core Concepts

### 3.1 Sudoku Validity
Many placements must be **Sudoku-valid** (the specific uniqueness rule is assumed from earlier versions of Sengoku and remains unchanged in v24).

### 3.2 Chain of Command
- Each player’s **Chain of Command** starts from their **Daimyō**.
- Some cards must be placed **connected/near the chain** (defined by their card rule/icon).
- Other cards (notably **Numbered cards**) can be placed anywhere (see below).

---

## 4) Card Types and Placement Rules

## 4.1 Daimyō
- Placed on the board at setup in a valid starting space.
- Cannot be removed or placed face-down.
- Starts your chain of command.
- Provides up to **3 “storage/build slots”** that can hold Protection tokens contributing to building progress.

**Δ v23:** Setup begins with **only** the Daimyō on the map (no extra numbered card placed at setup).  
v24 keeps this.

---

## 4.2 Numbered Cards (1–6)
**Placement**
- A numbered card can be placed **anywhere on the board** as long as it is **Sudoku-valid**.

**Chain**
- Numbered cards **do not need** to be connected to your chain of command.
- This is intentional to prevent board lock-ups and to enable strategic “off-chain” plays.

**Stacking**
- Numbered cards may be stacked when allowed and when the resulting state remains valid (or as permitted by specific card effects).

**Building base**
- **A Castle requires a Numbered card base** (1 numbered base per Castle).  
  (Kept as a manual rule; not mandatory to print on the player board.)

---

## 4.3 Retainers / Special Cards
Retainers fall into functional placement categories (as indicated by their icon/text):

### A) Chain-connected / near-chain retainers
- Must be placed connected to (or near) your chain of command (per their rule).
- Examples: **Samurai**, **Ashigaru**.

### B) Anywhere-placed retainers
- Can be placed **anywhere** on the board, respecting their own condition text.
- Sudoku validity is ignored only if a card explicitly allows it.

### C) Sacrifice-only retainers
- Trigger an effect by being **sacrificed/discarded** and are **not placed** on the board.

### Retainer stacking
Some retainers can stack if their effect allows it:
- **Sohei (Warrior Monk)**: can be placed on top of another Sohei, or on top of an unprotected Numbered/face-down card (any clan).
- **Samurai**: A1 includes “Cover a card”, implying stack/cover behavior.

> Targeting of stacks (“primary target = top card” vs “hit entire stack”) should be defined in the manual.  
> In current context: Ronin can affect an entire stack; otherwise top card is often the main target.

---

## 5) Face-down Cards (v24 status: NOT FINAL)
Face-down rules are **not fully finalized** in v24. The following is known from prior versions and current direction:

- Face-down play exists for bluff/chain extension and to avoid dead turns.
- Reveal exists and costs Koku (see Reveal).

**OPEN decisions (to finalize later):**
1) Can face-down cards be protected? (Previously “no”; now undecided)
2) Do face-down cards score 0 at endgame? (Previously “yes”; now undecided)
3) Can face-down cards be used as building bases? (Undecided)

---

## 6) Reveal / Bribery (v24)
- To reveal (flip) **any** card (including your own): pay **K3**.

**Δ v22:** Reveal cost was token-based (older approach).  
**Δ v23:** Reveal was **2 tokens** and could be used on your own cards.  
**v24:** Reveal is paid in **Koku**: **K3**.

---

## 7) Errors (Sudoku Violations)

### 7.1 What is an Error?
An **Error** is a board state where Sudoku validity is violated.

### 7.2 Why Errors matter
Errors are **strategic**:
- You can intentionally create an error to later “fix it” and remove enemy cards.
- Face-down play + later reveal can be used to create/confirm errors near key pieces and punish opponents.

### 7.3 Fixing Errors and rewards (v24)
When you fix errors (often via reveal + correction), you gain:
- **+K1 per Error fixed**

Multi-fix frequency model used in balancing discussions:
- ~20% of the time: 2 errors fixed in one action → +K2
- ~5% of the time: 3 errors fixed → +K3

### 7.4 Reveal outcomes (playtest heuristic)
Approximate distribution used during simulation reasoning:
- 50% meaningful fix,
- 25% trap,
- 25% bluff/empty/no longer relevant.

Late-game the “meaningful fix” rate can increase (more structure on board).

---

## 8) Economy (v24): Koku and Income

### 8.1 Koku Reserve
- Players store Koku up to **K9**.

### 8.2 Koku Income (end of your turn)
At the end of your turn gain:
- **+K1** base
- **+K1** if you own the **Market**
- **+K1** for each **Zone** you control
- **+K1** for each **Central space** you control

> Optional cap “max Koku gained per turn” appeared in a draft sheet (e.g., max +K5) but is **not locked** here; keep it in the manual or remove for simplicity if it causes confusion.

**Δ v23:** Zones stopped being an income source, making them less attractive.  
**v24:** Zones re-gain importance via Koku income.

---

## 9) Protection Tokens (map rules)

### 9.1 Protection purpose
Protection tokens are used to:
1) Protect face-up cards against attacks, and
2) Serve as building progress (Market/Castle) by placing 3 tokens across turns.

### 9.2 Basic protection
- Place **1 Protection token** on a valid target card to protect it.
- (Detailed constraints such as “max 1 per card” and face-down restrictions can remain in the manual, per your preference.)

### 9.3 Token interaction
Some card effects can:
- remove a token,
- steal up to 2 tokens,
- or remove cards/buildings (depending on card text).

---

## 10) Buildings: Market, Castles, Capital

### 10.1 Critical rule: buildings are not paid with Koku
You **do not** buy a Castle or Market with Koku.
You must be able to physically place tokens on the map (or in Daimyō slots).

### 10.2 Building a Castle or Market (progress build)
To build **one Castle** OR **one Market**:
1) Place **3 Protection tokens** as build progress (can be over 3 separate turns).
2) Tokens must be placed on eligible build locations:
   - Numbered card bases (and/or) Daimyō token slots.
3) Once all 3 are placed, collect them and replace them with the **Castle** or **Market**.

### 10.3 Capital
- A **Capital** is achieved via the Castle progression:
  - **3 Castles → Capital**
- Practical rule agreed: the “third castle” is effectively the Capital, so you do not end with “3 castles + capital” simultaneously.

**Δ v22:** Win condition involved 2 Capitals.  
**Δ v23:** Changed to 1 Capital due to faster pacing.  
**v24:** Keeps 1 Capital as the Shogun trigger.

---

## 11) Retainers — Action Reference (snapshot)
This section captures the actions provided in the thread (wording preserved as much as possible).

### Samurai — Elite Knight (#Army 1) — (Chain-connected / near chain; can cover/stack)
- **A1:** Place near or Cover a card of your Clan, then Kill 1 unprotected adjacent card OR Remove 1 Token  
- **A2:** During an opponent’s turn, Block their Special card action (they may use another card)

### Ashigaru — Light Infantry (#Army 2) — (Chain-connected / near chain)
- **A1:** Place near a card of your Clan. Kill up to 2 adjacent unprotected Number or face-down cards  
- **A2:** Draw 4, keep 1, return others top/bottom of the deck

### Chajin — Tea Master (#Power 1) — (Placement category not finalized)
- **A1:** Draw 2 new cards (max 1 of this action per turn)  
- **A2:** Draw and play 1 card right away. If Special then can Add +2 to the effect (max 3)

### Sohei — Warrior Monk (#Power 2) — (Stack-enabled)
- **A1:** Place on top of another Sohei or unprotected Numbered or face-down card of any Clan  
- **A2:** Retrieve the top 1 card from the discard pile into your hand

### Shinobi — Spy Assassin (#Mercenary 1) — (Placement category not finalized)
- **A1:** Kill and Remove from the map 1 Special + any Token on it OR 1 face-down card  
- **A2:** Spy on a player's hand, pick 2 cards to Discard, then Draw extra at the end of the turn

### Ronin — Masterless Warrior (#Mercenary 2) — (Affects stacks; placement category not finalized)
- **A1:** Replace 1 unprotected (non Ronin) card and Return it to the owner, Kill or Return the rest of the stack  
- **A2:** Steal up to 2 Tokens from Number or Retainer cards (max 1 per Player, rest from resources)

---

## 12) Turn Structure (v24 — needs final wording)
From v23/v24 discussion we know:
- Players commonly play **2 cards per turn** minimum in practice.
- Hand management target is often **3 cards in hand**, but it can go down to **1**.

**OPEN (big) to finalize:** exact “steps of a turn” (phases, timing windows for reveals, reactions, fixing errors by others, etc.) are not fully restated in this thread and should be formally written when you decide the exact structure.

---

## 13) Shogun (Win Trigger), Final Reveal, and Game End
### 13.1 Shogun trigger
A player becomes **Shogun** when they start **their turn** with:
- **1 Capital** connected to their Chain of Command.

The game **ends when the first Shogun is declared** (i.e., when a player starts their turn with a Capital).

### 13.2 Multiple Shogun scoring
It is possible that more than one player becomes Shogun (in rare cases, up to all players).
- If there are **multiple Shogun**, **each Shogun gains the Shogun bonus points**.
- Current draft bonuses:
  - **1st Shogun: +4 points**
  - **2nd Shogun: +3 points**
  - (If more are possible, define +2 / +1 or another ladder in the Scoring section.)

### 13.3 Final Shogun Reveal window (last-turn privilege)
After the game-end trigger, only players who are **Shogun** may take a final “last turn” reveal action:
- Each Shogun may spend **Protection tokens** to **reveal face-down cards** during this final window.
- This is a special exception (v24 normally uses **Koku (K3)** to reveal).

> Purpose: give Shogun players a final tactical chance to expose bluffs/traps and convert information into points before scoring.


---

## 14) Endgame Scoring (partially locked, partially open)
Known scoring model discussed:
- **+1 per face-up card** (linked / “true territory”)
- **+1 per Castle remaining**
- **+2 per Capital**
- Shogun points (each Shogun gets a bonus): currently **+4 for the 1st Shogun, +3 for the 2nd Shogun** (define additional steps if you allow 3rd/4th Shogun)
- Possible bonuses considered: leftover Koku, tokens on Daimyō, zones/central points (not locked)

Typical score ranges mentioned: ~8–15 (excluding Shogun points).

---

# Appendix A — Differences (v24 vs v22/v23)

## A1) Reveal
- **v22:** token-based reveal (older approach).
- **v23:** reveal = 2 tokens (also on your own cards).
- **v24:** reveal = **K3**.

## A2) Victory condition (Capital)
- **v22:** win with 2 Capitals linked.
- **v23:** 1 Capital is enough.
- **v24:** Shogun triggers with 1 Capital at start of turn (linked).

## A3) Zones importance
- **v23:** Zones not a resource source → less engaging.
- **v24:** Zones provide Koku income again.

## A4) Economy responsibilities clarified
- **v22/v23:** tokens carried too many roles and were harder to read.
- **v24:** Koku handles currency; Protection tokens handle map protection and building progress.

---

# Appendix B — Open Questions (Big vs Minor)

## BIG (resolve soon)
1) Exact **Turn Structure** and timing windows (reactions, reveal timing, fixing errors timing).
2) Final **face-down rules** (protectable? score? build base?).
3) Optional **cap on Koku gained per turn** (keep/remove).

## MINOR (iterative)
- Full list of which retainers are sacrifice-only vs placeable anywhere.
- Exact definition of “near/connected to chain” (orthogonal only? diagonal?).
- Stack targeting defaults vs exceptions (e.g., Ronin).
- Formal durability rule for Castles in “obvious error” situations.
