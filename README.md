# HumanType

HumanType is a macOS auto-typing app recovery project. The original workspace contained only a packaged `HumanType.app`, so this repository is being prepared as a clean editable rebuild rather than a dump of the bundled binary.

## Repository State

This repo currently contains:

- app metadata and icons recovered from the packaged app
- dependency notes for running/building the rebuilt app
- recovery manifests and code-object summaries to guide source reconstruction

This repo intentionally does not track:

- copied `.app` bundles
- extracted PyInstaller archives
- raw Python bytecode
- string/disassembly dumps that may include embedded service configuration

## Next Step

Rebuild the editable application source under `src/`, using the local recovery artifacts and the packaged app behavior as reference.
