# Sengoku v25 - Retainer Actions Matrix

Purpose:
- Single implementation-ready reference for Retainer action text and behavior mapping.
- Cross-check for simulator logic and card-behavior consistency.

Primary source:
- `AI/v25/RulesV25-Final.md` (general rules + appendix).

Normalization note:
- This matrix uses the printed Retainer wording normalized from `data.json`, so tag placeholders are expanded into plain rules text.
- Examples: `special` -> `Retainer`, `numbered` -> `Numbered`, `covered` -> `face-down`, `protected` -> `protected`.

## 1) Global Retainer Rules (v25)
1. Each Retainer has exactly 2 Order Actions (`A1` / `A2`).
2. When used, choose and resolve exactly 1 action.
3. Retainer Order Actions are separate from Turn Procedures (`Reveal`, `Convert Koku`, `Build`, `Error Fix`).
4. `[PLACE_CHAINED]` means `near your chain`: orthogonally adjacent to your Chain / Chain of Command.
5. Some Retainers may be used as traps (`[TRAP]`) depending on card text/timing.
6. Remove/replace-style effects cannot target a protected top card unless a rule/card explicitly says otherwise.

## 2) Action Categories (normalized for code)
- `PLACE_ANYWHERE` -> `[PLACE]` with no chain requirement, but still limited by the printed target text.
- `PLACE_CHAINED` -> `[PLACE_CHAINED]`
- `SACRIFICE` -> `[DISCARD]`
- `OVERLAP` -> `[COVER]`
- `TRAP_MODE` -> `[TRAP]`
- `REACTION` -> reactive opponent-turn interrupt window

## 3) Retainer Matrix (current base set)

| Card | Deck Code | A1 Tags | A1 Summary | A2 Tags | A2 Summary | Notes |
|---|---|---|---|---|---|---|
| Samurai | `Sam` | `PLACE_CHAINED`, `OVERLAP` | Place near own chain or cover own-clan card; then kill 1 adjacent unprotected card or remove 1 Token or 1 Market | `DISCARD`, `REACTION` | Cancel a declared Retainer action before it resolves; discard that card too | Cannot block Trap effects |
| Ashigaru | `Ash` | `PLACE_CHAINED`, `OVERLAP` | Place near own chain or cover own-clan unprotected Numbered card; kill up to 2 adjacent unprotected Numbered or face-down cards | `DISCARD` | Draw 4, keep 1, return the rest together to top/bottom of deck | Reference target is own-clan Numbered only |
| Chajin | `Cha` | `DISCARD` | Draw 2 cards (max 1 use of this action per turn) | `DISCARD` | Draw 1; if it is a Retainer and is played immediately, bonus becomes 3 | Per-turn limiter on A1 |
| Sohei | `Soe` | `PLACE_ANYWHERE`, `OVERLAP` | Place on a Sohei, unprotected Numbered, or face-down card of any Clan | `DISCARD` | Retrieve top discard card to hand | No chain requirement; printed target text still limits placement |
| Shinobi | `Shi` | `DISCARD` | Remove from map 1 Retainer and any Token on it, or 1 face-down card | `DISCARD`, `TRAP_MODE` | Spy hand, force 2 discards, then delayed end-turn draw +1 | Trap affects revealer |
| Ronin | `Ron` | `PLACE_ANYWHERE` | Replace own or any Clan's unprotected top non-Ronin card; return that card, then discard/return the rest of the stack | `DISCARD`, `TRAP_MODE` | Steal up to 2 Tokens from cards of other Clans, max 1 per Clan, rest from supply | No chain requirement; trap hits revealer first when applicable |

## 3b) Target Interaction Matrix

Interpretation rules:
- `any card` means any valid top card for that specific action text; it is not a global override.
- Unless action text says otherwise, `Daimyo` is never a removable/replaceable card target.
- `Protected` means any top active state with a Protection token, Market, Castle, or Capital.

| Action | Numbered (face-up) | Face-down | Retainer | Daimyo | Protected target |
|---|---|---|---|---|---|
| `Sam A1` remove card | Yes (adjacent, unprotected) | Yes (adjacent, unprotected) | Yes (adjacent, unprotected) | No | No |
| `Sam A1` remove token/Market | Yes | Yes if token exists | Yes | Yes if legal target exists | Yes, explicit exception |
| `Ash A1` remove card | Yes (adjacent, unprotected) | Yes (adjacent, unprotected) | No | No | No |
| `Soe A1` overlap | Yes (if unprotected) | Yes (if unprotected) | Only `Sohei` top (if unprotected) | No | No |
| `Shi A1` remove card | No | Yes | Yes | No | Yes, explicit exception by printed text |
| `Ron A1` replace | Yes (if unprotected top and non-Ronin) | Yes (if unprotected top and non-Ronin) | Yes (if unprotected top and non-Ronin) | No | No |
| `Ron A2` steal token | N/A | N/A | N/A | N/A | Token required |

## 4) Locked V25 Clarifications Relevant to Implementation
1. `Shinobi` and `Ronin` trap effects target the revealer first whenever the printed effect allows it.
2. Allied players may not Reveal each other's face-down cards unless a rule/card explicitly allows it.
3. Gained Protection must be placed immediately if legal; otherwise it is discarded to supply.
4. `Market = 2 Protection`, `Castle = 3 Protection`.
5. `Ronin A1` target must be the unprotected top non-Ronin card in that space.
6. `Ronin A1` leaves Ronin in the same space as the replacement card.
7. If `Ronin A1` returns cards, each returned card goes to its owner's hand.

## 5) Manual-writing caution
- This matrix is a technical/behavior document.
- It is useful for consistency checks, but `AI/v25/RulesV25-Final.md` remains the wording authority.

