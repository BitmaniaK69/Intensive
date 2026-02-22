# Sengoku 2026 Structure Plan
_Last updated: 2026-02-14_

## Objective
Create a clean, canonical `2026` structure for V24 work:
- one main tabletop project file (`Sengoku-V24.tcp`),
- assets organized by role,
- relative paths only,
- no dependency on `C:` or previous year folders.

## Canonical Project Rule
- Exactly one `.tcp` is canonical for active development: `E:\Projects\Intensive\Sengoku\2026\PROJECT\Sengoku-V24.tcp`
- Any other `.tcp` files are legacy snapshots/reference only.

## Proposed Canonical Root
`E:\Projects\Intensive\Sengoku\2026\`

## Proposed Folder Layout
```text
2026/
  PROJECT/
    Sengoku-V24.tcp
    data/
      data.json
      export.json
      variables.json
      blueprints/
      sets/
  RESOURCES/
    cards/
      fronts/
      backs/
      sashimono/
      titles/
    icons/
      actions/
      economy/
      status/
    clans/
      symbols/
      full/
    playerboard/
      v24/
    board/
      map/
      zones/
    ui/
      labels/
      backgrounds/
  FILES/
    psd/
      cards/
      playerboard/
      board/
      rulebook/
    afpub/
    source_exports/
  OUTPUT/
    print/
    tts/
  DOCS/
    rulebook/
    changelog/
```

## Canonical Asset Rules
1. `PROJECT/` contains only runtime project files (`.tcp` + `data/*`).
2. `RESOURCES/` contains only assets currently used by V24.
3. `FILES/` contains editable masters (`.psd`, `.afpub`, etc.), not used directly by `.tcp`.
4. `OUTPUT/` is generated-only; can be recreated.
5. No absolute `C:/...` or `E:/...` references inside `PROJECT/data/*.json`.

## Migration Strategy (Non-Destructive)
### Phase 1: Inventory
1. Read `Sengoku-V22.tcp` + `PROJECT/data/data.json` and collect all file references.
2. Build a unique asset list grouped by type (cards, icons, clans, board, playerboard).
3. Mark missing files and duplicates (same filename, different paths/hash).

### Phase 2: Staging
1. Create `2026/PROJECT`, `2026/RESOURCES`, `2026/FILES`, `2026/OUTPUT`, `2026/DOCS`.
2. Copy only required assets for V24 into `2026/RESOURCES`.
3. Keep original roots unchanged.

### Phase 3: Path Rewrite
1. Rewrite paths in `2026/PROJECT/data/*.json` to relative paths.
2. Normalize path style and naming conventions.
3. Validate by opening `Sengoku-V24.tcp` without fallback references.

### Phase 4: Validation
1. Zero broken textures/icons.
2. Exports to print/TTS complete.
3. No cross-root references in project JSON.

## Immediate Next Deliverables (in `AI`)
1. `V24_ASSET_INVENTORY.csv`
2. `V24_DUPLICATES_REPORT.md`
3. `V24_PATH_REWRITE_MAP.csv`
4. `V24_MIGRATION_CHECKLIST.md`

## Initial Canonical Project Seed
Use this as base input for migration:
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\Sengoku-V22\Sengoku-V22.tcp`
- `C:\Projects\Sengoku\PROJECTS\Sengoku TTC\Sengoku-V22\data\data.json`

Reason:
- It is the latest active tabletop project file in current workflow and already used for V22/V24-era asset linkage.
