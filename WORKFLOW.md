# CeylonRides — Development Workflow

Live site:  https://charithchand.github.io/CeylonRides/
Repository: https://github.com/CharithChand/CeylonRides

---

## Branch Structure

```
main        ← production (live site on GitHub Pages) — never commit directly here
 └── dev    ← integration (all tested features merge here first)
      └── feature/*  ← one branch per feature or fix
```

| Branch | Purpose | Who pushes here |
|---|---|---|
| `main` | Live production site | Merged from `dev` only when stable |
| `dev` | Staging / integration | Merged from feature branches |
| `feature/*` | Individual changes | You (Claude), then merged to dev |

---

## Standard Workflow — Step by Step

### 1. Always start from dev

```bash
git checkout dev
git pull origin dev          # get latest before branching
```

### 2. Create a feature branch

```bash
git checkout -b feature/your-feature-name
```

**Naming examples:**
```
feature/contact-form
feature/tour-packages-section
feature/mobile-nav-fix
fix/map-not-loading
style/hero-section-redesign
content/update-pricing
```

### 3. Make changes and commit

```bash
git add index.html           # stage specific files
git commit -m "feat: add contact form with validation"
```

**Commit message format:** `<type>: <short summary in present tense>`

| Type | When to use |
|---|---|
| `feat` | New feature or section |
| `fix` | Bug fix |
| `style` | CSS/layout, no logic change |
| `content` | Text, images, copy updates |
| `refactor` | Code restructure, no behavior change |
| `chore` | Config, cleanup |
| `docs` | README or documentation |

### 4. Push the feature branch to GitHub

```bash
git push origin feature/contact-form
```

### 5. Merge into dev (after testing locally)

```bash
git checkout dev
git merge feature/contact-form
git push origin dev
```

### 6. Promote dev → main (when ready to go live)

```bash
git checkout main
git merge dev
git push origin main         # triggers GitHub Pages deployment
```

### 7. Clean up the feature branch

```bash
git branch -d feature/contact-form           # delete locally
git push origin --delete feature/contact-form  # delete on GitHub
```

---

## Full Example — End to End

```bash
# Start fresh from dev
git checkout dev
git pull origin dev

# Create a feature branch
git checkout -b feature/booking-form

# Claude makes changes to index.html...

# Review, stage, commit
git status
git add index.html
git commit -m "feat: add tour booking form with date picker"

# Push feature branch
git push origin feature/booking-form

# Test locally, then merge to dev
git checkout dev
git merge feature/booking-form
git push origin dev

# When happy with dev, promote to main (goes live)
git checkout main
git merge dev
git push origin main

# Clean up
git branch -d feature/booking-form
git push origin --delete feature/booking-form
```

---

## Quick Reference

| Command | Purpose |
|---|---|
| `git branch` | List local branches |
| `git branch -a` | List all branches including remote |
| `git checkout dev` | Switch to dev branch |
| `git checkout -b feature/name` | Create and switch to new branch |
| `git status` | See what changed |
| `git diff` | See exact line changes |
| `git add <file>` | Stage a file |
| `git commit -m "..."` | Save a snapshot |
| `git push origin <branch>` | Push branch to GitHub |
| `git merge <branch>` | Merge branch into current branch |
| `git branch -d <branch>` | Delete local branch |
| `git log --oneline --graph` | Visual commit history |

---

## Rules

1. **Never commit directly to `main`** — always go through `dev`
2. **One feature per branch** — keeps history clean and easy to revert
3. **Test locally on `dev` before promoting to `main`**
4. **Meaningful commit messages** — future you will thank present you
5. **Pull `dev` before branching** — avoid merge conflicts
