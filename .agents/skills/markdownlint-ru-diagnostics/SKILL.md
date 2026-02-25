---
name: markdownlint-ru-diagnostics
description: Use this skill when the task is to localize markdownlint diagnostics (Problems) to Russian. Translate by ruleId (MDxxx), keep original details, add a language setting markdownlint.messageLanguage.
---
# markdownlint diagnostics RU localization

## Goal
Russian prefix for markdownlint diagnostic messages in VS Code Problems view.

## Requirements
- Translate ONLY by ruleId (MD001..).
- Message format:
  - `${ruleId}: ${ruText}. ${originalDetails}`
- If ruText missing: leave message unchanged.
- Add setting:
  - markdownlint.messageLanguage: en|ru (default en), scope application.
- Do not change lint behavior; change only message rendering.

## Implementation plan (strict)
1) Find where `vscode.Diagnostic.message` is constructed.
2) Add RU dictionary (json or ts map).
3) Add localizer function:
   - input: ruleId, originalMessage, lang
   - output: localizedMessage
4) Wire localizer into the diagnostic creation path.
5) Verify:
   - npm run compile
   - npx vsce package
6) Provide a minimal smoke test snippet that triggers MD056.

## Non-goals
- UI translation of VS Code or extension markdown docs.
- Translating markdownlint rule docs.
