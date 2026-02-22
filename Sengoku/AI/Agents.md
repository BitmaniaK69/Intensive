# AGENTS.md — Sengoku (Board Game) — Design + Rules + Player Board (v22 → v23 → v24)
_Last updated: 2026-02-14_

> Purpose: This file provides **Codex** with complete, high-fidelity context to work on the **Sengoku** board-game design tasks discussed in the current thread (versions v22, v23, v24), especially the **economy redesign with Koku** and the **player board text/icon updates**.  
> **Constraint:** The game is already complex; changes must **simplify**, not add “German-style” bookkeeping.

---

## 1) Project Goal & Current Focus

### What we are building
A competitive board/card game set in Sengoku Japan with:
- A **6×6 grid** where placements must respect a **Sudoku-like uniqueness** constraint.
- A **Chain of Command** starting from each player’s **Daimyō** card and extending through connected cards.
- **Face-up / face-down** cards (including bluff/trap usage).
- **Errors** (invalid placements / Sudoku violations) as a strategic mechanic to remove cards.
- **Resources / currency**, **protection**, and **buildings** (Castles, Market, Capital).
- Combat/interaction via **Retainer** cards (special actions).

### Current focus (v24)
We are moving from **v23 to v24** by introducing **Koku** as currency, while keeping the game **simple and readable**:
- **Koku = currency** (used for reveal/bribery + rewards + endgame leftover scoring if needed).
- **Protection cubes = physical map resource** used both for **protection** and **building progress** (Castles/Market).
- Update the **player board** so the economy is readable “at a glance” with minimal text.

---

## 2) Repository / File Context (non-code project)

This is not a software repo. The “working artifacts” are:
- **Player board graphics** (e.g., Oda Nobunaga sheet shared as image `OdaNobunaga.png`).
- **Rule text / manual** (not fully pasted here, but referenced as the location for detailed edge rules).
- Card list excerpts for Retainers included below.

If Codex is asked to produce deliverables:
- Prefer **short copy blocks** (ready to paste onto the player board).
- Prefer **structured changelogs** (v22/v23/v24 notes).
- Avoid long prose unless explicitly requested (manual sections).

---

## 3) Game Logic State (CRITICAL)

### 3.1 v22 — Major introduced systems (relative to earlier versions)

#### Deck / Card types
**Numbered Cards**
- 2 copies for each number 1–6.
- Can be:
  - Stacked (only if the Sudoku uniqueness remains valid),
  - Protected by token/cube,
  - Flipped face-down,
  - Used as bases for buildings (castle/capital),
  - Placed anywhere as long as valid.

**Retainers (Special cards)**
- 1 per type in the deck + 1 unique per character.
- Depending on symbols:
  - Can be sacrificed/discarded to trigger actions,
  - Can be placed **near the Chain of Command** (new placement restriction concept),
  - Can be placed anywhere (ignoring Sudoku validity),
  - Can be placed face-down as traps,
  - Can be protected by token/cube.

**Daimyō Card**
- 1 per clan/deck.
- Must be placed at game start in designated starting positions.
- Cannot be removed or flipped face-down.
- Starts Chain of Command.
- Has up to **3 token/cube slots** used to help build castles.

#### Mechanics (v22)
- **Siege towers removed**, **Market introduced**.
- Face-down/traps introduced.
- Reveal (in v22) required a cost (later moved/changed).
- Win condition then: **2 Capitals** linked with Chain of Command.
- Shogun points: 4 / 3 / 2 (first/second/others).
- Final scoring: **only face-up and linked** cards score; face-down extend chain but score 0.

#### Map changes (v22)
- Starting zones defined.
- Token bonuses on map for first arrivals (later changed).
- Dark Japan map aesthetic with starting markers and bonus markers.

#### Testing feedback (v22)
- 3 tests.
- Issues: speed, similar progression across players, still turtling.
- Improvements: cards/layout appreciated; positioning options improved.
- Negative: “less funny” (tone/feel decreased).

---

### 3.2 v23 — Changes (still being tested)

#### Key rule changes
- Reveal can be paid to flip **any** card (including your own): **2 tokens** (v23).
- Setup: start with **only Daimyō** (no extra numbered card).
- Hand: normally keep **3 cards**, can go down to **1**; implies players generally play **2 cards per turn** minimum.
- Zones are **no longer a resource source** (this reduced zone attractiveness → needs fixing).
- Win condition: **1 Capital** is enough (game faster, 2 capitals too slow).
- Emperor visit remains (introduced v22) — not visiting gives +1 point.

#### Map changes (v23)
- Starting positions increased; Daimyō placement must respect Sudoku validity.
- Some starting squares marked (+) and previously gave +1 extra card (seen as too confusing/strong).
- Central area: no longer a “first arrive gets token”; now **4 central free zones** worth **1 point** to controller.

#### Testing feedback (v23)
- 2 tests.
- Issues: zones lost importance; some confusion with “2 cards now”; progression slower; actions need review.
- Improvements: less turtling; more fighting; more errors via traps; more fun.
- Map layout improved; zones still less engaging.

---

### 3.3 v24 — Economy redesign (Koku) and player board updates (main topic)

#### Core design intent
The game is already complex (Sudoku + Errors + Resources + Protection + Buildings + Alliances + Combat + Hand management + Chain + Face-down + Stacking).  
v24 must keep gameplay **fast + intuitive**.

#### Terminology and UX
- **Koku** is historically huge; in-game it is treated as an **abstract wealth unit**.
- Icon issue: coin-with-hole too small/hidden by numbers → solution chosen:
  - Use notation **K1, K3, K6** in text instead of relying on a hard-to-read icon.
- Previous “fan icons” for tokens were removed in the latest board; now:
  - The physical cube represents **Protection** and also “build progress”.

#### Spending: Koku vs Protection cubes
**Koku (Currency)**
- Used for **Reveal/Bribery**: **Reveal a card costs K3** (confirmed).
- Can also be gained from income and error-fix rewards.
- Reserve cap chosen: **K9**.

**Protection cubes (Physical map resource)**
- Used to **protect cards** on the map.
- Also used to **build Market/Castle** by “placing 3 cubes across turns”.

**Important correction (the main misunderstanding that was fixed):**
- **Market/Castle are NOT paid in Koku.**
- They are built only by **placing 3 protection cubes** on eligible cards (can be across 3 different turns) and then **collecting them** to replace with a **Market** or **Castle**.
- If you cannot physically place those 3 cubes on the map (or on Daimyō slots), you cannot build, even if you had Koku.
- **Daimyō has up to 3 cube slots** which can contribute to that build requirement.
- **Numbered card requirement:** each Castle requires a **Numbered card** base (kept in the manual, not necessarily on the sheet).

#### Income (Koku) — current draft
At end of your turn:
- Base **+K1**
- If you own the **Market**: **+K1**
- Each **Zone you control**: **+K1**
- Each **Central space** you control: **+K1**
Optional/uncertain: cap on Koku gained per turn (was seen as “Max +K5” in the sheet draft; final decision not locked in this thread).

#### Reveal + error-fix reward model (used for balancing simulations)
Reveal outcomes (estimates used for reasoning):
- ~50% of reveals produce a real fix / payoff,
- ~25% trap,
- ~25% bluff/empty/no longer relevant.
Fix reward:
- +K1 per error fixed,
- sometimes 2 errors fixed (~20%),
- rarely 3 errors fixed (~5%).
Late game: probability of useful fixes tends to increase (more structure/stacking).

Traps present (current snapshot):
- Only a couple “trap-like” mechanics were mentioned in the thread (linked to Shinobi/Ronin A2 context).
- When a trap triggers, the trap card is removed from the map and discarded.

#### Shogun / endgame in v24
- **Shogun triggers** when a player starts their turn with **1 Capital linked to chain**.
- The “2 Capitals to win” condition is not used in v23/v24.
- Shogun points were discussed to move from 4/3/2 to 3/2/1 (not locked).

Scoring context:
- Face-up linked cards score; face-down score 0 (but extend chain).
- Castles and Capitals contribute to score (values not finalized in this file).
- Typical points range discussed: ~8–15 points (excluding Shogun points).

---

### 3.4 Starting positions & balance notes (4-player meta)
- 65% of games are played with **4 players**.
- “Flank line” starts (A3/A4/F3/F4) are generally more consistent (less sandwich).
- “Gateway” starts (C1/D1/C6/D6) can rush center but are more exposed in 4p.
- (+) distant starts felt disadvantaged; giving +1 extra card felt too strong/confusing; alternative proposed: +1 Koku or +1 cube.

(Exact zone mapping and central squares were provided; keep in manual if needed.)

---

## 4) Card Actions Snapshot (Retainers excerpt)
Used in thread (for context of interaction + token stealing + blocking):

### Samurai — Elite Knight (#Army 1)
- A1: Place *near* or Cover a Clan card, then Kill 1 unprotected adjacent card or Remove 1 Token
- A2: During opponent’s turn, Block their Special action (they may use another card)

### Ashigaru — Light Infantry (#Army 2)
- A1: Place near your Clan card; Kill up to 2 adjacent unprotected Number or face-down cards
- A2: Draw 4, keep 1, return others top/bottom

### Chajin — Tea Master (#Power 1)
- A1: Draw 2 new cards (max 1 per turn)
- A2: Draw & play 1 immediately; if Special can add +2 to effect (max 3)

### Sohei — Warrior Monk (#Power 2)
- A1: Stack on another Sohei or unprotected Numbered/face-down of any clan
- A2: Retrieve top 1 from discard to hand

### Shinobi — Spy Assassin (#Mercenary 1)
- A1: Kill/remove 1 Special + any Token on it OR 1 face-down
- A2: Spy hand, discard 2 chosen cards, then draw extra at end of turn

### Ronin — Masterless Warrior (#Mercenary 2)
- A1: Replace 1 unprotected non-Ronin; return it to owner; kill/return rest of stack
- A2: Steal up to 2 Tokens from Number or Retainer cards (max 1 per player; rest from resources)

Notes:
- Face-down cards cannot be protected.
- Ronin can affect entire stacks (“main target” language used).

---

## 5) Player Board Copywriting — What to change (English)
The user wants minimal text on the sheet; details stay in manual.
Essential things that MUST be visible (v24):
- Koku income (end of turn breakdown)
- Koku reserve cap (K9)
- Reveal cost (K3)
- Build steps using 3 protection cubes (castle/market)
- Capital and Shogun trigger

Recommended wording improvements (natural English, short):
- “Every counting” → “End of turn”
- “Every zone conquered” → “Each Zone you control”
- “Per Central controlled” → “Each Central space you control”
Title suggestions:
- “Resource Counting” → “Koku Income”
- “Koku Resource Reserve” → “Koku Reserve”
- “Tokens Conversion” → “Build & Protection”
Phrase that needed replacement:
- “Evolution of the tokens transformed” → prefer:
  - “Token Progression” / “Token Upgrade Path” / “Build Progress (Tokens)” / “Building with Tokens”

### Notation rule (important UX decision)
- Use **K#** notation (K1/K3/K6) because the coin icon hole is too small / hidden by number.
- Fan icons were removed; cubes represent protection/build.

---

## 6) Constraints & “Do / Don’t” Rules for Codex

### High-level constraints
- Avoid adding new subsystems.
- Avoid adding extra per-turn micro-accounting.
- Sheet text must remain compact; only “at-turn” info.

### Do
- Keep the player board readable with minimal lines.
- Provide “copy-ready” text blocks for each box.
- When proposing changes, provide:
  - **Before → After** phrases
  - Alternative short versions if space is tight.

### Don’t
- Don’t reintroduce Siege Towers.
- Don’t shift building costs fully to Koku (build requires 3 cubes placed).
- Don’t add long explanations on the sheet; put them in manual.

---

## 7) Immediate Next Tasks (What to do in the next session)
1) Finalize whether “Max Koku gained per turn” exists (e.g., Max +K5) or remove it for simplicity.
2) Confirm the final Koku income formula (especially Zone and Central contributions).
3) Produce final copy for the three player board boxes:
   - Koku Income
   - Koku Reserve (K9, Reveal K3)
   - Build & Protection (1 cube protect; 3 cubes build castle/market; 3 castles capital; Shogun trigger)
4) Ensure any leftover “Siege Towers” references are removed from the “Playing round” box text.
5) Keep “castle requires numbered card” and “no protection on face-down” in the manual unless space allows.

---

## 8) Minimal Copy Pack (Ready-to-paste, compact)
(Use K# notation; cubes represent protection/build)

### Koku Income
- End of turn: **+K1**
- If you own the Market: **+K1**
- Each Zone you control: **+K1**
- Each Central space you control: **+K1**
(Optional: “Max +K5 per turn” if confirmed)

### Koku Reserve
- Max: **K9**
- Reveal a card: **K3**

### Build & Protection
- **1** cube: Protect 1 card
- **3** cubes: Build Castle or Market
- **3 Castles**: Capital
- Start your turn with **1 Capital** (linked): Shogun (game ends)

(Any extra constraints stay in the manual.)

---

## 9) Notes on “context rot” and verbosity
The user requested full detail (do not omit anything).  
However, the player board itself must remain short; Codex should keep:
- Long explanations here (AGENTS.md / manual),
- Short actionable text on the sheet.
