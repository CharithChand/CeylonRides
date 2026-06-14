# CeylonRides — Development Workflow

## Workflow Overview

```
Write Code → Stage → Commit → Push to GitHub → Deploy to GitHub Pages
```

Live site: https://charithchand.github.io/CeylonRides/
Repository: https://github.com/CharithChand/CeylonRides

---

## Step-by-Step

### 1. Make Changes Locally
Edit files in `/workspace/Projects/CeylonRides/` using Claude as your development assistant.

### 2. Review Changes
```bash
git status        # see which files changed
git diff          # see exact line-by-line changes
```

### 3. Stage Files
```bash
git add index.html          # stage a specific file (preferred)
git add index.html style.css  # stage multiple files
```

### 4. Commit with a Meaningful Message

Format: `<type>: <short summary in present tense>`

| Type | When to use |
|---|---|
| `feat` | New feature or section |
| `fix` | Bug fix |
| `style` | CSS/layout, no logic change |
| `content` | Text, images, copy updates |
| `refactor` | Code restructure, no behavior change |
| `chore` | Config, cleanup |

```bash
git commit -m "feat: add contact form to homepage"
git commit -m "fix: map embed not loading on mobile"
git commit -m "style: update hero section colours and font"
git commit -m "content: update tour package prices"
```

### 5. Push to GitHub
```bash
git push origin main
```

### 6. Verify Deployment
GitHub Pages auto-deploys within ~60 seconds of a push.
Check: https://charithchand.github.io/CeylonRides/

---

## Quick Reference

| Command | Purpose |
|---|---|
| `git status` | See what changed |
| `git diff` | See exact line changes |
| `git add <file>` | Stage a file |
| `git commit -m "..."` | Save a snapshot |
| `git push origin main` | Upload to GitHub + trigger deploy |
| `git log --oneline` | View commit history |
| `git pull origin main` | Download latest from GitHub |

---

## Feature Branch Workflow (for larger changes)

```bash
git checkout -b feature/your-feature-name   # create branch
# ... make changes and commit ...
git checkout main                            # switch back to main
git merge feature/your-feature-name         # merge in the work
git push origin main                         # deploy
git branch -d feature/your-feature-name     # clean up
```

---

## Commit History Tips
- One logical change per commit — don't mix a bug fix with a new feature
- Write messages in present tense: "add" not "added"
- Be specific: "fix map not loading on iOS Safari" beats "fix bug"
