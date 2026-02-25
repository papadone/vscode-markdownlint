---
name: build-and-package
description: Use this skill to build and package the VS Code extension. Runs npm run compile and npx vsce package, captures errors, and stops on failure.
---
# Build & Package runbook

## Commands (Windows / PowerShell)
- npm install
- npm run compile
- npx vsce package

## Failure policy
- If compile fails: fix compile before attempting package.
- If package fails: read the error, fix, and re-run package.
- Never propose "ignore the error".

## Artifacts
- VSIX must be produced in repo root.
- Report the output file name and path.
