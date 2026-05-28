# Sengoku V25 - Manual Generation Guide

This file explains how to generate and maintain the two derived manual documents:

- [Sengoku_Rulebook_v25_ManualFull.md](./Sengoku_Rulebook_v25_ManualFull.md)
- [Sengoku_Rulebook_v25_ManualFull-complete.md](./Sengoku_Rulebook_v25_ManualFull-complete.md)

The source rule document is:

- [RulesV25-Final.md](./RulesV25-Final.md)

The working principle is simple:

1. Keep writing and correcting the rules in [RulesV25-Final.md](./RulesV25-Final.md).
2. Treat [RulesV25-Final.md](./RulesV25-Final.md) as the single rules authority.
3. Generate or update the two manual files from that source.
4. Do not use either manual file as the source for changing the rules.

---

## 1) Source Authority

### Primary source

[RulesV25-Final.md](./RulesV25-Final.md) is the current source of truth for Sengoku V25.

It contains:

- formal rules;
- setup rules;
- component rules;
- turn structure;
- scoring;
- endgame;
- Expert Mode;
- Duels;
- glossary;
- historical notes;
- designer notes;
- Retainer appendix;
- rule clarifications already consolidated from older add-ons.

If a rule appears differently in any other file, follow [RulesV25-Final.md](./RulesV25-Final.md).

### Secondary references

Use these only to support wording, timing checks, playerboard alignment, or implementation consistency:

- [README_FOR_MANUAL_WRITER.md](./README_FOR_MANUAL_WRITER.md)
- [sengoku_rulebook_v25_play.md](./sengoku_rulebook_v25_play.md)
- [TURN_FLOW_RECAP_V25.md](./TURN_FLOW_RECAP_V25.md)
- [actions_by_clan.md](./actions_by_clan.md)
- [RETAINER_ACTIONS_MATRIX_V25.md](./RETAINER_ACTIONS_MATRIX_V25.md)
- [PLAYERBOARD_V25_NOTES.md](./PLAYERBOARD_V25_NOTES.md)

### Historical references

Use these only for history, comparison, or recovery:

- [BACKUP/RulesV25.md](./BACKUP/RulesV25.md)
- [BACKUP/RulesV25-addOns.md](./BACKUP/RulesV25-addOns.md)
- [BACKUP/RulesV25-Final.md](./BACKUP/RulesV25-Final.md)

Do not promote old wording from backup files unless it is intentionally reintroduced into [RulesV25-Final.md](./RulesV25-Final.md).

---

## 2) Derived Documents

### A) `Sengoku_Rulebook_v25_ManualFull.md`

Purpose:

- Create a complete, readable manual draft for the game designer.
- Follow the collaborator's requested rulebook structure.
- Include every formal rule needed to play the game.
- Reorganize the source into a clean manual flow.
- Avoid unnecessary duplication where the same rule is repeated in the source.

This document may consolidate wording, but it must not remove rules.

It should include:

- all components;
- all setup rules;
- goal;
- full gameplay rules;
- endgame and scoring;
- Standard Mode;
- Expert Mode;
- Duels;
- Retainers reference;
- glossary;
- historical/designer notes when they are present in [RulesV25-Final.md](./RulesV25-Final.md).

It should not include full copies of external files.

### B) `Sengoku_Rulebook_v25_ManualFull-complete.md`

Purpose:

- Create the exhaustive writer handoff version.
- Preserve all information from [RulesV25-Final.md](./RulesV25-Final.md).
- Include collateral notes from the source when useful for the writer.
- Add reference links to external support files instead of copying those files into the manual.

This document is allowed to be longer than the final printed manual.

The writer or game designer can cut text later. The generation pass must not cut rules for them.

It should include:

- the same complete manual structure as `ManualFull.md`;
- source-complete writer notes;
- locked clarifications;
- additional source details to preserve;
- historical notes;
- designer notes;
- illustration briefs from the source;
- open playerboard questions if still relevant;
- reference links to external files when a detail is supported by another document.

It should not include a pasted full copy of external reference files.

---

## 3) Collaborator's Required Manual Structure

The game designer asked for the whole rulebook to be structured in this format:

```text
TITLE
X-X players | X hours | X+ years

Introduction paragraph.

COMPONENTS
Name and quantity of each component, listed in the order they're mentioned during setup.
List of important names for parts of the components that are mentioned throughout the rules (just the list of names and where they're found in which component).

SETUP
Numbered list of steps.
List steps in the order they would appear in the image of the full setup, top to bottom left to right.
Every single component must be mentioned during the setup steps, no exception, even if in a final step of "return all unused components to the game box".
Write a step for each kind of component, except for those that have identical setup instructions (which should be grouped together in a single step) or a more complex set of procedures (which should be split in separate steps according to necessity).
Bold the first mention of each component's name in this section.

GOAL
Brief definition, preferably in a single sentence, of how to win.
Do not explain in-depth, as the nuances will be explained in GAME END.

GAMEPLAY
The actual rules, from macro to micro, from early to late.
Organize into sections and subsections according to the structure.

GAME END
Same content as in GOAL, but explaining each mechanic in depth.

VARIANTS, LISTS, GLOSSARY...
Anything beyond the essential for playing the first game.
```

Both generated manuals must follow this structure unless there is an explicit later instruction to change the format.

---

## 4) Non-Omission Rule

The most important instruction from the project owner is:

> Do not leave anything out.

Generation must follow these rules:

- Do not omit a rule because it feels too detailed.
- Do not omit edge cases.
- Do not omit timing windows.
- Do not omit exceptions.
- Do not omit component limits.
- Do not omit Expert Mode rules.
- Do not omit Duels rules.
- Do not omit Retainer action details.
- Do not omit historical notes, designer notes, glossary notes, or illustration notes when generating the complete version.
- Do not silently resolve ambiguity by deleting one side.
- If something is unclear, keep the source detail and add a writer note or question.
- If something is supported by an external reference file, add a Markdown link to that file instead of pasting the whole file.

The designer may shorten the final manual later. The generation pass should preserve information, not edit it down.

---

## 5) No-Surprise Editing Rules

When creating or regenerating the manual files:

- Do not overwrite existing manual files unless explicitly asked.
- If a new attempt is needed, create a new file with a clear suffix.
- Do not modify [RulesV25-Final.md](./RulesV25-Final.md) unless the task is specifically to update the source rules.
- Do not copy full external reference files into the manual.
- Use Markdown links to references instead.
- Do not make backup files the authority.
- Do not use old V24 values or wording if V25 has changed them.
- Do not reintroduce removed systems such as Siege Towers.

Recommended naming when creating a new generation attempt:

- `Sengoku_Rulebook_v25_ManualFull-draft2.md`
- `Sengoku_Rulebook_v25_ManualFull-complete-draft2.md`
- `Sengoku_Rulebook_v25_ManualFull-YYYY-MM-DD.md`

Only replace the canonical files after the project owner explicitly approves replacement.

---

## 6) Generation Workflow

### Step 1 - Read the source

Read [RulesV25-Final.md](./RulesV25-Final.md) completely.

Do not rely on memory from previous chats.

### Step 2 - Check source hierarchy

Read [README_FOR_MANUAL_WRITER.md](./README_FOR_MANUAL_WRITER.md) to confirm the current file hierarchy and locked clarifications.

### Step 3 - Read secondary references

Use the secondary files to cross-check:

- turn timing in [TURN_FLOW_RECAP_V25.md](./TURN_FLOW_RECAP_V25.md);
- Retainer behavior in [RETAINER_ACTIONS_MATRIX_V25.md](./RETAINER_ACTIONS_MATRIX_V25.md);
- compact Retainer wording in [actions_by_clan.md](./actions_by_clan.md);
- table-facing wording in [sengoku_rulebook_v25_play.md](./sengoku_rulebook_v25_play.md);
- playerboard values and open playerboard questions in [PLAYERBOARD_V25_NOTES.md](./PLAYERBOARD_V25_NOTES.md).

### Step 4 - Build the manual structure

Create the document in the collaborator's required structure:

1. Title and player/time/age line.
2. Introduction.
3. Components.
4. Setup.
5. Goal.
6. Gameplay.
7. Game End.
8. Variants, lists, glossary, appendices.

### Step 5 - Transfer rules from macro to micro

In `GAMEPLAY`, organize rules in this order unless a later editorial direction changes it:

1. game overview;
2. core concepts;
3. turn structure;
4. card types and placement;
5. face-down cards, Reveal, and traps;
6. Errors / Rebellions;
7. Koku, Protection, reserve, and player supply;
8. defenses;
9. building Market and Castle;
10. forming a Capital;
11. attacks and Retainer timing;
12. Shogun / Imperial Summons;
13. Alliances;
14. Visit the Emperor;
15. final scoring.

### Step 6 - Add variants and references

Place beyond-first-game material in the final sections:

- Standard Mode recap;
- Expert Mode;
- Duels;
- Retainers reference;
- glossary;
- designer notes;
- historical notes;
- source/writer notes.

### Step 7 - Cross-check for omissions

Before considering the manual complete, verify that every major heading from [RulesV25-Final.md](./RulesV25-Final.md) is represented:

- Game Overview;
- Game Components;
- Setup;
- Game Elements;
- Deck and Card Types;
- Retainer Cards Anatomy;
- Card Placement Rules;
- Errors / Rebellions;
- Cards and Tokens;
- Token Types;
- Defences;
- Building Castles and Market;
- Forming a Capital;
- Attack Actions;
- Became a Shogun / Imperial Summons;
- Alliances;
- Visit the Emperor;
- Turn Structure;
- End Game Sequence;
- Final Scoring;
- Junbi;
- Sengoku Duels;
- Duel Rule Changes;
- Duel End Game;
- Duel Scoring;
- Glossary;
- Designer Note;
- Retainers Appendix.

### Step 8 - Report anything not integrated

If anything from [RulesV25-Final.md](./RulesV25-Final.md) is not integrated into the manual body, it must be listed in a writer note and linked to the source section or file.

Do not simply omit it.

---

## 7) Current V25 Values To Preserve

These values are easy to confuse with older versions. Preserve the V25 values unless [RulesV25-Final.md](./RulesV25-Final.md) is changed:

- Koku is currency and stays on the player board.
- Koku storage cap is 5.
- End-of-turn economy counting can generate at most 5 Koku from counting sources.
- Reveal costs 3 Koku.
- Convert Koku to Protection: 2 Koku -> 1 Protection token.
- Protection tokens are map resources.
- Protection token pool is capped at 6 per player.
- Market costs 2 Protection.
- Castle costs 3 Protection.
- Market conversion is not mandatory.
- Castle conversion is mandatory only under the connected Numbered-card condition in the rules.
- 3 connected Castles immediately form a Capital.
- A Capital must be connected to the Chain of Command to trigger Imperial Summons.
- Imperial Summons triggers immediately when a valid connected Capital is formed.
- Restricted final turns allow only Koku-based Reveal and Koku-to-Protection/build progression.
- Shogun scoring is ordered: first +4, second +3, third +2, later players +1.
- Face-down cards do not score direct card points.
- Face-down cards still count for control by clan.
- Imperial Zones cannot receive face-down cards, Protection tokens, or buildings.
- Alliances, Visit the Emperor, and Destiny Path belong to Expert Mode.

---

## 8) Handling Unclear Or Conflicting Information

If a conflict appears:

1. Follow [RulesV25-Final.md](./RulesV25-Final.md).
2. If the conflict is between secondary files, use the hierarchy in [README_FOR_MANUAL_WRITER.md](./README_FOR_MANUAL_WRITER.md).
3. If a secondary file contains useful wording but not authority, use the wording only if it does not change the rule.
4. If a real design question remains unresolved, add it as a writer note in `ManualFull-complete.md`.
5. Do not invent a final rule unless the project owner asks for a design decision.

Known example:

- Playerboard notes still ask whether Line income should be explicitly printed. The current manual generation should preserve the rule as stated in the source and, if needed, note the playerboard wording question with a link to [PLAYERBOARD_V25_NOTES.md](./PLAYERBOARD_V25_NOTES.md).

---

## 9) Quality Checklist Before Delivery

Before delivering either manual file, check:

- The file follows the collaborator's requested structure.
- Every component is listed in `COMPONENTS`.
- Every component is mentioned in `SETUP`.
- The first mention of each component in `SETUP` is bold.
- `GOAL` is short.
- `GAME END` explains the endgame in depth.
- `GAMEPLAY` moves from macro to micro and from early to late.
- Standard, Expert, and Duel material are all present.
- Retainer actions are present and aligned with the source.
- Historical/designer notes from the source are either included or preserved in complete writer notes.
- External files are linked, not pasted.
- No old V24 values remain accidentally.
- No rules are removed for brevity.
- Any unresolved issue is explicitly listed.

---

## 10) Short Instruction For Future Work

When asked to update the manual:

1. Update [RulesV25-Final.md](./RulesV25-Final.md) first if the rule itself changed.
2. Regenerate or update [Sengoku_Rulebook_v25_ManualFull.md](./Sengoku_Rulebook_v25_ManualFull.md) from that source.
3. Regenerate or update [Sengoku_Rulebook_v25_ManualFull-complete.md](./Sengoku_Rulebook_v25_ManualFull-complete.md) from that source.
4. Preserve everything.
5. If cutting is needed, leave that to the game designer unless explicitly instructed.

