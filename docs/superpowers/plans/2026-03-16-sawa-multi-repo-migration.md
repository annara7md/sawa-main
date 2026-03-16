# SAWA Multi-Repository Migration Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Repair the current local Git state and convert `sawa-main` into a clean coordination repository that tracks `sawa-dashboard`, `sawa-backend`, and `sawa-app` as independent submodules.

**Architecture:** First stabilize each child repository independently, starting with the only repository that already has real Git history (`sawa-dashboard`). Then initialize the root `sawa-main` repository with shared docs and README only, and finally attach the three child projects as submodules so root stays clean and each project keeps an isolated lifecycle.

**Tech Stack:** Git, Git submodules, GitHub remotes, pnpm/Husky for dashboard, Python/Django backend repo setup, Flutter app repo setup

---

## File Structure

**Create:**
- `/Users/fahmifareed/Documents/sawa-main/README.md`
- `/Users/fahmifareed/Documents/sawa-main/.gitignore`
- `/Users/fahmifareed/Documents/sawa-main/.gitmodules`
- `/Users/fahmifareed/Documents/sawa-main/docs/superpowers/plans/2026-03-16-sawa-multi-repo-migration.md`

**Modify:**
- `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard/.git/config`
- `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard/.gitignore` if needed
- `/Users/fahmifareed/Documents/sawa-main/sawa-app/.git/config`
- `/Users/fahmifareed/Documents/sawa-main/sawa-backend/.git/config` once initialized

**Verify:**
- `/Users/fahmifareed/Documents/sawa-main/`
- `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard`
- `/Users/fahmifareed/Documents/sawa-main/sawa-backend`
- `/Users/fahmifareed/Documents/sawa-main/sawa-app`

## Chunk 1: Capture Baseline Evidence

### Task 1: Re-run full Git diagnosis and save the evidence

**Files:**
- Verify: `/Users/fahmifareed/Documents/sawa-main/`
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard`
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-backend`
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-app`

- [ ] **Step 1: Run root diagnostics**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git rev-parse --show-toplevel
```
Expected: fail with `not a git repository` before root initialization.

- [ ] **Step 2: Run dashboard diagnostics**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git status
git branch -vv
git remote -v
git log --graph --oneline --decorate --all --max-count=50
git submodule status
git rev-parse --show-toplevel
git config --list
```
Expected: dashboard shows dirty working tree and incorrect remote.

- [ ] **Step 3: Run backend diagnostics**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git status
```
Expected: fail with `not a git repository`.

- [ ] **Step 4: Run app diagnostics**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git status
git branch -vv
git remote -v
git log --graph --oneline --decorate --all --max-count=50
git submodule status
git rev-parse --show-toplevel
git config --list
```
Expected: app repo exists but has no commits and no remote.

## Chunk 2: Stabilize `sawa-dashboard`

### Task 2: Preserve all current dashboard work before any remote repair

**Files:**
- Modify: `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard/.git`
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard`

- [ ] **Step 1: Record current dashboard diff summary**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git status --short
```
Expected: list of modified and untracked files.

- [ ] **Step 2: Create a local safety commit**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git add .
git commit -m "chore: checkpoint local dashboard work before repo migration"
```
Expected: local checkpoint commit created successfully.

- [ ] **Step 3: Verify working tree is clean after checkpoint**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git status --short --branch
```
Expected: no modified or untracked files.

### Task 3: Repair dashboard remote and branch tracking

**Files:**
- Modify: `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard/.git/config`

- [ ] **Step 1: Point `origin` to the correct GitHub repo**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git remote set-url origin https://github.com/annara7md/sawa-dashboard.git
```
Expected: command succeeds without output.

- [ ] **Step 2: Fetch remote state**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git fetch origin --prune
```
Expected: remote refs refresh.

- [ ] **Step 3: Compare local `main` vs remote `main`**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git log --graph --oneline --decorate --all --max-count=50
git branch -vv
```
Expected: clear picture of whether remote is empty, behind, or unrelated.

- [ ] **Step 4: Apply the appropriate reconciliation**

Recommended default if remote is empty or does not contain needed work:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git push -u origin main
```
Alternative if histories are unrelated but both must be kept:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git pull origin main --allow-unrelated-histories
```
Expected: dashboard remote matches intended repo and local work is preserved.

- [ ] **Step 5: Verify dashboard repository health**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
git status
git branch -vv
git remote -v
```
Expected: clean working tree, correct remote, tracked `main` branch.

## Chunk 3: Initialize `sawa-backend`

### Task 4: Create a fresh backend repository from current files

**Files:**
- Modify: `/Users/fahmifareed/Documents/sawa-main/sawa-backend/.git`

- [ ] **Step 1: Initialize Git in backend**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git init
```
Expected: repository initialized.

- [ ] **Step 2: Create initial backend commit**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git add .
git commit -m "chore: initialize sawa-backend repository"
```
Expected: first backend commit created.

- [ ] **Step 3: Normalize branch name**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git branch -M main
```
Expected: active branch becomes `main`.

- [ ] **Step 4: Attach backend remote**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git remote add origin https://github.com/annara7md/sawa-backend.git
```
Expected: origin configured.

- [ ] **Step 5: Push backend upstream**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git push -u origin main
```
Expected: backend repo published and tracking set.

- [ ] **Step 6: Verify backend repository health**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
git status
git branch -vv
git remote -v
```
Expected: clean `main` branch tracking `origin/main`.

## Chunk 4: Normalize `sawa-app`

### Task 5: Convert app repo into a proper initialized repository

**Files:**
- Modify: `/Users/fahmifareed/Documents/sawa-main/sawa-app/.git`

- [ ] **Step 1: Confirm app has no commits yet**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git log --oneline
```
Expected: fail or return no commits.

- [ ] **Step 2: Create first app commit**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git add .
git commit -m "chore: initialize sawa-app repository"
```
Expected: first app commit created.

- [ ] **Step 3: Normalize branch name**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git branch -M main
```
Expected: branch is `main`.

- [ ] **Step 4: Attach app remote**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git remote add origin https://github.com/annara7md/sawa-app.git
```
Expected: origin configured.

- [ ] **Step 5: Push app upstream**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git push -u origin main
```
Expected: app repo published and tracking set.

- [ ] **Step 6: Verify app repository health**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
git status
git branch -vv
git remote -v
```
Expected: clean `main` branch tracking `origin/main`.

## Chunk 5: Create the root `sawa-main` repository

### Task 6: Initialize the coordination repository

**Files:**
- Create: `/Users/fahmifareed/Documents/sawa-main/README.md`
- Create: `/Users/fahmifareed/Documents/sawa-main/.gitignore`
- Modify: `/Users/fahmifareed/Documents/sawa-main/.git`

- [ ] **Step 1: Create root `.gitignore`**

Suggested contents:
```gitignore
.DS_Store
.vscode/
```
Expected: root ignores machine-specific files only.

- [ ] **Step 2: Write root README**

Create a concise architecture README describing:
- purpose of `sawa-main`
- submodule layout
- clone/update workflow
- where to run app-specific commands

- [ ] **Step 3: Initialize Git at root**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git init
```
Expected: root repo initialized.

- [ ] **Step 4: Create first root commit**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git add README.md .gitignore memory
git commit -m "chore: initialize sawa-main coordination repository"
```
Expected: root repo contains docs and shared memory only.

- [ ] **Step 5: Normalize branch and attach remote**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git branch -M main
git remote add origin https://github.com/annara7md/sawa-main.git
```
Expected: root branch is `main` and remote is configured.

- [ ] **Step 6: Push root upstream**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git push -u origin main
```
Expected: root repo published and tracking set.

## Chunk 6: Attach submodules cleanly

### Task 7: Register child repositories as submodules in root

**Files:**
- Create: `/Users/fahmifareed/Documents/sawa-main/.gitmodules`

- [ ] **Step 1: Add dashboard submodule**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git submodule add https://github.com/annara7md/sawa-dashboard.git sawa-dashboard
```
Expected: dashboard registered as submodule.

- [ ] **Step 2: Add backend submodule**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git submodule add https://github.com/annara7md/sawa-backend.git sawa-backend
```
Expected: backend registered as submodule.

- [ ] **Step 3: Add app submodule**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git submodule add https://github.com/annara7md/sawa-app.git sawa-app
```
Expected: app registered as submodule.

- [ ] **Step 4: Commit submodule wiring**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git add .gitmodules sawa-dashboard sawa-backend sawa-app
git commit -m "chore: add sawa project submodules"
```
Expected: submodule references committed.

- [ ] **Step 5: Push updated root**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git push
```
Expected: root repo updated with submodule references.

## Chunk 7: Verify integrity and tooling

### Task 8: Verify Git integrity across all repositories

**Files:**
- Verify: `/Users/fahmifareed/Documents/sawa-main/.gitmodules`

- [ ] **Step 1: Verify root submodule status**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git submodule status
git submodule update --init --recursive
```
Expected: all submodules initialized at valid commits.

- [ ] **Step 2: Verify each repository health**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard && git status && git remote -v
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend && git status && git remote -v
cd /Users/fahmifareed/Documents/sawa-main/sawa-app && git status && git remote -v
```
Expected: all repos are clean and point to the correct remotes.

### Task 9: Validate project tooling at repository boundaries

**Files:**
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-dashboard/package.json`
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-backend/pyproject.toml`
- Verify: `/Users/fahmifareed/Documents/sawa-main/sawa-app/pubspec.yaml`

- [ ] **Step 1: Validate dashboard tooling**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-dashboard
pnpm install
pnpm build
```
Expected: Husky installs in dashboard repo context and build completes or produces actionable project-level errors.

- [ ] **Step 2: Validate backend tooling**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-backend
uv sync
python manage.py check
```
Expected: backend installs and Django configuration check passes, or errors are clearly application-specific.

- [ ] **Step 3: Validate app tooling**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main/sawa-app
flutter pub get
flutter analyze
```
Expected: app resolves dependencies and analyzer output is captured.

## Chunk 8: Final documentation and handoff

### Task 10: Finalize root README for long-term workflow

**Files:**
- Modify: `/Users/fahmifareed/Documents/sawa-main/README.md`

- [ ] **Step 1: Ensure README includes cloning instructions**

README must include:
```bash
git clone --recurse-submodules https://github.com/annara7md/sawa-main.git
```

- [ ] **Step 2: Ensure README includes submodule update instructions**

README must include:
```bash
git submodule update --init --recursive
git submodule update --remote --merge
```

- [ ] **Step 3: Ensure README includes developer workflow**

README must explain:
- edit each project inside its own repo
- commit inside child repo first
- then commit updated submodule pointer in `sawa-main`

- [ ] **Step 4: Final verification sweep**

Run:
```bash
cd /Users/fahmifareed/Documents/sawa-main
git status
git log --graph --oneline --decorate --all --max-count=30
git submodule status
```
Expected: root is clean, submodule refs are committed, and migration is complete.
