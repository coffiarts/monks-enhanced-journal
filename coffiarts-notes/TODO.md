# TODO: coffiarts fixes on top of bularzik/integration-14.08

Base: `bularzik/integration-14.08` (working mod). Optional upstream PRs: one branch per fix from `origin/main`.
Status: [ ] open, [~] in progress, [x] done, [-] dropped

## Backlog

- [ ] **A. Purchases stack in buyer's inventory** (general)
    - Shared helper `addOrStackToInventory`, used by direct and approved purchases; `parseInt` on quantities
    - Files: `monks-enhanced-journal.js`, `sheets/ShopSheet.js`
    - Commits: `f03ed2c`, `765e6cd`
    - Conflict expected in `ShopSheet.js` against the base

- [ ] **B. Quantity path gets `.value`** (dsa5)
    - `quantityname()` appends `.value` for dsa5
    - Files: `monks-enhanced-journal.js`

- [ ] **C. Skip the actor sheet drop handler** (dsa5)
    - Adds `dsa5` to the exclusion list in `canDropOnActorSheet`
    - Files: `helpers.js`

- [ ] **D. Sold items stack in the shop's inventory** (general)
    - Matches by item name instead of `parentId`; adds the sold quantity
    - Files: `sheets/EnhancedJournalSheet.js`
    - Commit: `4636d0a`
    - Check: `remaining` still increases by 1 while `quantity` increases by the sold amount; `addedQty` is not parsed and may be undefined

- [ ] **E. Hidden shop items invisible to players (#805)** (general)
    - Hides hidden items and groups with no visible items for non-owners (`countVisible`)
    - Files: `sheets/EnhancedJournalSheet.js`, `templates/sheets/partials/sheet-shop-items.hbs`
    - Commit: `e22a15c`

- [ ] **F. Item name opens the item sheet** (general)
    - New action `renderItemSheet`; summary toggle moves to the item icon
    - Files: `sheets/ShopSheet.js`, `templates/sheets/partials/sheet-shop-items.hbs`
    - Check: stray double quote in the template (`data-action="renderItemSheet""`)

- [ ] **G. Item summary data** (dsa5)
    - `createItemChatData` builds summary data for dsa5; null-safe `price?.denomination`
    - Files: `sheets/EnhancedJournalSheet.js`
    - Check: the non-dsa5 branch has no `return`, so other systems get `undefined`

- [ ] **H. German translations and verb localization** (i18n)
    - `de.json` corrections and three new keys; `format(verb)` in the quantity dialog
    - Files: `lang/de.json`, `sheets/EnhancedJournalSheet.js`
    - Check: `MonksEnhancedJournal.Description` is still English

- [ ] **I. Page-type hack and version string** (personal, not for PRs)
    - `ALLOWED_PAGETYPES` bypass in `openJournalEntry`; `module.json` version `14.01-x (coffiarts)`
    - Files: `monks-enhanced-journal.js`, `module.json`
    - Commit: `829e793`

## Already in bularzik's line (nothing to do)

- "Allow GM" setting (`7cc2140`)
- DSA5 currency matching, #795 (`3c0be9a`)
- Quest rewards fix, #803 (no longer in my delta)
