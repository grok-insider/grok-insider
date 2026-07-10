# AGENTS.md — grok-insider (profile README)

GitHub **profile README** repo only. Not a product codebase.

> ## ⛔ Rule #1 — always exactly one commit
>
> This repository must have **exactly one commit** on the default branch at all
> times. There is **no history** to keep.
>
> ```sh
> git rev-list --count HEAD   # must print: 1
> ```

## Default branch

- **`master`** (not `main`)
- Force-push is the **intended** publish path for this repo
- Do **not** open multi-commit PR stacks here
- Exception to the org-wide “always PR / no force-push” rule for product repos

## How to update

1. Edit files on `master` (usually `README.md`).
2. Publish with **one** of these (never leave a second non-amended commit):

**Amend** (when HEAD is already a single root commit):

```sh
git add -A
git commit --amend -m "Grok Insider profile"
git push --force-with-lease origin master
```

**Orphan rewrite** (always safe; always ends at 1 commit):

```sh
git checkout --orphan _single
git add -A
git commit -m "Grok Insider profile"
git branch -M master
git push --force-with-lease origin master
```

3. Confirm: `git rev-list --count HEAD` → `1`.

## CI

`.github/workflows/single-commit.yml` fails if the tip of `master` is not
exactly one commit. Fix by amending or orphan-rewriting, then force-pushing.

## Org QC

This repo is an intentional **exception** to Model A product rules. Scoreboard:
`~/dev/opensource/docs/comparison.md` (special row).
