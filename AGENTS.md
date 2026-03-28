# Repository Guidelines

## Project Structure & Module Organization

This repository is a ZMK firmware module for the Cornix keyboard. Core board definitions live in `boards/jzf/cornix/` and custom shields live in `boards/shields/`. User-facing firmware configuration is in `config/`, including keymaps (`*.keymap`), build manifest data in [build.yaml](/Users/rv/repos/zmk-keyboard-cornix/build.yaml), and `west.yml` under `config/`. Bootloader recovery assets are in `bootloader/`, reference images in `images/`, and Nix environment files at the repo root (`flake.nix`, `flake.lock`).

## Build, Test, and Development Commands

Use `just` for local workflows:

- `just init` initializes the local `west` workspace and Zephyr export.
- `just build all` builds every target declared in [build.yaml](/Users/rv/repos/zmk-keyboard-cornix/build.yaml).
- `just build cornix_left` builds matching targets by artifact, board, or shield expression.
- `just list` prints the available build targets.
- `just draw cornix` renders a keymap SVG from `config/cornix.keymap`.
- `just clean` removes `.build/` and `firmware/`.

GitHub Actions also builds firmware on pushes touching `boards/` or `config/`.

## Coding Style & Naming Conventions

Match existing ZMK and Zephyr file patterns. Use 2-space indentation in YAML and 4 spaces in `Justfile` recipes. Keep DTS/Kconfig names board- and shield-specific, for example `cornix_left_defconfig`, `Kconfig.shield`, and `cornix_dongle_adapter.overlay`. Name build artifacts with descriptive, hardware-specific suffixes such as `cornix_right_nosd`.

## Testing Guidelines

CI validation is primarily build-based: changes should compile for affected targets in [build.yaml](/Users/rv/repos/zmk-keyboard-cornix/build.yaml). The `Justfile` also provides `just test <path-to-test-config>` for native ZMK event snapshot tests when adding dedicated test fixtures. For config changes, verify at least one local build for the touched board or shield before opening a PR.

## Commit & Pull Request Guidelines

Recent history uses short, imperative commit messages such as `update read me`, `migrate to zephyr4`, and `add nosd for build ouputs`. Prefer concise subject lines describing the change scope, for example `add cornix indicator shield docs`. PRs should include:

- a brief summary of hardware or config impact
- linked issue or rationale for the change
- the exact build target(s) tested
- screenshots only when updating docs or generated layout visuals

## Configuration Notes

Avoid committing unrelated generated files. Current local changes in `config/` are what trigger CI most reliably, so keep board and keymap edits scoped and intentional.
