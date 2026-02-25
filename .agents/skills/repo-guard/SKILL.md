---
name: repo-guard
description: Use this skill for ANY change in this repository. It enforces minimal diffs, no dependency churn, and mandatory build/package verification. Never refactor unrelated code.
---
# Repo Guard (strict)

## Scope
This repository is a VS Code extension. Keep changes tightly scoped.

## Hard rules
- Do NOT reformat whole files.
- Do NOT rename folders or restructure unless explicitly required by the task.
- Do NOT update dependencies unless:
  1) build is broken, or
  2) security fix is required and verified not to break compilation.
- No "cleanup", "modernization", "upgrade" passes.

## Workflow
1) Identify the single smallest place to implement the change.
2) Make the minimal edit.
3) Run:
   - npm run compile
   - npx vsce package
4) If any command fails: stop, fix, re-run. Do not proceed until green.

## Output expectations
- Provide the exact files changed.
- Provide the exact commands run and their result.
