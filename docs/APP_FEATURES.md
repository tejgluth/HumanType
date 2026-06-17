# HumanType App Feature Inventory

This document describes the current packaged app behavior recovered from the local `HumanType.app`. It is intentionally written from push-safe metadata and recovered symbols, not from committed bytecode or embedded secrets.

## Product Summary

HumanType is a desktop auto-typer. It types clipboard text into the currently focused field while attempting to mimic human typing rhythm, including variable speed, hesitation, typos, corrections, and accidental key patterns.

## Core User Flow

1. User copies text from any app.
2. User clicks into the target field where the text should appear.
3. User starts typing from the HumanType window or global hotkey.
4. App waits through a configurable countdown.
5. App types the copied text into the active field.
6. User can stop/pause immediately, then resume from the same position or start over.

## Main Screens

- Guide: onboarding-style instructions for copying text, focusing a target field, starting, stopping, resuming, and tuning behavior.
- Settings: presets and sliders for speed, rhythm, mistakes, correction behavior, and launch delay.
- Calibrate: a typing sample screen that records user keystrokes and tunes the Natural preset to match observed typing style.
- License activation: modal gate shown when the app is not activated locally.
- OS permissions onboarding: modal guidance for macOS Accessibility and Input Monitoring permissions.

## Typing Behavior

Recovered symbols identify a `TypingEngine` that:

- uses `pynput.keyboard.Controller` for keystroke output
- reads clipboard text through `pyperclip`
- schedules typing through Tk timers so stopping can cancel the next pending keystroke quickly
- maintains current text, queue, position, count, stop state, and running state
- supports resume after a stop
- sanitizes typographic punctuation and whitespace before typing
- can emit wrong nearby keys
- can backspace and correct mistakes
- can double-press keys
- can transpose adjacent letters
- can add bursts and hesitation pauses

## Settings And Presets

Known presets:

- Careful
- Natural
- Fast
- Sloppy

Known slider groups:

- Speed and rhythm
- Imperfection
- Launch

Known controls:

- minimum keystroke delay
- maximum keystroke delay
- burst chance
- hesitation chance
- mistake frequency
- self-correction chance
- double-press chance
- transpose chance
- start delay
- launch at login

## Calibration

The app includes a calibration prompt and keystroke recorder. It records typed characters, spaces, enter presses, and backspaces, then computes settings such as:

- words per minute
- average key delay
- backspace frequency
- keystroke count

The resulting values tune the Natural preset.

## Global Hotkeys

The recovered UI text identifies these shortcuts:

- macOS start/resume: Command + Control + T
- macOS stop/pause: Command + Control + S
- Windows/Linux start/resume: Control + Alt + T
- Windows/Linux stop/pause: Control + Alt + S

Input Monitoring permission is required on macOS for global hotkeys.

## Platform Behavior

macOS:

- asks for Accessibility permission so the app can type
- asks for Input Monitoring permission so the global stop/start hotkeys work
- can reveal the app bundle in Finder for permission setup
- can open System Settings panes for Accessibility and Input Monitoring
- supports launch at login through a LaunchAgent

Windows:

- includes guidance for Windows Security if simulated typing is blocked
- supports launch at login through the current user's Run registry key

Linux:

- expects X11/Xorg for keystroke simulation
- warns that Wayland sessions may not work

## Licensing

The app has a local activation gate. Recovered symbols show:

- per-machine fingerprinting based on a hashed machine identifier
- local activation state saved in a JSON file under the user's home directory
- remote license activation through a Supabase RPC
- user-facing errors for empty keys, invalid keys, revoked keys, machine limit, network failure, SSL failure, and server failure

Actual service URL/key values are intentionally not committed to this repository.

## Build Shape

The packaged app is a PyInstaller macOS bundle built from a single Python entry point named `autotyper.py`.

Known dependencies:

- Python 3.13 in the packaged build
- Tkinter for UI
- `pynput` for keyboard control/global hotkeys
- `pyperclip` for clipboard access
- `certifi` for SSL certificate handling
- PyObjC ApplicationServices/Quartz for macOS permission checks

## Current GitHub Limitations

The GitHub repo does not contain the full editable original source. It contains enough recovery metadata to understand the app architecture and feature set, but another agent would still need either:

- the local ignored recovery artifacts in this workspace, or
- a reconstructed `src/autotyper.py`

before it could build or modify the full app from GitHub alone.
