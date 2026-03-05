# Rules V24 - Proposed Wording Updates (from Simulator Clarifications)

Purpose:
- Keep `RulesV24.md` unchanged while collecting concrete wording updates discovered during simulator implementation and playtest feedback.
- Source alignment: `AI/SIMULATION.md` clarifications (`C-001+`), `AI/TURN_FLOW_RECAP_V24.md`, and runtime behavior in the simulator.

## Priority A (high impact on gameplay correctness)

1. Imperial income connectivity
- Proposed wording:
  - "Each Imperial Zone grants `+1 Koku` only if its top controlled card is connected to your Chain of Command."
- Why:
  - Avoids interpretation that disconnected Imperial ownership still scores.
- Source clarification:
  - `C-029`.

2. Immediate placement of gained Protection
- Proposed wording:
  - "Protection gained during turn procedures/effects (for example conversion, error rewards, card effects) must be placed immediately when legal."
  - "A player cannot close MAIN while mandatory gained-Protection placements are pending."
- Why:
  - Removes ambiguity between "supply later" vs immediate board placement timing.
- Source clarifications:
  - `C-031`, `C-016`.

3. Main-phase exit gates (minimum explicit list)
- Proposed wording:
  - "To leave MAIN: at least one card must have been played this turn; hand-floor/last-card payment must be legal; no pending mandatory Protection placement; no pending mandatory build."
- Why:
  - Makes turn closure deterministic and simulator/test friendly.
- Source clarifications:
  - `C-009`, `C-012`.

4. Mandatory Castle trigger condition
- Proposed wording:
  - "Castle is mandatory only when the trigger condition is met: at least three connected protected Numbered cards in your Chain of Command."
  - "This is distinct from generic total chain protection."
- Why:
  - Prevents over-triggering Castle obligation.
- Source clarifications:
  - `C-013`.

5. Capital target legality
- Proposed wording:
  - "Capital can be built on a legal connected Numbered target; if face-up, it is flipped face-down during build. A pre-existing Castle marker on that target is not required."
- Why:
  - Resolves mismatch found in simulator and user tests.
- Source clarifications:
  - `C-011`, `C-022`.

5b. Imperial overlap restriction for Numbered cards
- Proposed wording:
  - "In Imperial Zones, Numbered cards cannot be overlapped by other Numbered cards."
  - "Retainer overlap/replacement remains governed by Retainer action rules."
- Why:
  - Prevents repeated Numbered stack spam in Imperial cells and aligns simulator legality with playtest intent.
- Source clarification:
  - `C-051`.

5c. Final scoring list + multi-Shogun post-trigger reveal clause
- Proposed wording:
  - "Final scoring grants: +1 per face-up card in play (including Daimyo), +1 per completed zone, +1 per completed line, +1 per controlled Imperial zone, +1 per Castle, +2 per Capital, +4 for Shogun."
  - "Multiple Shogun players can exist."
  - "After endgame trigger, Koku-for-reveal spending is allowed only to players in Shogun status (all eligible Shogun players)."
- Why:
  - Consolidates scoring and post-trigger eligibility in one deterministic rule block.
- Source clarification:
  - `C-052`.

## Priority B (economy/setup consistency)

6. Setup baseline
- Proposed wording:
  - "Default setup: each Daimyo starts with `+P1`."
  - "Optional experimental starts (`+P2` on selected seats/zones) must be declared before Turn 1."
- Why:
  - Prevents debug-start values from being misread as core rules.
- Source clarification:
  - `C-030`.

7. Koku cap wording lock
- Proposed wording:
  - "Counting gain cap remains `max +5` per collection."
  - "Storage cap is `max 5 Koku`; excess is discarded."
- Why:
  - Ensures one consistent cap reference.
- Source clarification:
  - `C-032`.

8. Protection pool cap wording lock
- Proposed wording:
  - "Each player has a total Protection token pool cap of `6`."
  - "Conversion is blocked when no free Protection capacity remains."
- Why:
  - Aligns component economy with simulator limits.
- Source clarification:
  - `C-033`.

## Priority C (retainer/action appendix precision)

9. Chajin A1 limiter
- Proposed wording:
  - "Chajin A1 (draw-2 action) can be used at most once per turn."
- Why:
  - Text intent exists but needs explicit enforcement sentence.
- Source clarification:
  - `C-034`.

10. Retainer appendix implementation notes (temporary)
- Proposed wording:
  - Add explicit target/sequence details where current text is compact (Ronin stack replacement order, Shinobi A2 exact discard workflow, trap timing windows).
- Why:
  - These are the current highest-friction points for deterministic simulator implementation.
- Source:
  - `AI/RETAINER_ACTIONS_MATRIX_V24.md` open items.

## Not rulebook changes (simulator-only)

- AI placeholder-action de-prioritization (`C-035`).
- AI autoplay step caps and batch controls (`C-036`).
- Scenario/view persistence fields (`C-028`).
