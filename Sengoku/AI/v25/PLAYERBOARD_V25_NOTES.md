# Sengoku - Playerboard V25 Notes
_Working component notes. Playerboard text must match the rulebook._

Purpose:
- Collect playerboard-facing information for the V25 redesign.
- Keep playerboard wording aligned with `RulesV25-Final.md`.
- Separate current/old board observations from intended V25 updates.

---

## 1) Rulebook Alignment Principle

- Anything printed on the playerboard or game board must also be supported by the manual.
- The playerboard may show short reminders, icons, values, and clan-specific rewards.
- The manual must explain the rules behind those reminders.
- Variable values printed on playerboards, especially Alliances and Destiny Path, should be treated as component-authoritative and referenced by the manual.

---

## 2) Main Round Reminder Panel

Current V24-style panel observed:

```text
Playing Round

BEGINNING:
Draw up to 3 Cards

WITHIN THE TURN:
Play down to 1 or 2 Cards in hand
Place protections on cards
Build Castles, Capitals or other buildings

OPTIONAL:
Fix Errors spotted
Reveal facedown cards
Make/Break Alliances
Visit the Emperor

END OF THE TURN:
Draw up to 3 Cards
Collect the Resources
and Pass the Turn
```

V25 problems with the current wording:
- `Visit the Emperor` is no longer a generic optional action during the turn.
- `Draw up to 3` should probably become `Refill to 3`.
- `Collect the Resources` is its own phase before the final refill/pass.
- The turn structure should show `Collect Resources` before `End of Turn`.
- `Play down to 1 or 2 Cards` should be tied to the hand condition and `1 Koku` extra-card cost.
- `Build Castles, Capitals or other buildings` is too vague for V25.

Proposed V25 phase names:

```text
Beginning of Turn
Active Turn
Collect Resources
End of Turn
```

Proposed V25 Active Turn action groups:

```text
Play Cards
Build & Fortify
Reveal
Fix Errors
Diplomacy
```

Proposed playerboard wording, readable version:

```text
PLAYING ROUND

BEGINNING OF TURN
Refill your hand to 3 Cards
Visit the Emperor before action

ACTIVE TURN
Play Cards and resolve effects
Build & Fortify your domain
Reveal face-down Cards
Fix Errors on the board
Use Diplomacy for Alliances

COLLECT RESOURCES
Collect Resources from your domain
Keep up to 5 Koku

END OF TURN
Refill your hand to 3 Cards
Pass the Turn
```

More compact version:

```text
BEGINNING OF TURN
Refill to 3 Cards
Visit Emperor before action

ACTIVE TURN
Play Cards
Build & Fortify
Reveal
Fix Errors
Diplomacy

COLLECT RESOURCES
Gain Resources
Keep up to 5 Koku

END OF TURN
Refill to 3 Cards
Pass Turn
```

Notes:
- `Visit Emperor before action` is more precise than `before playing`, because no other action should happen before the Visit window.
- `Diplomacy` means make/break Alliances when Expert rules are enabled.
- `Build & Fortify` means convert Koku to Protection, place Protection, and resolve Market/Castle/Capital progression.

---

## 3) Resource Counting / Koku Panel

Current V24-style panel observed:

```text
Resource Counting (Koku)
Every counting -> +1
With Market built -> +1
Every Zone conquered -> +1
per Central controlled -> +1
5 max
Koku gained at the end of the round
```

V25 notes:
- `5 max` still matches current V25 Koku cap.
- Consider replacing `Every counting` with clearer wording.
- Consider replacing `Central` with the current final term, likely `Imperial Zone`.
- Manual must state that Imperial Zone income requires connection to Chain / Chain of Command.

Possible V25 wording:

```text
Collect Resources (Koku)
Base income +1
Market built +1
Each Zone or Line +1
Each connected Imperial Zone +1
Keep up to 5 Koku
```

Question for later:
- Should the playerboard mention `Line` income explicitly, or is `Zone conquered` intended to include both zones and lines?

---

## 4) Koku Reserve Panel

Current V24-style panel observed:
- Title: `Koku Resource Reserve`
- Storage icon shows `9 max`.
- Reveal reminder shows `3 -> Reveal a card`.
- Text: `Keep your reserved Koku safely stored here`.

V25 required updates:
- Koku storage cap is now `5`, not `9`.
- Reveal cost remains `3 Koku`.
- Koku is currency stored on the playerboard, not on map cards.

Possible V25 wording:

```text
Koku Reserve
Store up to 5 Koku
Pay 3 Koku to Reveal
```

Visual requirements:
- Update reserve slots / max icon from `9 max` to `5 max`.
- Keep Reveal reminder near the reserve, since it is paid with Koku.

---

## 5) Build & Fortify / Protection Costs Panel

Current V24-style panel observed:

```text
Build and Protections Costs
2 Koku -> Protection Tokens
3 Protection -> Castle or Market
3 Castles -> the Capital
Capital -> Shogun / the game ends at the beginning of the turn
Evolution of the tokens transformed
```

V25 required updates:
- `2 Koku -> 1 Protection Token` is current.
- `Market` costs `2 Protection`, not `3`.
- `Castle` costs `3 Protection`.
- `3 connected Castles -> Capital`.
- Shogun / endgame triggers immediately when the Capital is formed, not at the beginning of a later turn.
- The finale is now `Imperial Summons`.

Possible V25 wording:

```text
Build & Fortify
2 Koku -> 1 Protection
2 Protection -> Market
3 Protection -> Castle
3 Castles -> Capital
Capital -> Imperial Summons
```

Rules reminder:
- Market conversion is optional.
- Castle conversion is mandatory only when the 3 Protection are all on connected Numbered cards.
- Capital conversion is immediate when 3 connected Castles exist.
- These details likely belong in the manual, not all on the playerboard.

---

## 6) Visit the Emperor Panel

Current V24-style panel observed:

```text
Visit the Emperor
- Shuffle the Discarded deck with your hand
- ReDraw 3 cards in your Hand
Once per game: an audience with the Emperor.
```

V25 required update:
- Timing: beginning of a normal turn, after refill and before any other action.
- Effect: shuffle deck + discard pile + entire hand together, then draw 3.
- If hand has more than 3 cards, shuffle all cards in hand and still draw 3.
- Not available during `Imperial Summons`.
- If the Emperor marker remains unused at final scoring, gain `+1` point.
- The lost point/opportunity is the pledge/gift paid to seek imperial favor.

Possible V25 wording:

```text
Visit the Emperor
Before action, shuffle deck,
discard pile, and hand.
Draw 3 cards.
```

Small footer:

```text
Once per game. Unused Emperor marker: +1 point.
```

Question for later:
- Does the playerboard need to explicitly say `after refill`, or is `Before action` enough as a reminder?

---

## 7) Alliances / Diplomacy Panel

General V25 notes:
- Alliances are Expert Mode / Diplomacy.
- Playerboard rewards are clan-specific and should be followed from the playerboard.
- The manual should say to follow the printed playerboard for Alliance rewards/costs.
- Current design preference: avoid Alliance rewards that create accidental instant-Capital spikes.
- If rewards remain in Protection, immediate placement/build rules apply.
- When a Capital is formed and `Imperial Summons` starts, all Alliances end immediately with no break reward.
- If an Alliance token is removed by an effect, the Alliance ends immediately with no break reward.
- Retainer actions cannot affect allies unless a card explicitly says otherwise.

Current V24-style examples observed:

`Akechi Mitsuhide`
```text
Can propose or accept alliances gaining +1 extra token.
To break an alliance, a Castle or Capital is required, granting +2 tokens.
One pact per time. No renewal with the same daimyo.
```

`Oda Nobunaga`
```text
Can ask or break an alliance only with at least 4 Number Cards on game board.
When forming a new alliance, gains same tokens of the other Daimyo.
One pact per time. No renewal with the same daimyo.
```

`Tokugawa Ieyasu`
```text
Can form an alliance and gain +1 extra Token.
Breaking requires to have at least 4 Number Cards on the Game Board.
One pact per time. No renewal with the same daimyo.
```

`Toyotomi Hideyoshi`
```text
Can ask an alliance to gain +2 Tokens.
No extra Tokens provided when receiving an alliance.
No Tokens provided when breaking an existing one.
One pact per time. No renewal with the same daimyo.
```

V25 design watch:
- These currently use Tokens heavily.
- We discussed that Koku-based rewards may be cleaner for V25, but this requires playerboard redesign.
- Keep this as component-design work, not a core rulebook principle.

Possible generic V25 panel title:

```text
Diplomacy
```

Possible generic footer:

```text
One pact at a time.
No renewal with the same Daimyo.
```

---

## 8) Destiny Path Panel

General notes:
- Destiny Path is playerboard-specific.
- The manual should explain that Destiny Path conditions are printed on the playerboard.
- Some missions may depend on cards in hand, so final restricted turns still include hand refill.
- Destiny Path should be checked at endgame/final scoring according to the printed condition.

Current V24-style examples observed:

`Akechi Mitsuhide`
```text
End with 1 Shinobi in the discard pile and 1 Castle built.
+2 Points
```

`Oda Nobunaga`
```text
Complete the game with 1 Samurai on the board.
+2 Points
```

`Tokugawa Ieyasu`
```text
End the game with 3 Retainers Cards in the discard pile.
+2 Points
```

`Toyotomi Hideyoshi`
```text
End the game holding 2 Retainers cards in hand.
+2 Points
```

V25 notes:
- Wording should use `Retainer cards`, not `Special cards`.
- Missions involving cards in hand justify final-turn refill during `Imperial Summons`.
- Check spelling/capitalization:
  - `Retainer cards`
  - `Shinobi`
  - `Castle`
  - `on the board`
  - `in hand`

---

## 9) Clan Header / Biography / Strategy

Observed sections:
- Clan/Daimyo name.
- Historical biography text.
- Strategy text.
- Level.
- Order number.
- Clan icon / mon / calligraphy.
- Map/start-position visual.

V25 notes:
- Historical/strategy text does not need full rules support, but should not contradict mechanics.
- `Strategy` text can be evocative but should avoid promising mechanics that are no longer true.
- `Order Number` should match setup/turn-order rules if still used.

Observed strategy examples:

`Akechi Mitsuhide`
```text
Use the raw strength of the army
to conquer and expand.
Hostile to religious symbols.
```

`Oda Nobunaga`
```text
Use the raw strength of the army
to conquer and expand.
Hostile to religious symbols.
```

`Tokugawa Ieyasu`
```text
Conquer gradually with
strategic patience and careful
planning for ultimate success.
```

`Toyotomi Hideyoshi`
```text
Castles and buildings are best
defences, use the speed
as advantage on the others
```

---

## 10) Immediate Manual Updates Needed From Playerboard

- Add or update a playerboard reference section in the manual.
- Manual must define the new turn phase names:
  - `Beginning of Turn`
  - `Active Turn`
  - `Collect Resources`
  - `End of Turn`
- Manual must explain Active Turn action groups:
  - `Play Cards`
  - `Build & Fortify`
  - `Reveal`
  - `Fix Errors`
  - `Diplomacy`
- Manual must explain `Imperial Summons`.
- Manual must align with V25 playerboard values:
  - Koku cap `5`
  - Reveal cost `3 Koku`
  - `2 Koku -> 1 Protection`
  - `2 Protection -> Market`
  - `3 Protection -> Castle`
  - `3 Castles -> Capital`
  - Capital immediately starts `Imperial Summons`
- Manual must say playerboard-specific Alliance and Destiny Path text is authoritative.

---

## 11) Open Playerboard Design Questions

1. Should Alliance rewards move from Protection tokens to Koku in V25?
2. Should `Collect Resources` mention only Koku, or also other possible playerboard rewards?
3. Should `Visit the Emperor` panel include `after refill`, or just `before action`?
4. Should `Imperial Summons` appear as a visible playerboard reminder?
5. Should the Playing Round panel use full phrases or compact labels?
6. Should `Line` income be explicitly printed, or does current `Zone conquered` cover it?
7. Should `Koku Reserve` visually show 5 slots only, or keep decorative unused slots with `5 max`?
