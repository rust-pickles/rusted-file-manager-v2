# RUSTED

RUSTED is a Windows 10/11 x64 file manager in development. This repository
contains the AI Studio React interface and the existing Rust engine workspace.
The frontend currently uses an in-memory mock filesystem; it is **not** yet
connected to the Rust engine and is not a desktop application. The Rust app and
GPUI frontend crates are currently stubs. GPUI remains declared pending a later,
separately approved migration to Tauri.

## Layout

- `frontend/` — React, TypeScript, Vite and Tailwind UI.
- `crates/` — existing Rust workspace crates, including `rusted-app` and
  `rusted-ui`. The root `Cargo.toml` defines the workspace.
- `.github/workflows/ci.yml` — Windows frontend and Rust checks.

No `src-tauri/` exists yet: Tauri integration is deliberately outside Phase 0.
The original Rust repository remains an independent backup.

## Frontend

Use Node.js 22.12 or later (CI uses Node 22), with npm:

```sh
cd frontend
npm ci
npm run lint
npm run build
npm run dev
```

The committed `package-lock.json` is the frontend dependency lockfile.

## Rust

Use stable Rust (minimum 1.90) and the `x86_64-pc-windows-msvc` target on
Windows with the MSVC build tools:

```sh
cargo check --workspace --all-targets
cargo test --workspace
```

The workspace currently has no committed Cargo.lock; dependency resolution can
therefore vary between runs. These commands do not start an application yet.
