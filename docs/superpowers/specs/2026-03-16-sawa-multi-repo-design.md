# SAWA Multi-Repository Submodule Migration Design

**Date:** 2026-03-16
**Status:** Approved design awaiting implementation review

## Goal

Transform the local `sawa-main` directory into a production-grade multi-repository layout where:

- `sawa-main` is the coordination repository.
- `sawa-dashboard`, `sawa-backend`, and `sawa-app` are independent repositories.
- `sawa-main` references those three projects via Git submodules.
- existing project files are preserved.
- Git state is repaired before restructuring.

## Current State Summary

### Directory layout

Current local root:

- `/Users/fahmifareed/Documents/sawa-main/`

Current children:

- `memory/`
- `sawa-dashboard/`
- `sawa-backend/`
- `sawa-app/`

### Git state discovered

- `sawa-main/` is **not** a Git repository.
- `sawa-backend/` is **not** a Git repository.
- `sawa-app/` has `.git` but **no commits**, **no remote**, and all files are untracked.
- `sawa-dashboard/` is the only active Git repository.

### Dashboard-specific issues

Inside `sawa-dashboard/`:

- branch: `main`
- local `HEAD`: `2b2a331 first commit`
- remote configured as: `git@github.com:annara7md/sawaa.git`
- remote-tracking history exists locally on `origin/main` and is much newer than local `HEAD`
- working tree contains modified and untracked files

This indicates at least one of the following likely happened:

- the wrong GitHub repository was configured as `origin`
- local branch was reset or re-initialized incorrectly
- push/pull attempts likely would fail or create confusion because the remote identity does not match the intended project name `sawa-dashboard`

### Tooling-related observations

- `sawa-dashboard` has Husky configured using `core.hooksPath=.husky`
- `sawa-dashboard/package.json` contains `prepare: is-ci || husky install`
- Husky itself is not broken by design, but it is sensitive to the Git root of the dashboard repository and should remain local to `sawa-dashboard`
- `sawa-main` should not become a Node workspace root at this stage

## Desired Final Architecture

```text
sawa-main/
  .git
  .gitmodules
  README.md
  memory/
  sawa-dashboard/    # git submodule
  sawa-backend/      # git submodule
  sawa-app/          # git submodule
```

### Repository roles

#### `sawa-main`

Purpose:

- top-level coordination repository
- shared documentation (`memory/`)
- submodule pinning and update orchestration

It should **not** contain application source code directly beyond shared docs and repo-level metadata.

#### `sawa-dashboard`

Purpose:

- web admin/dashboard project
- independent Git repository
- independent build and install lifecycle

#### `sawa-backend`

Purpose:

- backend/API project
- independent Git repository
- independent deployment and versioning lifecycle

#### `sawa-app`

Purpose:

- mobile app project
- independent Git repository
- independent Flutter lifecycle

## Design Decisions

### 1. Keep `memory/` in `sawa-main`

`memory/` appears to be shared documentation across projects. It should stay in the root repository instead of being tied to one subproject.

### 2. Preserve dashboard local work before any repair

Because `sawa-dashboard` is the only repo with real Git history and also has uncommitted work, the first protective action during implementation must be one of:

- a local safety commit, or
- a local stash with message

Recommended: create a local safety commit so nothing is lost and future divergence inspection remains visible.

### 3. Treat backend and app as first clean initializations

Because:

- `sawa-backend` has no `.git`
- `sawa-app` has `.git` but no commits/history to preserve

both should be normalized as freshly initialized repositories tied to their intended GitHub remotes.

### 4. Use `sawa-main` as submodule coordinator only

No pnpm workspace or shared lifecycle should be imposed at root. Developers should work inside each sub-repository directly.

### 5. Keep Husky local to dashboard

`Husky` should remain in `sawa-dashboard` only. It should not be moved to `sawa-main`.

## Implementation Strategy

### Phase A — Repair `sawa-dashboard`

1. Inspect full status and divergence.
2. Preserve current uncommitted work with a local safety commit.
3. Replace incorrect `origin` with the intended remote:
   - `https://github.com/annara7md/sawa-dashboard`
4. Fetch remote and compare local/remote histories.
5. Choose the least destructive alignment strategy:
   - if remote is empty: push local branch
   - if remote has unrelated history: explicitly merge or replace only after confirming contents
   - if remote has correct history but local branch is behind/wrong: reconcile without losing local working files

### Phase B — Initialize `sawa-backend`

1. Create `.git`
2. create first commit from current files
3. set branch to `main`
4. set remote to:
   - `https://github.com/annara7md/sawa-backend`
5. push upstream

### Phase C — Normalize `sawa-app`

1. inspect current `.git`
2. create first real commit from current files
3. set branch to `main`
4. set remote to:
   - `https://github.com/annara7md/sawa-app`
5. push upstream

### Phase D — Create `sawa-main`

1. initialize Git at `/Users/fahmifareed/Documents/sawa-main`
2. add root-level files only:
   - `README.md`
   - `memory/`
   - `.gitignore` as needed
3. create initial commit
4. set remote to:
   - `https://github.com/annara7md/sawa-main`

### Phase E — Attach submodules

Add:

- `sawa-dashboard`
- `sawa-backend`
- `sawa-app`

as Git submodules in `sawa-main`.

### Phase F — Verify integrity

Validate:

- `.gitmodules` correctness
- submodule URLs
- submodule status
- recursive init/update
- no nested Git conflicts

### Phase G — Document developer workflow

Create a root README that documents:

- repo architecture
- clone with submodules
- submodule update commands
- daily development workflow
- where to run dashboard/backend/app commands

## Risk Management

### Main risks

1. losing uncommitted dashboard work
2. pointing dashboard at the wrong remote again
3. creating nested Git confusion by initializing `sawa-main` before subprojects are stable
4. assuming remote emptiness without fetching

### Mitigations

- do not delete files
- do not run destructive reset commands by default
- fetch before remote reconciliation
- commit/stash before modifying Git wiring
- initialize root repo only after the three child repos are individually healthy

## Testing and Verification Plan

After implementation, verify with:

### Git verification

For each repository:

```bash
git status
git branch -vv
git remote -v
git log --graph --oneline --decorate --all
```

For root:

```bash
git submodule status
git submodule update --init --recursive
```

### Tooling verification

Dashboard:

```bash
pnpm install
pnpm build
```

Backend:

Run project-appropriate install/build checks after repo initialization.

App:

Run project-appropriate Flutter dependency and build validation after repo initialization.

## Expected Outcome

At the end of implementation:

- all 4 GitHub repositories are wired correctly
- `sawa-dashboard`, `sawa-backend`, and `sawa-app` are independent repositories
- `sawa-main` tracks them as submodules
- shared docs remain at root
- local development becomes predictable and maintainable

## Non-Goals

This migration does **not** include:

- merging app/backend/dashboard into a monorepo
- introducing pnpm workspaces at root
- changing internal application architecture
- refactoring application code unrelated to Git migration
