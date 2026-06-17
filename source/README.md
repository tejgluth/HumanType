# HumanType Recovery Copy

This folder is the working copy recovered from `HumanType.app`.

## What Was Copied Locally

- `app-bundle/HumanType.app/` is an exact local copy of the packaged macOS app.
- `Info.plist` is the app bundle metadata.
- `assets/icon.png` and `assets/icon.icns` are the bundled app icons.
- `recovered/autotyper.code-summary.json` lists functions/classes, line numbers, names, and locals.
- `recovered/PYZ.contents.txt` is the embedded PyInstaller dependency module list.

The raw copied app bundle, bytecode, dependency archive, string dumps, and disassembly dumps are intentionally ignored by Git. They are useful locally, but they are binary/noisy and may include embedded service configuration.

## Current State

The original editable `autotyper.py` source was not present in the workspace or inside the app bundle. The packaged app contains Python 3.13 bytecode, and the common local decompilers available here do not support Python 3.13 decompilation.

The recovered symbols show the draft app was a single-file Tkinter/Pynput app with:

- license activation through Supabase
- macOS permission onboarding
- launch-at-login setup
- global start/stop hotkeys
- humanized typing engine with typos, corrections, bursts, and hesitation
- presets, sliders, and calibration

The practical next step is to rebuild an editable `src/autotyper.py` from these recovered artifacts and the running app behavior.
