# Issue Hierarchy Tree - Documentation

## What it does

Adds a **Hierarchy** panel to the Jira issue view showing the full parent/child chain for the current issue - every ancestor up to the top-most level (Epic, Feature, Initiative, or a custom hierarchy level) and every descendant down to Sub-task - as an interactive map, plus every `blocks` / `is blocked by` relationship drawn directly on it.

## How to use it

1. Open any issue in Jira Cloud.
2. Find the **Hierarchy** panel (below the description, among the app panels - click to expand it if it's collapsed).
3. The map opens with the path to your current issue already expanded. Click the **+ / -** circle on any card to expand or collapse its children.
4. Click and drag on empty space to pan around large trees.
5. Red dashed lines labeled "blocks" show blocking relationships between issues on the map. If a blocker sits outside the current tree (a different epic, a different project), the card shows a small chip naming that issue directly - click it to open it in a new tab.
6. Click any issue key to open that issue in a new tab.

## Permissions

The app only reads data via your own Jira permissions (issue summary, status, type, hierarchy, and `blocks`/`is blocked by` links). It never shows you anything you couldn't already see in Jira, and never writes, deletes, or modifies any Jira data.

## Support

Questions or issues: **bim.eleck@gmail.com**

## Privacy & Security

- [Privacy Policy](./PRIVACY.md)
- [Security Policy](./SECURITY.md)
