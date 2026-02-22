# Sengoku - Differences V22 vs V24.1 Update
_Compared files: `AI/rulesV22.md` and `AI/rulesV24-update.md`_

## Scope
- This document lists the main rules/mechanics differences between V22 and V24.1 Update.
- It also includes differences clarified during this conversation history (editorial + terminology decisions applied in v24 docs/play docs).

---

## 0) Newly Promoted Rules in V24.1
- **Hand-floor payment rule**:
  - Play down to 2 cards in hand.
  - To play the last card (go to 1), pay **1 Koku**.
- **Face-down in center/Imperial Zones**:
  - Face-down cards are now explicitly forbidden in Imperial Zones.
- **Face-down overlap expansion**:
  - Face-down placement is now allowed on top of Retainer/Special cards when stacking is legal.
- **Koku storage cap reduced**:
  - From 9 to **6**.
- **Capital score increased**:
  - Standard and Duels: Capital value raised from +2 to **+3**.
- **Error-fix reward flow updated**:
  - +1 Protection token per corrected Error.
  - Token must be placed immediately on a legal face-up map card.
  - If no legal map slot exists: park on Daimyo reserve (max 3); if full, lose/discard that token.
- **Immediate error correction clarified**:
  - Before turn handoff, opponents may call illegal placement.
  - Acting player corrects immediately and may switch to another legal card/play.
  - If they switch card, the originally attempted illegal card is **not** lost.
- **Building progression tightened**:
  - If 3 connected Protection tokens exist and a legal connected Numbered destination exists, conversion is mandatory.
  - Destination can be any eligible connected Numbered card (not necessarily one of the source-token cards).
- **Castle limit handling clarified**:
  - If conversion would create a 4th Castle, relocate one existing Castle to a legal connected destination.
  - If no legal relocation exists, conversion does not resolve and tokens remain.
- **Setup/Junbi staging clarified**:
  - Daimyo is staged beside Player Board during deck setup and placed on the Game Board during Junbi.
- **Mode geometry backlog formalized**:
  - 5x5 (The Duel) and 9x9 (The Grand Campaign) starting coordinates/zone geometry are explicitly tracked as pending definitions in NOTE TO TEST/ADD.

---

## 1) Core System Changes
- **Currency model changed**:
  - V22 uses generic/honour/power token language (`AI/rulesV22.md:367`, `AI/rulesV22.md:374`).
  - V24 explicitly splits resources into **Koku (currency)** and **Protection tokens (map resource)** (`AI/rulesV24-update.md:304`, `AI/rulesV24-update.md:337`, `AI/rulesV24-update.md:343`).
- **Economy conversion added/standardized**:
  - V24: `2 Koku -> 1 Protection token` (`AI/rulesV24-update.md:347`, `AI/rulesV24-update.md:368`).
  - This rate is not formalized as such in V22.
- **Koku cap formalized and tightened**:
  - V24.1: explicit `max 6 Koku`.
  - V22 has token-limit language but not this Koku economy model.

---

## 2) Buildings and Combat Evolution
- **Siege Tower subsystem removed from core V24**:
  - V22 has full tower evolution and attack thresholds (`AI/rulesV22.md:415`, `AI/rulesV22.md:426`, `AI/rulesV22.md:527`).
  - V24 replaces that path with card-effect attacks and building progression without towers (`AI/rulesV24-update.md:471`, `AI/rulesV24-update.md:400`).
- **Market introduced as a core building in V24**:
  - V22 has no Market building chapter.
  - V24 adds Market in components and progression (`AI/rulesV24-update.md:73`, `AI/rulesV24-update.md:400`, `AI/rulesV24-update.md:423`).
- **Capital track simplified**:
  - V22 component/rules allow up to 2 capitals (`AI/rulesV22.md:66`, `AI/rulesV22.md:503`).
  - V24 uses single active capital path for Shogun progression (`AI/rulesV24-update.md:75`, `AI/rulesV24-update.md:461`).

---

## 3) Shogun and Endgame Logic
- **Shogun condition normalized**:
  - V22 contains internal conflict (2 capitals vs 3 capitals) (`AI/rulesV22.md:706`, `AI/rulesV22.md:556`, `AI/rulesV22.md:573`).
  - V24 sets trigger to **1 connected Capital** (`AI/rulesV24-update.md:628`).
- **Anchor/final-cycle behavior defined in V24**:
  - V24 adds anchor re-declare/full rotation rule (`AI/rulesV24-update.md:631`, `AI/rulesV24-update.md:645`).
  - V22 leaves this ambiguous (explicit questions remain).
- **Tie-break clarified in V24**:
  - V24: highest remaining Koku on the Player Board, then shared victory.
  - This is now the same tie-break logic in both Standard and Duels.
  - V22 tie-break is uncertain and appears only in Q/A notes (`AI/rulesV22.md:54`, `AI/rulesV22.md:55`).

---

## 4) Setup and Turn Flow
- **Junbi setup changed**:
  - V22 Junbi includes placing first Numbered card next to Daimyo (`AI/rulesV22.md:755`, `AI/rulesV22.md:759`).
  - V24 Junbi is Daimyo-placement-only; no initial numbered placement (`AI/rulesV24-update.md:697`, `AI/rulesV24-update.md:698`).
- **Daimyo setup staging clarified**:
  - V24 now states Daimyo is kept beside the Player Board during deck preparation and placed on the Game Board during Junbi.
- **Turn phases rationalized**:
  - V22 has draw-phase ambiguity (start + end confusion) (`AI/rulesV22.md:662`, `AI/rulesV22.md:688`, `AI/rulesV22.md:697`).
  - V24 defines explicit 3-section structure and timing boundaries (`AI/rulesV24-update.md:588`, `AI/rulesV24-update.md:605`).
- **Hand-floor clarified**:
  - V24.1 uses paid-last-card logic: stop at 2, pay 1 Koku to play the last card.
  - V22 text conflicts around “leave 2 cards”.
- **Deck exhaustion rule updated**:
  - V24 differentiates Standard reshuffle vs Expert Emperor flow (`AI/rulesV24-update.md:614`, `AI/rulesV24-update.md:615`, `AI/rulesV24-update.md:570`).
- **Immediate error-call timing clarified**:
  - V24 uses explicit "before turn handoff" timing and immediate correction without reward.

---

## 5) Board and Control Model
- **Board size for Duels changed**:
  - V22 duels references 4x4 (`AI/rulesV22.md:133`, `AI/rulesV22.md:794`).
  - V24 uses 5x5 Duels board (`AI/rulesV24-update.md:131`, `AI/rulesV24-update.md:717`).
- **Imperial central area formalized in V24**:
  - V24 defines 4 Imperial Zones, income + restrictions (`AI/rulesV24-update.md:138`, `AI/rulesV24-update.md:139`, `AI/rulesV24-update.md:394`, `AI/rulesV24-update.md:431`).
  - V22 uses different “special zones/bridge” language without this finalized standard model.
- **5x5 / 9x9 geometry status made explicit**:
  - V24 now marks 5x5 and 9x9 starting-coordinate and zone-geometry definitions as pending backlog items.
- **Control using top visible layer explicitly codified**:
  - V24 repeatedly enforces top-layer control checks (`AI/rulesV24-update.md:148`, `AI/rulesV24-update.md:660`).
  - V22 had this as a major ambiguity area.

---

## 6) Face-down / Reveal / Trap Framework
- **New explicit face-down subsystem in V24**:
  - Numbered placeholders + trap retainers + reveal timing (`AI/rulesV24-update.md:223`, `AI/rulesV24-update.md:224`, `AI/rulesV24-update.md:597`).
  - V22 does not define this as a complete formal subsystem.
- **Center restriction added in V24.1**:
  - Face-down cards are not allowed in Imperial Zones.
- **Overlap expansion in V24.1**:
  - Face-down placement can overlap Retainer/Special cards when legal.
- **Reveal (Bribery) cost and effects standardized**:
  - V24 fixes reveal at `K3` and integrates with trap resolution (`AI/rulesV24-update.md:367`, `AI/rulesV24-update.md:597`).

---

## 7) Alliances and Emperor (Expert Mode Refactor)
- **Alliances moved to Expert-mode framework**:
  - V22 presents alliances as baseline multiplayer chapter (`AI/rulesV22.md:579`).
  - V24 scopes alliances to Expert mode and player-board conditions (`AI/rulesV24-update.md:524`, `AI/rulesV24-update.md:530`, `AI/rulesV24-update.md:546`).
- **Alliance marker redefined as protection-token marker**:
  - V24 formalizes marker behavior and removals (`AI/rulesV24-update.md:534`, `AI/rulesV24-update.md:535`).
- **Visit the Emperor rewritten**:
  - V22: tribute action with unresolved once/game vs once/turn conflict (`AI/rulesV22.md:633`, `AI/rulesV22.md:649`, `AI/rulesV22.md:654`).
  - V24.1: marker-based once-per-match right with two explicit timings:
    - proactive window only at start of your turn (after refill, before first card),
    - if deck exhausts during a required draw, perform normal reshuffle and lose Emperor right if still unused (`AI/rulesV24-update.md:565`, `AI/rulesV24-update.md:577`, `AI/rulesV24-update.md:589`).

---

## 8) Scoring Differences
- **Connected-only scoring explicitly enforced in V24**:
  - V24 excludes disconnected cards/structures from score (`AI/rulesV24-update.md:669`, `AI/rulesV24-update.md:670`).
  - V22 leaves this as a question point (`AI/rulesV22.md:742`).
- **Daimyo rank points removed from V24 standard score block**:
  - V22 includes `+1 per Daimyo rank` (`AI/rulesV22.md:730`).
  - V24 standard scoring block does not include that line (`AI/rulesV24-update.md:651`-`AI/rulesV24-update.md:657`).
- **Expert bonus added in V24**:
  - `+1` if Emperor reshuffle right unused (`AI/rulesV24-update.md:657`).
- **Capital value increased in V24.1**:
  - Capital score is now +3 (Standard and Duels).

---

## 9) Duels (2P) Redesign
- **Seppuku special rule removed from active Duels ruleset**:
  - V22 includes Seppuku (`AI/rulesV22.md:818`).
  - V24 Duels uses same core Koku/protection framework as standard (`AI/rulesV24-update.md:747`).
- **Duels tie-break explicitly defined in V24**:
  - Duels now follows the same global tie-break: remaining Koku on Player Board -> shared victory.

---

## 10) Documentation/Editorial Differences (from conversation history)
- **Terminology normalization**:
  - “Imperial Spaces” standardized to “Imperial Zones” in v24 player-facing material.
- **Play guide gained explicit mini clarifications**:
  - deck-runout handling,
  - tie-break wording,
  - quick Koku formula,
  - clearer Reveal wording.
- **V22 ambiguity sections replaced by rule assertions in V24**:
  - V22 has extensive `QUESTION:` blocks throughout.
  - V24 converts many of those into concrete rules text.

---

## 11) Important Note
- `AI/rulesV24-update.md` still contains an internal TODO block (`# NOTE TO TEST/ADD:`), so the file is richer than V22 but not fully “clean final print” yet.
