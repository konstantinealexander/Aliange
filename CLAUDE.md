# Aliangé Theme — Claude Code Rules

## Git: Always Pull Before Editing, Always Push After

**The Shopify theme editor auto-commits to `origin/main` on every save.**
Other team members (and the Shopify editor itself) may push at any time.

### Mandatory workflow for every session:

1. **Before touching any file** — pull first:
   ```
   git pull --rebase origin main
   ```
   If there are local uncommitted changes, stash first:
   ```
   git stash && git pull --rebase origin main && git stash pop
   ```

2. **After making all changes** — commit and push immediately:
   ```
   git add <files>
   git commit -m "..."
   git push origin main
   ```

3. **If push is rejected** (someone else pushed while you were working):
   ```
   git pull --rebase origin main
   git push origin main
   ```

### Why this matters
- Shopify's GitHub integration commits every theme editor save directly to `main`
- There is no version control in the Shopify theme editor UI
- Any local edits pushed without pulling first will silently overwrite editor changes
- Always pull → edit → commit → push. Never skip the pull.
