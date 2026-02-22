# Path Dependencies Audit
_Last updated: 2026-02-14_

## Scope
Cross-root dependency audit between:
- `C:\Projects\Sengoku`
- `E:\Projects\Intensive\Sengoku`

Filters used:
- Included: `*.json`, `*.md`, `*.txt`, `*.docx`, `*.csv`, `*.yml`, `*.yaml`
- Excluded: `**/temp/logs/**`, `**/logs/**`

## Key Finding
The mix is real and operational (not only historical): active project JSON files in one root contain hardcoded absolute paths to the other root.

## High-Impact Cross References
### `C -> E` references
Files containing references to `E:\Projects\Intensive\Sengoku`:
1. `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\V21\data\data.json`
2. `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\Sengoku-V22\data\data.json`

Observed pattern:
- Card/project data in `C:` points to assets under `E:\Projects\Intensive\Sengoku\2025\RESOURCES\...`
- Typical examples: icons, sashimono, card backs, playerboard assets.

### `E -> C` references
Files containing references to `C:\Projects\Sengoku`:
1. `E:\Projects\Intensive\Sengoku\2024\PROJECTS\Sengoku TTC\V19-0\data\data.json`
2. `E:\Projects\Intensive\Sengoku\2024\ADVERT\CardCreator\data\sets\80bb7ae9-c90d-49f9-b4a2-3c92afacfee0.json`
3. `E:\Projects\Intensive\Sengoku\2024\ADVERT\CardCreator\data\blueprints\f28627fd-a1a7-457d-aaf9-f870bd67c59b.json`
4. `E:\Projects\Intensive\Sengoku\2024\ADVERT\CardCreator\data\blueprints\6d21611d-a90f-4c60-8bc9-0215e6252610.json`

Observed pattern:
- `E:` projects reference business-card and icon assets in `C:\Projects\Sengoku\...`

## Main Tabletop Creator Project Files (`.tcp`)
### Primary candidates
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\Sengoku-V22\Sengoku-V22.tcp`
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\V21\V21.tcp`
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\V19-0\V19-0.tcp`
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\V19-0\SudokuDeck-19.tcp`
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\V16-1\SudokuDeck.tcp`

### Additional legacy/experimental `.tcp`
- `E:\Projects\Intensive\Sengoku\2024\PROJECTS\Sengoku TTC\V19-0\SudokuDeck-19.tcp`
- `E:\Projects\Intensive\Sengoku\2024\PROJECTS\Sengoku TTC\V16-1\SudokuDeck.tcp`
- `E:\Projects\Intensive\Sengoku\2024\EXTRA\EXPERIMENTS\Sengoku TabletopCreator\SudokuDeck.tcp`
- `C:\Projects\Sengoku\ADVERT\CardCreator\BusinessCard.tcp`

## Risk Summary
1. Opening a project from one root may fail silently/miss textures due to absolute path dependencies on the other root.
2. Duplicated assets across roots increase drift risk.
3. Legacy logs and exports add noise and can hide the canonical source files.

## Recommendation
Do not edit old roots in-place first. Create a clean `2026` canonical root, then migrate the active V24 project and only required assets, converting references to relative paths.
