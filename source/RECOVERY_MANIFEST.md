# Recovery Manifest

Original input:

- `../HumanType.app`

Copied app bundles:

- `../extracted/HumanType.original.app`
- `app-bundle/HumanType.app`

Recovered entry point:

- PyInstaller script name: `autotyper`
- Embedded source filename: `autotyper.py`
- Python bytecode version: 3.13
- Top-level app name: `HumanType`
- Bundle identifier: `com.humantype.app`

Known runtime dependencies from recovered imports:

- `tkinter`
- `pyperclip`
- `pynput`
- `certifi`
- `ApplicationServices` / `Quartz` on macOS through PyObjC

Generated recovery artifacts:

- `recovered/autotyper.code-summary.json`
- `recovered/PYZ.contents.txt`

Local-only ignored artifacts:

- `app-bundle/HumanType.app`
- `recovered/autotyper.raw.pyc`
- `recovered/autotyper.pyc`
- `recovered/autotyper.dis`
- `recovered/autotyper.full.dis`
- `recovered/autotyper.strings.txt`
- `recovered/PYZ.pyz`
