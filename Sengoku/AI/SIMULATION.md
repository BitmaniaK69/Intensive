# Sengoku - Simulation Protocol (v24.1)

This file defines how we will run a step-by-step match simulation with me acting as the game simulator.

Primary references:
- `AI/RulesV24.md` (full rules source)
- `AI/sengoku_rulebook_v24_play.md` (play/quick version)
- `AI/KOKU_BALANCE_IDEAS.md` (optional balance variants)

## 1) Simulation Goal

Run a turn-by-turn match simulation to:
- validate game flow
- test Koku / Protection economy
- expose rule edge cases
- evaluate the impact of balance variants

## 2) Default Ruleset (Recommended)

Recommended default for the first test:
- `Rules V24.1`
- `Standard` mode (3-4 players, 6x6 board)
- No Expert rules (Alliances / Visit the Emperor) unless needed

We can enable variants before the match starts (see Section 5).

## 3) What I Need Before We Start

Please provide these inputs to begin:

1. Match mode
- `Standard 3p/4p (6x6)` or `Duels 2p (5x5)`

2. Players and clans
- list of players (short name + clan/color)
- which player you control (if you want to pilot only one)

3. Initial turn order
- first player
- clockwise order

4. Simulation type (important)
- `Designer-driven`: you decide moves for everyone
- `Hybrid`: you decide for 1+ players, I simulate the others
- `Autoplay`: I simulate all players (with declared priorities)

5. Hidden information handling
- `Open info`: hands and deck order visible (best for rules testing)
- `Fog of war`: only public information visible

6. Setup / randomization method
- `Real shuffle` (you provide draws as they happen)
- `Seeded` (fixed test order / seed)
- `Scripted opening` (predefined opening hands to test a scenario)

7. Active modules / variants
- Expert Mode: `On/Off`
- Alliances: `On/Off`
- Visit the Emperor: `On/Off`
- Balance variants (example): `Line income = +2 Koku` instead of `+1`

8. Log detail level
- `Compact` (one snapshot per turn)
- `Detailed` (snapshot after each action)
- `Debug` (explicit rule checks and reasoning)

## 4) Simulation Conventions (Proposed)

### 4.1 Board Coordinates (default)

For the 6x6 board, we will use:
- Columns: `A B C D E F`
- Rows: `1..6`
- Example cell: `C4`

Operational assumption (to confirm):
- row numbers increase top to bottom (`1` at the top, `6` at the bottom)

### 4.2 6x6 Zones (temporary convention until official map IDs are fixed)

The rules say "6 zones of 3x2" but do not fully lock official zone IDs/coordinates yet.
For simulation, we will use this convention (can be overridden):

- `Z1 = A1-C2`
- `Z2 = D1-F2`
- `Z3 = A3-C4`
- `Z4 = D3-F4`
- `Z5 = A5-C6`
- `Z6 = D5-F6`

Imperial Zones (4 central cells, to confirm with printed board):
- `C3`, `D3`, `C4`, `D4`

Imperial Zone restrictions (v24.1):
- no face-down cards
- no Protection tokens
- no Buildings (Market/Castle/Capital)

### 4.3 Cell / Stack Notation (textual visual format)

Clan code standard (recommended for simulations):
- `TI` = Tokugawa Ieyasu
- `TH` = Toyotomi Hideyoshi
- `ON` = Oda Nobunaga
- `AM` = Akechi Mitsuhide

Proposed notation per cell:
- `CLAN:TopCard[flags]`

Numbered card notation (readability convention):
- use `NumX` (examples: `Num2`, `Num4`, `Num9`)
- use `Down` for a face-down top card (`facedown`)

Examples:
- `TI:Num4` = Tokugawa Ieyasu Numbered 4 face-up
- `AM:Down` = Akechi Mitsuhide face-down top card
- `TI:Sam[+P]` = Samurai Retainer with Protection
- `ON:Num2[+CS]` = Numbered 2 with Castle
- `TH:Down[+CAP]` = Capital on a face-down base (top = Capital)

Standard flags:
- `[+P]` Protection token
- `[+MK]` Market
- `[+CS]` Castle
- `[+CAP]` Capital

When stack detail matters:
- `C4 stack: bottom TI:Num3 / middle AM:Down / top TI:Sohei[+P]`

## 5) Testable Variants (declare before game start)

We can define a test profile. Example:

- `Economy Variant A`:
  - Zone income = `+1`
  - Line income = `+2` (from `AI/KOKU_BALANCE_IDEAS.md`)
  - all other rules remain v24.1

Other possible variants:
- Koku storage cap
- Reveal cost
- paid last card (`1 Koku`)
- Capital / Shogun scoring

Important:
- every variant must be declared before Turn 1
- I will print the active ruleset/variant in the log to avoid confusion

## 6) Simulation Flow (turn by turn)

### 6.1 Pre-game (setup)

1. Confirm match configuration (Section 3)
2. Confirm map conventions (Section 4)
3. Set up deck/hand start state
4. `Junbi`: place starting Daimyos (respecting restrictions)
   - default start: Daimyo begins with `+P1`
   - optional experimental declared setup: selected seats may begin with `+P2`
5. Create `Turn 0` snapshot

### 6.2 Turn Structure (v24.1)

For each turn we will follow this sequence:

1. `Beginning of turn`
- refill hand to 3
- Expert window: `Visit the Emperor` (if active)

2. `Main section`
- play cards down to 2 cards in hand
- optional last card by paying `1 Koku`
- convert Koku -> Protection (`2:1`)
- place gained Protection tokens immediately (if legal)
- build (Market / Castle / Capital) if requirements are met
- reveal (`3 Koku`) if declared
- fix Errors / Rebellions (with Protection reward)
- declare Shogun candidacy (if a connected Capital is completed)

3. `Immediate legality window`
- placement legality / error check before passing the turn

4. `End of turn`
- refill hand to 3
- collect Koku (base + Market + Zone/Line + Imperial)
- apply counting cap (`max +5`) and storage cap (`max 5`)
- pass turn

### 6.3 Automatic Checks I Will Run

After each action (or at end of turn if using Compact log), I will check:
- Sudoku validity (row / column / zone)
- top-card control in stacks
- Chain of Command connectivity to Daimyo
- Zone / Line / Imperial control
- mandatory building conversions (when applicable)
- Shogun candidacy / Final Cycle status
- Koku cap and component limits (Market, Castles, Daimyo reserve)

If a rule is ambiguous or incomplete:
- I stop the simulation
- I label it `RULING NEEDED`
- I propose 1-2 interpretations
- I continue only after your confirmation

## 7) Output Format During Simulation (text visual)

To give you a clear visual status, I will use these blocks consistently.

### 7.1 Board Snapshot (ASCII)

Compact 6x6 example format:

```text
Board (top cards)
      A        B        C        D        E        F
1 | TI:DY | ..    | ..    | AM:DY | ..    | ..    |
2 | ..    | TI:Num4 | ..   | ..    | ..    | AM:Num2 |
3 | ..    | ..    | [IZ]  | [IZ]  | ..    | ..    |
4 | ..    | ..    | [IZ]  | [IZ]  | ..    | ..    |
5 | ..    | ..    | ..    | ..    | TI:Num5 | ..  |
6 | ..    | TI:DY | ..    | ON:DY | ..    | ..    |
```

Notes:
- `[IZ]` marks an empty Imperial Zone
- if occupied, I will show the card and mark it as `IZ` when useful
- if a stack is relevant, I will add a separate `Stack details` block

### 7.2 Player Dashboard

```text
TI | Hand 3 | Deck 14 | Discard 2 | Koku 4 | ProtSupply 5 | Reserve 1 | Market N | Castles 1 | Capital N | Emperor Unused
AM | Hand 3 | Deck 13 | Discard 3 | Koku 2 | ProtSupply 6 | Reserve 0 | Market Y | Castles 0 | Capital N | Emperor Unused
```

### 7.3 Control / Income Summary

```text
TI controls: Zones Z1, Z3 | Lines Row2 | Imperial C3
Income preview (v24.1): base +1, market +0, zones/lines +2, imperial +1 => +4 (counting cap max +5)
```

If a variant is active:
- I will show the calculation with that variant (example: `Line = +2`)

### 7.4 Action Log (sequential)

```text
Turn 5 - AM
1. Start refill: draw 1 (hand 2 -> 3)
2. Play AM:Num4 at C2 (face-up) - legal
3. Convert Koku 2 -> 1 Protection (Koku 3 -> 1)
4. Place Protection on C2
5. End refill: draw 1 (hand 2 -> 3)
6. Collect Koku: +3 (base +1, zone +1, imperial +1), Koku 1 -> 4
```

## 8) Recommended Input Format (how you send moves)

To keep the simulation fast, use short structured commands.

Examples:
- `TI turn: play Num4 at B2`
- `AM: place Shinobi face-down at D4`
- `TI: reveal C4 (pay 3 Koku)`
- `ON: convert 4 Koku -> 2 Protection`
- `AM: fix error at row 3 removing D3 top card`

If you want me to decide:
- `Simulate AM turn with income priority`
- `Autoplay all players until end of round`

## 9) Start Template (copy/paste)

Use this block when you want to begin for real.

```md
# Simulation Start
- Ruleset: V24.1
- Mode: Standard (6x6) / Duels (5x5)
- Players:
  - P1 = [name] ([clan])
  - P2 = [name] ([clan])
  - P3 = [name] ([clan]) [optional]
  - P4 = [name] ([clan]) [optional]
- First player:
- Turn order:
- Simulation type: Designer-driven / Hybrid / Autoplay
- Hidden info: Open / Fog
- Expert modules: Alliances [On/Off], Emperor [On/Off]
- Variants:
  - Line income = +1 (default) / +2 (test)
  - [others]
- Log detail: Compact / Detailed / Debug
- Zone convention: default in `AI/SIMULATION.md` [Yes/No]
- Imperial coordinates convention: default in `AI/SIMULATION.md` [Yes/No]
- Opening hands / deck handling:
  - [scripted OR real draws provided step by step]
```

## 10) Practical Suggestions (for a good test)

For a first deep test, I recommend:

1. `Open info + Detailed`
- best for validating rules and timing

2. Run a short focused test first
- example: only Koku economy / lines / zones
- or: errors / reveal / trap timing

3. Test one variant at a time
- example: first `Line +2 Koku`, then a separate test for storage cap

4. Define AI priorities (if I autoplay)
- `aggressive`, `income`, `capital rush`, `disruption`

## 11) First Step When You Are Ready

Send me the `# Simulation Start` block (even partially filled), and I will:
- fill in missing assumptions
- prepare `Turn 0` (Junbi + initial state)
- start the step-by-step simulation

## 12) Clarifications Discovered During Testing (Rulebook Cleanup Notes)

Purpose:
- This section stores clarifications that emerge during simulation, UI testing, or designer feedback when a rule was not explicit enough in the rulebook.
- These notes are temporary design clarifications and should later be reviewed and integrated into the official rules text.

How we use this section:
- When you correct me on a rule/application detail that was ambiguous or missing, I will append a new note here.
- Each note should describe:
  - what was unclear
  - the clarified behavior to use in simulation
  - whether it implies a future rulebook wording fix

### C-001 - Numbered cards do not require connection (unless card-specific rules say otherwise)

Observed ambiguity:
- It may be incorrectly assumed that all played cards must be connected to the clan chain / Daimyo.

Clarified simulation behavior:
- `Numbered` cards can be placed in any legal board position allowed by the current rules/timing, and they do **not** require connection by default.
- Connection / stacking / adjacency obligations apply only when explicitly required by the specific card type or effect.
- Some `Special / Retainer` cards may have constraints such as:
  - must be connected
  - must be stacked
  - must follow a specific placement condition

Rulebook cleanup impact:
- Add an explicit sentence in the placement rules to distinguish default placement rules for `Numbered` cards from card-specific constraints of `Special/Retainer` cards.

### C-002 - Each player has a personal player board; only one player is active per turn

Observed ambiguity:
- During UI/simulation testing, it may be unclear whether shared controls (for example `Koku -> Protection`) are global or tied to a specific player board.

Clarified simulation behavior:
- Each player has a **personal player board** with their own resources (`Koku`, Protection supply, Reserve, etc.).
- Actions such as resource conversion (`Koku -> Protection`) always apply to the **active player** (the player whose turn it is), unless an effect explicitly says otherwise.
- Multiple player boards may be visible at the same time for overview/inspection, but there is only **one active player** at a time.
- A UI may support a separate **focus/inspect** player board (for viewing another player's state) without changing the active turn player.

Rulebook cleanup impact:
- Add a short explicit note in the turn/action section that player resources are personal and actions resolve on the acting player's board by default.

### C-003 - Distinguish action scope: board-targeted actions vs player-board actions

Observed ambiguity:
- During simulation/UI testing, it may be unclear whether an available action depends on the selected board cell or is a general action on the active player's personal board.

Clarified simulation behavior:
- Actions should be understood by scope:
  - **Board-targeted actions**: require a legal target on the game board (often the currently selected cell).
  - **Player-board actions**: operate on the active player's resources (for example `Koku -> Protection`) and do not depend on the selected board cell unless explicitly stated.
  - **Global turn actions**: affect turn flow or simulator state (for example `End Turn`, `Reset Sandbox Match` in the tool UI).
- A selected board cell should not imply that every listed action is valid "on that cell."

Rulebook cleanup impact:
- Add wording (or examples) in the action flow / turn summary to distinguish target-based actions from resource-management actions on the player's board.

### C-004 - Turn-flow recap should include Emperor Visit and separate tool actions from game actions

Observed ambiguity:
- During simulator/UI testing, the "available actions" recap may be misleading if it mixes simulator/tool actions (for example reset) with actual in-game turn options, and if it omits key turn-flow options such as `Visit Emperor`.

Clarified simulation behavior:
- A turn recap should prioritize **gameplay actions** and show them by scope/timing, including turn-flow options (for example `Visit Emperor`, when applicable/implemented).
- Simulator/tool commands (for example `Reset Sandbox Match`) should not be listed as normal in-game actions in the same gameplay recap, or they must be clearly separated as tool/debug actions.
- `Visit Emperor` belongs to turn-flow/options recap (not a selected-cell action), and should be visible near other turn-flow items (such as refill / handoff context), even if not yet implemented in the current simulator phase.

Rulebook cleanup impact:
- Add a concise turn summary/checklist in the rulebook that clearly distinguishes:
  - turn-flow options (e.g. refill, Emperor visit timing)
  - board actions
  - player-board/resource actions
  - simulator/tool controls (if shown in testing tools)

### C-005 - The turn has 3 distinct phases, and the action recap should show only the current phase actions

Observed ambiguity:
- A generic "available actions" list can become noisy or misleading if it shows all possible actions at once, instead of what is legal in the current moment of the turn.

Clarified simulation behavior:
- The turn is modeled as **3 distinct phases**:
  - **Start phase**: start refill (draw to 3) and optional `Visit Emperor`
  - **Main phase**: primary and secondary gameplay actions
  - **End phase**: refill to 3, collect resources, pass turn
- The simulator UI (especially `AVAILABLE ACTIONS NOW`) should prioritize **only the actions available in the current phase**.
- Actions from other phases may be shown only as optional previews (for example collapsible sections), and they should be clearly marked as not currently available.
- Turn controls/buttons should reflect the current phase transition (`Start -> Main -> End -> Pass hand`) rather than implying that every turn always goes directly to handoff.

Rulebook cleanup impact:
- Add a compact turn-phase structure in the rulebook (Start / Main / End) and categorize actions by phase.
- Make explicit that some actions are timing-restricted to a specific phase and should not be treated as always available during the turn.

### C-006 - Player-board gameplay actions (convert/protect/build) are Main-phase actions

Observed ambiguity:
- When the simulator shows the player board at all times, it may look as if resource conversions or player-board gameplay actions are valid in `Start` or `End` phases as well.

Clarified simulation behavior:
- The player board is always visible for information, but gameplay actions on it should respect turn timing.
- Actions such as `Koku -> Protection`, `place Protection`, and (later) `build` should be treated as **Main-phase actions** unless a rule/effect explicitly allows otherwise.
- In `Start` and `End` phases, the player board may remain visible, but gameplay actions should be hidden/disabled or clearly marked as unavailable due to phase timing.

Rulebook cleanup impact:
- In the turn structure section, explicitly label which player-board/resource actions belong to the Main phase.

### C-007 - Daimyo can receive Protection tokens (up to 3)

Observed ambiguity:
- During simulator testing, Protection placement was initially blocked on `Daimyo`, but this conflicted with the intended rules.

Clarified simulation behavior:
- A player's `Daimyo` card **can receive Protection tokens**.
- The Daimyo can hold **up to 3 Protection** tokens.
- The simulator/UI should represent Daimyo Protection clearly (for example with a visible protection marker/count on the card).

Rulebook cleanup impact:
- Add an explicit rule in the Protection placement section stating:
  - whether Daimyo is a legal Protection target
  - the Daimyo-specific Protection limit (`3`)
  - how this interacts (if relevant) with other attached markers/buildings.

### C-008 - Castle/Capital transformations use 3 different connected source cards

Observed ambiguity:
- During simulator implementation, build logic was initially interpreted as using `3` tokens on the **same** selected card to build a Castle (and a direct `3 castles` player-count upgrade to Capital). This is not the intended rule.

Clarified simulation behavior:
- `Castle` and `Capital` are **transformations** based on `3` sources on **3 different cards**, connected to the player's Daimyo chain.
- `Castle` uses `3 Protection` tokens (including Protection on the Daimyo if present/eligible in the connected chain).
- `Capital` uses `3 Castles` (same transformation idea, using castles instead of protection tokens).
- The player must choose which `3` source cards are consumed.
- The resulting `Castle`/`Capital` is placed on a **Numbered** card.
- The simulator should show the `Castle`/`Capital` option only when the transformation is actually available; before that it should remain hidden in the main action controls.

Rulebook cleanup impact:
- Explicitly state that Castle/Capital transformations consume `3` sources on `3 different connected cards` (not `3` markers on one card).
- Clarify legal source types (including Daimyo Protection, if intended) and legal target card type (`Numbered`).
- Clarify whether/when Castle creation becomes mandatory when the available source set is all-numbered.

### C-009 - You cannot leave Main phase without playing, and end-hand size is constrained

Observed ambiguity:
- During simulator testing, it was possible to leave `Main` phase too early, even without playing any card, which does not match the intended turn flow constraints.

Clarified simulation behavior:
- A player cannot leave `Main` phase without playing at least one card (unless a future explicit rule/effect says otherwise).
- The end of `Main` should leave the player with:
  - `2` cards in hand, or
  - `1` card in hand only if the `1 Koku` last-card cost has been paid.
- The simulator should block the phase transition to `End` and show a clear message when these conditions are not met.

Rulebook cleanup impact:
- In the Main-to-End transition rules, explicitly state:
  - the "must play at least one card" condition
  - the allowed hand-count states at the end of Main
  - the last-card Koku payment requirement for ending Main with `1` card.

### C-010 - Castle uses 3 total Protection on the connected chain (not necessarily 3 different cards)

Observed ambiguity:
- During simulator testing, the Castle transformation was initially interpreted as requiring `3 Protection` on `3 different connected cards`.
- This conflicts with the intended rule when, for example, the Daimyo holds `+P2` and another connected card holds `+P1`.

Clarified simulation behavior:
- `Castle` requires **3 total Protection tokens** on the player's connected chain (the "chain of command" from the Daimyo).
- These `3` tokens do **not** need to be on `3 different cards`.
- Protection on the Daimyo counts normally (e.g. `Daimyo +P2` contributes `2` tokens).
- The Castle is placed on a legal `Numbered` target card in the connected chain.

Rulebook cleanup impact:
- Replace/clarify any wording that implies `3 different cards` for Castle token consumption.
- Explicitly say the requirement is based on **total Protection tokens on the connected chain**, not distinct-card count.

### C-011 - Capital build target flips if it is a face-up Numbered card

Observed ambiguity:
- During simulator implementation, it was unclear whether building a `Capital` on a selected `Numbered` target keeps the card face-up, requires choosing a face-down card, or flips the selected card.

Clarified simulation behavior:
- When building a `Capital` on the chosen target card:
  - if the target is a **face-up Numbered** card, it is **flipped face-down** and the Capital is built on it;
  - if the target is **already face-down**, the Capital is built directly.

Rulebook cleanup impact:
- In the Capital transformation section, explicitly describe the target-card orientation outcome (flip to face-down if currently face-up Numbered).

### C-012 - Mandatory Castle/Capital build blocks leaving Main phase

Observed ambiguity:
- During simulator testing, the phase-advance control could allow leaving `Main` even when a mandatory transformation (`Castle`/`Capital`) was available.

Clarified simulation behavior:
- If a mandatory `Castle` or `Capital` transformation is available, the player must resolve it before leaving `Main` phase.
- The simulator should block `Main -> End` transition and may hide the phase-advance button while the mandatory build is pending.

Rulebook cleanup impact:
- Explicitly state the mandatory timing/priority of Castle/Capital transformations relative to ending the Main phase.

### C-013 - Mandatory Castle trigger is not generic "3 Protection on chain"

Observed ambiguity:
- A generic rule like "Castle is mandatory when 3 Protection exist on the chain" is too broad and produces false positives (for example `Daimyo +P2` plus one other `+P1` source).

Clarified simulation behavior:
- `Castle` becoming mandatory depends on the specific trigger condition tied to **protected connected Numbered cards** (not just total Protection tokens anywhere on the chain).
- In practical simulator terms for the current interpretation:
  - the Castle mandatory trigger is checked using connected protected `Numbered` cards in the Daimyo chain;
  - generic Protection totals on non-numbered sources (e.g. Daimyo Protection) are not sufficient by themselves to force Castle.

Rulebook cleanup impact:
- Clarify the exact mandatory trigger for Castle (and separate it from the generic "available resources on chain" condition).
- Explicitly distinguish:
  - Castle **availability** (enough consumable resources on chain)
  - Castle **mandatory trigger** (specific pattern/condition on protected Numbered cards).

### C-014 - Market uses the same build-resource logic as Castle (and counts as a token in defense)

Observed ambiguity:
- Market build cost/trigger could be interpreted differently from Castle if the rule text is not explicit.

Clarified simulation behavior:
- `Market` uses the same resource logic as `Castle` for building in the current simulator interpretation (chain-based Protection consumption, not "3 tokens on one selected card").
- In defense, `Market` counts as a token (combat/defense resolution effects to be implemented later).

Rulebook cleanup impact:
- Explicitly state whether Market build cost/consumption follows the same chain-based token logic as Castle.
- Clarify the defensive value of Market ("counts as a token") in the combat/defense rules.

### C-015 - Building is not allowed in Imperial Zones and not allowed on Daimyo

Observed ambiguity:
- Build target restrictions (Imperial Zones / Daimyo) can be missed if they are not stated clearly.

Clarified simulation behavior:
- Building (`Market`, `Castle`, `Capital`) is **not allowed** in `Imperial Zones`.
- Building on the `Daimyo` card is **not allowed**.

Rulebook cleanup impact:
- Add an explicit list of build target restrictions, including:
  - Imperial Zone prohibition
  - Daimyo prohibition
  - any other target-type restrictions (e.g. face-up/down and Numbered requirements).

### C-016 - Protection converted from Koku must be placed before leaving MAIN phase

Observed ambiguity:
- The rules flow around `Convert Koku -> Protection` can be read as either:
  - "increase Protection supply and keep playing", or
  - "convert and then place those converted Protection tokens before ending the action phase."

Clarified simulation behavior:
- `Convert Koku -> Protection` is a `MAIN` phase action.
- Protection generated by that conversion must be **placed before leaving `MAIN`**.
- In simulator UX terms:
  - `MAIN -> END` is blocked while converted Protection placements remain pending;
  - the phase-advance button is hidden and replaced by a warning until they are placed.

Rulebook cleanup impact:
- Explicitly state whether converted Protection becomes a mandatory immediate/phase-bounded placement obligation.
- If yes, clarify whether the obligation applies to:
  - only the Protection generated by the current conversion action (current simulator interpretation), or
  - all Protection available in supply.

### C-017 - Reveal timing for own face-down cards is deferred to next turn start

Observed ambiguity:
- During tests, revealing your own face-down cards could happen immediately in `MAIN`, which conflicts with the intended timing.

Clarified simulation behavior:
- If the reveal target is an owned face-down card, reveal is queued and resolves at the player's next `START` phase.
- Immediate reveal placeholder actions can still be used for non-owned face-down interaction tests, but own-card reveal timing is deferred.

Rulebook cleanup impact:
- Clarify reveal timing windows, explicitly distinguishing:
  - own face-down reveal timing (deferred to next turn start),
  - other reveal interactions (if any) and their timing/cost constraints.

### C-018 - Reveal and Error-check actions are MAIN-phase only

Observed ambiguity:
- During simulator iteration, reveal/error placeholder actions could appear callable outside the intended action window.

Clarified simulation behavior:
- `Reveal` actions are activated only in `MAIN` phase.
- `Error check`/`Declare Error` actions are activated only in `MAIN` phase.
- Outside `MAIN`, these actions should not trigger from contextual shortcuts (e.g., `Shift + Right Click` on board cards).

Rulebook cleanup impact:
- In turn structure text, explicitly bind reveal/error windows to the `MAIN` phase action block.
- Keep START/END phase options separate from these secondary correction/reveal actions.

### C-019 - Optional simulator variant to allow intentional error placements

Observed ambiguity:
- In strict legality mode, players cannot intentionally create board errors for stress-testing error-fix/reveal flows.

Clarified simulation behavior:
- A configuration variant `allowIntentionalErrorPlacements` is available in Scenario Config.
- When enabled, face-up Numbered plays that would create row/column/zone duplicates are allowed (for testing).
- Other placement legality constraints remain unchanged.
- Action log/status should explicitly label these plays as intentional error placements.

Rulebook cleanup impact:
- Keep this option marked as a **simulator/testing variant**, not a default tabletop rule.
- If design decides to support deliberate error creation as gameplay, formalize timing/cost/limits in rules text.

### C-020 - Extra Protection placement is blocked when 3 connected Numbered protections force Market/Castle resolution

Observed ambiguity:
- During testing, once a player reaches the "3 connected Numbered protections" condition, it was unclear whether they can keep placing additional Protection before building.

Clarified simulation behavior:
- If a player has `3+` connected Protection tokens all on connected `Numbered` cards, and a legal `Market` or `Castle` target exists, placing additional Protection is blocked until one of those builds is resolved.
- Exception: if at least one connected Protection token is on `Daimyo` or `Retainer`, this specific lock does not trigger.

Rulebook cleanup impact:
- Explicitly distinguish:
  - generic Protection placement legality,
  - build-priority lock condition when Numbered-only connected protection threshold is reached.

### C-021 - Keyboard `E` uses hovered board target (fallback selected when no hover)

Observed ambiguity:
- Error-declare via keyboard could feel inconsistent with mouse rollover targeting.

Clarified simulation behavior:
- Keyboard `E` triggers `Declare Error` on the current keyboard target (`hovered` board cell first, then selected cell fallback).
- This aligns keyboard behavior with other hover-first shortcuts.

Rulebook cleanup impact:
- No core rules change; this is a simulator UX targeting convention and should remain documented as tool behavior.

### C-022 - Capital target does not need an existing Castle marker

Observed ambiguity:
- The simulator blocked Capital build with `Selected target must already have a Castle`, which conflicts with intended gameplay.

Clarified simulation behavior:
- `Capital` can be built on any owned connected:
  - face-up `Numbered` card (auto-flipped face-down on build), or
  - already face-down card.
- The target card does **not** need a pre-existing `Castle` marker.
- Cost/source rule remains unchanged: consume `3` connected castle sources.

Rulebook cleanup impact:
- In Capital build rules, separate clearly:
  - target eligibility (owned connected Numbered or face-down),
  - build source requirement (3 connected Castles consumed).

### C-023 - Hidden-info reveal details are masked in recaps/logs under Controlled mode

Observed ambiguity:
- Reveal placeholder and deferred-reveal logs can expose target coordinates/effects that are sensitive in fog-style playtests.

Clarified simulation behavior:
- In `Controlled` info mode, reveal-sensitive details are masked in `Round Recap` and `Action Log`.
- In `Open Info` mode or when local debug reveal is enabled, full reveal details are shown.
- This is a simulator visibility policy; gameplay resolution logic is unchanged.

Rulebook cleanup impact:
- No core rule change required.
- Keep as simulator UX/testing visibility rule for hidden-information sessions.

### C-024 - Retainer actions currently run in placeholder baseline mode

Observed ambiguity:
- Retainer cards need visual/action flow testing before all final effects are fully implemented.

Clarified simulation behavior:
- Retainer cards are now playable in a baseline placeholder mode:
  - `Action1`: simplified placement legality by retainer type (`place anywhere`, `place chained`, optional `overlap own`).
  - `Action2`: sacrifice placeholder (card is consumed/logged; full effect resolution is pending).
- Action selection remains exclusive (`A1` or `A2`) per played Retainer card.
- Logs explicitly mark retainer effects as placeholder.

Rulebook cleanup impact:
- Keep this as an implementation-stage simulator note.
- Final retainer effect text/rules will replace placeholder logic in later phases.

### C-025 - END phase uses two-step resolution with mandatory refill before handoff

Observed ambiguity:
- During tests, END handoff could occur without a clear visible refill step, and it was unclear when newly drawn end-turn cards should be visible.

Clarified simulation behavior:
- `END` is now resolved in two explicit steps:
  - Step 1: `Resolve End Phase` (mandatory refill to 3, then end income collection).
  - Step 2: `Pass Hand` to next player.
- Default runtime behavior auto-resolves Step 1 when entering `END`.
- If configuration `Auto resolve END on entry` is OFF, Step 1 stays manual and must be triggered via button.
- Newly drawn cards from END refill are visible in the END phase (same visual lock/highlight scheme used for START refill).
- If END refill draws `0` cards (hand already at 3+), no card is marked as newly drawn.
- Future card effects that trigger after END refill may increase hand size above 3 (rule-consistent).

Rulebook cleanup impact:
- Clarify END ordering explicitly:
  - refill-to-3 first,
  - then end effects/resources,
  - then handoff.

### C-026 - New cards from START/END refill are marked with a visual badge

Observed ambiguity:
- During refill steps it can be hard to distinguish previously-held cards from newly drawn cards.

Clarified simulation behavior:
- In both `START` refill view and resolved `END` refill view, newly drawn cards are marked with a `*` badge in the top-left card corner.
- On each player's first personal `START` in a new match, the opening setup hand is also treated as `new` for this UI badge, even if START refill draw is `0`.
- If refill draws `0`, no card gets the new badge.
- Retainer cards use near-standard brightness (no heavy darkening), to keep art/text readable during testing.

Rulebook cleanup impact:
- No tabletop rule change required.
- Keep as simulator UX convention for playtest readability.

### C-027 - Pending hand effects resolve before START refill

Observed ambiguity:
- Some card effects (for example Shinobi/Samurai placeholders during simulation) must alter hand size before the next turn refill.

Clarified simulation behavior:
- A pre-START hand-effect queue is available.
- Queued adjustments resolve at the target player's START, before refill-to-3:
  - negative value: discard from hand first,
  - positive value: draw first.
- START refill then runs on the updated hand count.
- Action Log records queueing and resolution details.

Rulebook cleanup impact:
- Clarify ordering for any hand-modifying delayed effects:
  - delayed hand effect resolution,
  - then START refill to 3.

### C-028 - Scenario config persists local view preferences

Observed ambiguity:
- Debug reveal/card visual mode were useful per-scenario but not always saved with setup.

Clarified simulation behavior:
- Scenario JSON now stores/loads:
  - `view.revealHiddenHandsOnPlayerBoards`
  - `view.cardGraphicMode`
- This is local simulator tooling, not gameplay state.

Rulebook cleanup impact:
- No rulebook impact; simulator configuration quality-of-life.

### C-029 - Imperial income requires connectivity to the Chain of Command

Observed ambiguity:
- During playtests, Imperial Zone income could be interpreted as "any owned Imperial top card", even if disconnected from the Daimyo chain.

Clarified simulation behavior:
- `+1 Koku` per Imperial Zone is awarded only when that Imperial card is:
  - owned by the player, and
  - connected to the player's Chain of Command (Daimyo-connected mask).
- Owned but disconnected Imperial cards do not grant Imperial income until reconnected.

Rulebook cleanup impact:
- In Economy/Income wording, explicitly state that Imperial income follows connected-chain validity (same connectivity principle used for chain-based scoring/control effects).

### C-030 - Start setup baseline is Daimyo `+P1` (with optional declared `+P2` starts)

Observed ambiguity:
- During simulator/debug iterations, sandbox setup started with extra Koku and loose Protection availability, which does not represent the intended baseline opening.

Clarified simulation behavior:
- Baseline setup starts with Daimyo `+P1` for each player.
- Optional experimental setup may assign `+P2` to selected starting seats/zones, but this must be declared before Turn 1.
- These are setup values, not in-turn generated resources.

Rulebook cleanup impact:
- Setup section should explicitly define default Daimyo starting Protection and how optional `+P2` starts are declared for tests/scenarios.

### C-031 - Gained Protection must be placed immediately

Observed ambiguity:
- In simulator flow, Protection could be interpreted as generic supply to use later, even when generated by an immediate procedure/effect.

Clarified simulation behavior:
- When Protection is gained through a turn procedure/effect (for example `Convert Koku`, `Error Fix` rewards), those gained tokens must be placed immediately when legal.
- `MAIN -> END` transition remains blocked while mandatory converted placements are pending.

Rulebook cleanup impact:
- Add a single explicit timing rule for gained Protection placement (immediate placement window and fallback behavior when no legal slot exists).

### C-032 - Koku storage cap is `5`

Observed ambiguity:
- Earlier simulator/rule iterations used storage cap `6`, creating mismatch with current test baseline.

Clarified simulation behavior:
- End-of-turn counting cap remains `max +5` from counting sources.
- Storage cap is `max 5` Koku; excess is discarded after income application.

Rulebook cleanup impact:
- Replace remaining storage-cap `6` references in active rules with storage-cap `5`.

### C-033 - Protection token pool cap is `6` per player

Observed ambiguity:
- Token economy did not clearly enforce per-player physical token cap in simulator baseline.

Clarified simulation behavior:
- Each player has a total Protection pool cap of `6` tokens.
- Conversion to Protection is blocked when this cap is already fully allocated.

Rulebook cleanup impact:
- Components/economy sections should explicitly state the per-player Protection pool cap and related conversion constraints.

### C-034 - `Chajin A1` has a once-per-turn usage limit

Observed ambiguity:
- The card text/appendix implies a per-turn limiter for `Chajin A1` draw action, but simulator baseline previously allowed repeated `A1` in the same turn when multiple Chajin cards were available.

Clarified simulation behavior:
- `Chajin A1` (`Draw 2`) is now limited to once per active turn.
- Additional `Chajin A1` attempts in the same turn are blocked with explicit status feedback.
- Counter resets at each new `START` for the active player.

Rulebook cleanup impact:
- Add explicit "once per turn" wording in the Retainer appendix/action timing section for `Chajin A1`.

### C-035 - AI autoplay must de-prioritize placeholder actions

Observed ambiguity:
- With partial `Reveal/Error` placeholder flows, AI scoring could over-prioritize non-progress actions, reducing practical usefulness of autoplay test runs.

Clarified simulation behavior:
- AI baseline scoring now treats placeholder `Reveal/Error` as low-priority compared with core turn progression actions.
- AI analysis still lists them as legal options, but they are no longer preferred in normal autonomous turn flow.

Rulebook cleanup impact:
- No rulebook change required.
- This is simulator-policy tuning for automated playtest quality while placeholder systems are incomplete.

### C-036 - AI batch controls are step-capped safety tools

Observed ambiguity:
- Long automatic runs can enter repetitive loops while some advanced effects remain placeholder.

Clarified simulation behavior:
- AI analysis panel now supports:
  - `AI Step (1 move)`,
  - `AI Auto Turn`,
  - `AI Auto Round`,
  - `AI N Moves`,
  - a configurable step cap.
- Step cap is a safety guard; batch actions stop early on no-legal-move/failure.

Rulebook cleanup impact:
- No rulebook impact; this is simulator automation tooling.

### C-037 - Chained Retainer placement can target empty cells adjacent to the chain

Observed ambiguity:
- During playtest, `Ashigaru A1` was blocked when placed on an empty cell orthogonally adjacent to the Daimyo (chain origin), because the simulator only accepted targets already marked as connected.

Clarified simulation behavior:
- For chained Retainer placement (`PlaceChained` / `PlaceChainedOverlapOwn`):
  - the target is legal if it is already connected to the player's chain, or
  - the target is an empty cell orthogonally adjacent to at least one connected chain cell (including Daimyo origin).
- This allows chained Retainers to extend the chain from the Daimyo as intended.

Rulebook cleanup impact:
- In Retainer placement wording, explicitly define chained placement as "on connected cells or empty orthogonally adjacent cells to the chain."

### C-038 - Samurai A2 is modeled as a queued one-block interrupt in simulator baseline

Observed ambiguity:
- Full reactive "interrupt window" timing is not yet represented in UI flow, but Samurai `A2` requires blocking an opponent special action.

Clarified simulation behavior:
- `Samurai A2` arms a queued interrupt against the next player's first Retainer action.
- When that Retainer action is attempted, it is blocked and not consumed.
- The interrupt expires after the intended target turn if unused.

Rulebook cleanup impact:
- No rulebook wording change required; this is a simulator timing policy until live reactive windows are implemented.

### C-039 - Ronin replacement returns replaced top card to owner hand when reconstructable

Observed ambiguity:
- Replacement effects can be interpreted as removing the target card entirely or returning it to owner resources.

Clarified simulation behavior:
- `Ronin A1` replacement returns the replaced top card to the original owner's hand when the card identity is reconstructable from board top metadata.
- If the replaced top cannot be reconstructed reliably, it is removed with explicit action log note.
- Any tokens/build markers on the replaced top are removed with that top card.

Rulebook cleanup impact:
- Add explicit replacement outcome wording (return to hand vs discard/remove, plus marker handling) in the Ronin action text.

### C-040 - Samurai A1 adjacent removal scope and deterministic priority

Observed ambiguity:
- During playtest, `Samurai A1` did not remove an adjacent enemy card in a legal scenario, because simulator priority could consume token-removal path first.
- Card scope wording needs to stay explicit: adjacent unprotected card can be any non-Daimyo top card.

Clarified simulation behavior:
- `Samurai A1` deterministic resolver now applies:
  - first: remove 1 adjacent unprotected top card (enemy first, then own if needed),
  - fallback: remove 1 adjacent protection token (enemy first, then own if needed).
- Removable card scope is any non-Daimyo adjacent top card (`Numbered`, `FaceDown`, `Retainer`) when unprotected.
- Token removal alternative includes tokens on adjacent Daimyo cards.

Rulebook cleanup impact:
- In Samurai `A1` text, keep explicit "adjacent unprotected card (non-Daimyo) OR adjacent token (including Daimyo token)" wording to avoid implementation ambiguity.

### C-041 - Ronin A2 compensation rule when stealable board tokens are fewer than 2

Observed ambiguity:
- During playtest, `Ronin A2` behavior around low-token tables was unclear: whether missing stolen tokens should reduce gain or be compensated.

Clarified simulation behavior:
- `Ronin A2` steals from opponent in-play cards first (board cards with protection tokens).
- No supply/reserve stealing for this action in current clarified baseline.
- Gain target stays `2`:
  - steals `2` -> gain `2`,
  - steals `1` -> gain `2` (1 direct compensation),
  - steals `0` -> gain `2` (2 direct compensation).
- Final gain is still capped by protection-token capacity.

Rulebook cleanup impact:
- Ronin `A2` text should explicitly define compensation behavior when fewer than `2` stealable board tokens exist.

### C-042 - Visit Emperor must execute full hand/discard reshuffle effect

Observed ambiguity:
- In simulator flow, `Visit Emperor` could appear available but only log usage without changing cards.

Clarified simulation behavior:
- `Visit Emperor` in START phase performs the full effect:
  - merge current hand + discard pile,
  - shuffle deterministically,
  - redraw `3` cards into hand.
- Effect remains `once per player` (`emperorUnused` toggle).

Rulebook cleanup impact:
- Keep explicit action text in the START phase section:
  - "Shuffle hand with discard pile, redraw 3 cards."

### C-043 - Numbered stacking is allowed only on own top cards (not opponent top cards)

Observed ambiguity:
- Legal move preview showed a face-up/down Numbered placement on an opponent occupied cell (stack target), which is not intended.

Clarified simulation behavior:
- Numbered cards cannot stack on opponent top cards.
- Numbered stacking (when allowed) is restricted to own top cards only.
- Occupied opponent cells remain invalid targets for Numbered placement.

Rulebook cleanup impact:
- In Numbered placement/stacking wording, explicitly state "stack only on own cards" to avoid overlap confusion with Retainer actions.

### C-044 - Capital arms endgame final cycle; game ends when turn returns to that same player

Observed ambiguity:
- Endgame timing after placing a `Capital` was not explicit in simulator behavior.

Clarified simulation behavior:
- Building `Capital` arms a final-cycle trigger on that player.
- Turn flow continues normally for other players.
- The game ends when hand/turn order returns to the same player who built that `Capital`.
- No additional active turn is started for that player after the return point; scoring can begin.

Rulebook cleanup impact:
- Add an explicit endgame sentence in the Shogun/Capital section:
  - "After Capital is placed, complete the table cycle and end the game when turn returns to that declaring player."

### C-045 - After endgame trigger, only Shogun players may spend Koku for reveals

Observed ambiguity:
- After Capital/endgame trigger, reveal spending rights were not explicitly restricted by player role.

Clarified simulation behavior:
- In the endgame resolution window, only players currently considered `Shogun` may spend gained `Koku` to reveal cards.
- Non-Shogun players cannot perform Koku-based reveal spending after endgame has been triggered.

Rulebook cleanup impact:
- Add a short explicit clause in the endgame/scoring chapter defining post-trigger reveal spending eligibility (`Shogun-only`).

### C-046 - Shinobi A1 cannot remove face-up Numbered cards

Observed ambiguity:
- During testing, Ninja/Shinobi removal was interpreted as if it could target a face-up Numbered card.

Clarified simulation behavior:
- `Shinobi A1` removable targets are only:
  - a `Retainer` top card, or
  - a `FaceDown` top card.
- Face-up `Numbered` cards are not legal targets for `Shinobi A1`.
- Any tokens/build markers on the removed legal target are removed together with that target card.

Rulebook cleanup impact:
- Keep explicit wording in Retainer appendix/action text:
  - "Kill and remove 1 Special (Retainer) + any token on it OR 1 face-down card."
  - Add parenthetical clarification: "face-up Numbered cards are not valid for this action."

### C-047 - Numbered cards cannot be stacked on top of Retainer cards

Observed ambiguity:
- During testing, Numbered placement was allowed on a Retainer top card (example: Ronin), which is not intended in the current simulator baseline.

Clarified simulation behavior:
- Numbered cards may not be stacked on a Retainer top card.
- Numbered stacking remains limited to legal non-Retainer owned tops (subject to all other blockers).
- Retainer overlap/replacement interactions are handled by Retainer action rules, not by Numbered placement.

Rulebook cleanup impact:
- In Numbered placement/stacking text, add explicit sentence:
  - "Numbered cards cannot be placed on top of Retainer cards."

### C-048 - MAIN -> END gate is hand-floor based, not "must have played at least 1 card"

Observed ambiguity:
- During testing, leaving MAIN after reducing hand to 2 via discard/tool flow was blocked by an old hard check ("play at least 1 card this turn").

Clarified simulation behavior:
- MAIN phase closure is gated by hand-floor legality:
  - hand must be `<= 2`, or `1` only when paid last-card condition is satisfied.
- There is no additional universal requirement to have played at least one card if the current hand-floor and other mandatory gates are satisfied.

Rulebook cleanup impact:
- In turn-flow/phase-exit wording, replace "must play at least 1 card" with explicit hand-floor rule as the gating condition.

### C-049 - Error declaration baseline: duplicate Numbered flips face-down and grants +1 Protection

Observed ambiguity:
- Error declaration existed in flow/UI, but correction/reward behavior was not concretely defined in simulator runtime.

Clarified simulation behavior:
- During `MAIN`, declaring error on a valid duplicate face-up `Numbered` target applies immediate correction:
  - target flips to `FaceDown` (hidden identity retained for future reveal),
  - active player gains `+1 Protection` as effect reward,
  - gained Protection enters pending placement flow and must be placed before leaving `MAIN`.
- If no duplicate exists for the selected Numbered target, declaration is blocked.

Rulebook cleanup impact:
- Add explicit error-correction outcome text:
  - "duplicate Numbered is corrected by flipping face-down; reward token is granted and must be placed immediately."

### C-050 - Reveal behavior split: own face-down deferred, opponent face-down immediate (if identity tracked)

Observed ambiguity:
- Reveal action timing differed between own and opponent face-down cards in playtest expectations.

Clarified simulation behavior:
- In `MAIN`:
  - own face-down reveal is queued and resolves at the owner's next `START`,
  - opponent face-down reveal resolves immediately when hidden identity is tracked.
- If hidden identity is not tracked for the target, reveal is rejected with explicit status.

Rulebook cleanup impact:
- Clarify reveal timing and tracking requirements in reveal section:
  - include own-vs-opponent timing and fallback when identity data is unavailable.

### C-051 - Imperial Numbered overlap restriction and anti-stack spam overlap priorities

Observed ambiguity:
- In playtests, Numbered overlap chains were over-used (including repeated overlap on a single cell), and Imperial overlap legality for Numbered-on-Numbered was unclear.

Clarified simulation behavior:
- Numbered cards in Imperial Zone cells cannot be overlapped by other Numbered cards.
- Retainer overlap/replacement interactions remain legal in Imperial Zones according to Retainer rules.
- AI overlap tuning (same-clan self-stack control):
  - overlap on own stack depth `>=3` is strongly de-prioritized (`PRI-3`),
  - first overlap using a face-down Numbered is strongly de-prioritized (`PRI-3`),
  - first-layer own face-down -> face-up overlap is moderately preferred (`PRI-2`).

Rulebook cleanup impact:
- In Numbered placement/stacking section, add explicit Imperial restriction:
  - "Numbered cards in Imperial Zones cannot be overlapped by other Numbered cards."
- Keep/clarify that Retainer overlap/replacement is governed by Retainer action text, including Imperial interactions where legal.

### C-052 - Final scoring formula and multi-Shogun reveal window

Observed ambiguity:
- Final scoring breakdown and post-trigger reveal eligibility were not fully explicit together in one endgame reference.

Clarified simulation behavior:
- Final scoring components:
  - `+1` per face-up card in play (including Daimyo),
  - `+1` per completed zone,
  - `+1` per completed line,
  - `+1` per controlled Imperial zone,
  - `+1` per Castle,
  - `+2` per Capital,
  - `+4` for Shogun status.
- Endgame trigger remains tied to the first Capital/final-cycle arming player.
- Multiple players can still be in `Shogun` status.
- In the post-trigger reveal window, all Shogun players may spend Koku for reveals; non-Shogun players may not.

Rulebook cleanup impact:
- Add explicit scoring bullet list in endgame/scoring section.
- Add explicit sentence that multiple Shogun players are possible, and reveal spending after trigger is Shogun-only for all eligible Shogun players.

### C-053 - Endgame trigger player is not automatically winner; winner is decided by final points

Observed ambiguity:
- Endgame completion message could be interpreted as if the Capital trigger player is automatically the winner.

Clarified simulation behavior:
- The player who arms/returns the final cycle is the trigger reference for game end timing.
- Winner is determined by final points after game-over, using the configured scoring formula.
- Tie on top score is allowed and logged as shared winners.

Rulebook cleanup impact:
- In endgame chapter, separate clearly:
  - trigger/timing of game end,
  - winner determination by final scoring.

### C-054 - Clan special card is a single unique card instance per player

Observed ambiguity:
- The yellow star marker could be interpreted as "all cards of that type" instead of "one unique special card instance".

Clarified simulation behavior:
- Each player deck contains exactly **one** clan-special card instance (marked `*`).
- `*` travels with that card instance across deck/hand/discard/board.
- `*` is not a type marker for all cards with the same code.

Rulebook cleanup impact:
- Add one explicit sentence in deck setup/card identity:
  - "Each Daimyo has one unique special Retainer card instance in the deck."

### C-055 - Seed-sweep batch analysis export for fairness / first-seat advantage

Observed ambiguity:
- Manual single-match inspection is not enough to evaluate seat-order advantage and rank drift.

Clarified simulation behavior:
- Simulator includes a seed-sweep batch runner:
  - run one full AI match per seed in `[seedStart..seedEnd]` (inclusive),
  - export per-match CSV, aggregate markdown summary, and aggregate JSON,
  - track winner counts by seat and clan, seat-1 win rate, average rank/score/koku, and rank-change metrics.

Rulebook cleanup impact:
- No direct rules text change required.
- Add testing appendix note recommending seed-sweep analysis before balance conclusions.

### C-056 - Retainer AI priorities are now context-aware (A121..A162 practical subset)

Observed ambiguity:
- Retainer autoplay previously looked too flat (mostly base card-play weight), with weak differentiation by board context.

Clarified simulation behavior:
- AI now applies contextual scoring keys for Retainer actions (runtime TOML-driven), including:
  - `Sam` A1/A2 disruption/interruption context,
  - `Ash` A1 removal pressure + A2 filtering triggers,
  - `Cha/Tea` A1/A2 tempo timing and hand/deck context,
  - `Soe` A1 overlap disruption context + A2 top-discard value class,
  - `Shi` A1 target-value context + A2 disruption timing,
  - `Ron` A1 replacement-value context + A2 token-swing timing.
- These keys are logged with document tags (`[Axxx]`) in AI choice traces.
- Trap-only timing windows (`Shi/Ron` trap-mode specific rules) remain partial and are still tracked as pending.

Rulebook cleanup impact:
- No immediate core-rule text change required.
- Keep explicit "simulator policy vs pending trap-window final wording" note in testing appendix.

### C-057 - AI Analysis breakpoints for rule-tag frequency in seed sweeps

Observed ambiguity:
- It was hard to quantify how often a specific strategy rule/tag (for example `A180`) was actually used across large sweeps.

Clarified simulation behavior:
- AI Analysis now includes a closed-by-default `Breakpoints` tree for rule-tag counters.
- Up to 6 tags can be configured (`max 5 chars` each, e.g. `A180`).
- Empty slots are ignored.
- Counters are computed from AI chosen-rule usage tracking (not only from visible logs), so they work in fast batch mode too.
- For each configured tag:
  - `Hits` = total occurrences across matches,
  - `Match %` = matches where tag appeared at least once / total matches,
  - `Avg hit/match` = `Hits / total matches`.

Rulebook cleanup impact:
- No direct rule text change.
- Testing appendix should recommend breakpoint counters for verifying strategy frequency assumptions.
