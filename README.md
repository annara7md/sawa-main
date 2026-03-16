# sawa-main

Top-level coordination repository for the SAWA platform.

## Architecture

This repository does not contain application source code directly.
It coordinates the three project repositories as Git submodules:

- `sawa-dashboard/` — admin dashboard
- `sawa-backend/` — backend API and services
- `sawa-app/` — mobile application

Shared cross-project notes and documentation live in:

- `memory/`
- `docs/`

## Clone

```bash
git clone --recurse-submodules git@github.com:annara7md/sawa-main.git
cd sawa-main
```

If submodules were not cloned initially:

```bash
git submodule update --init --recursive
```

## Update Submodules

To sync submodule pointers recorded by `sawa-main`:

```bash
git submodule update --init --recursive
```

To pull the latest remote changes inside submodules:

```bash
git submodule update --remote --merge
```

## Developer Workflow

Work inside each project repository directly:

- dashboard work happens inside `sawa-dashboard/`
- backend work happens inside `sawa-backend/`
- app work happens inside `sawa-app/`

Typical workflow:

1. enter the child repository you want to change
2. commit and push changes there first
3. return to `sawa-main`
4. commit the updated submodule pointer in `sawa-main`

## Notes

- `sawa-main` is the coordination layer, not a monorepo workspace
- Husky and package/tooling remain local to each child repository
- shared planning and migration docs are intentionally kept at the root level
