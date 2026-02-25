# TASKS.md

## Правила работы (обязательные)
1) Работать маленькими диффами.
2) Не менять форматирование файлов массово.
3) После каждого милстоуна запускать проверки:
   - npm run compile
   - npx vsce package

## M1 — Инвентаризация (1 проход)
- [ ] Найти место в коде, где создаётся `new vscode.Diagnostic(...)` и назначается `.message`.
- [ ] Выписать: какие строки составляют message сейчас (ruleName, description, detail).

## M2 — Словарь RU
- [ ] Создать `src/i18n/ru.json` (или эквивалент) с ключами `MD001..`.
- [ ] Заполнить минимум: MD001, MD003, MD007, MD009, MD010, MD012, MD013, MD022, MD024, MD025, MD029, MD031, MD032, MD033, MD034, MD036, MD040, MD041, MD046, MD056.
- [ ] Формат: “краткое описание сути правила”.

## M3 — Настройка языка
- [ ] В `package.json` добавить настройку:
  - `markdownlint.messageLanguage`: enum `["en","ru"]`, default `en`, scope `application`.

## M4 — Внедрить локализацию в diagnostics
- [ ] Реализовать функцию:
  - input: `ruleId`, `originalMessage`, `lang`
  - output: `ruleId: <ru>. <rest>`
- [ ] Интегрировать в точку формирования `Diagnostic.message`.
- [ ] Fallback: если ru-строки нет — вернуть original.

## M5 — Сборка и упаковка
- [ ] npm run compile
- [ ] npx vsce package
- [ ] Smoke test в VS Code:
  - включить `"markdownlint.messageLanguage": "ru"`
  - создать ошибку MD056 (таблица с разным числом колонок)
  - убедиться, что сообщение начинается с RU-префикса.

## M6 — Документация (минимум)
- [ ] README: 3 строки как включить ru.
