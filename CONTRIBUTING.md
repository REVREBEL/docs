# Contributing to REVREBEL Docs

This repo is the single Mintlify deployment for `docs.revrebel.io`. Pages live as MDX under product subfolders.

## Repo layout

Each product / source repo gets its own subfolder so synced content stays isolated:

```
metrics-library/   # synced from REVREBEL/Metrics-Library
api-reference/     # authored here
essentials/        # authored here
agent-ready/       # authored here
ai-tools/          # authored here
```

When onboarding a new product repo, give it its own top-level folder (e.g. `metrics-dataform/`, `brand/`) and a matching tab in `docs.json`.

## Editing docs

- **Authored-here folders** (`api-reference/`, `essentials/`, `agent-ready/`, `ai-tools/`, root pages): edit directly via PR.
- **Synced folders** (currently `metrics-library/`): **do not edit MDX directly**. Edit the source Markdown in the upstream repo (`REVREBEL/Metrics-Library/docs/`). A GitHub Action in that repo opens a PR here on every push to `main`.

If you edit a synced folder by hand, the next sync will overwrite your changes.

## Adding a new synced product

1. Pick a folder name (kebab-case, matches the product).
2. In the source repo, add a sync workflow modeled on `REVREBEL/Metrics-Library/.github/workflows/sync-docs.yml`. Change `TARGET_DIR` to your new folder.
3. In `docs.json`, add a new tab under the appropriate product with the page list.

## Local preview

```bash
mint dev
```

## Validation

Before opening a PR:

```bash
mint validate
mint broken-links
```
