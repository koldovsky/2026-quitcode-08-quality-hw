# Здача WS8

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: vhrytsyndyshynquitcode
- Ваше репо: https://github.com/vhrytsyndyshynquitcode/property-workflows
- SHA: d81decfdeefedefbe1ad89c5502c5da4bbd37380
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows-one.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://property-workflows-one.vercel.app/api/health — `{"ok":true,"sha":"d81decfdeefedefbe1ad89c5502c5da4bbd37380","env":"production","db":"ok"}` на момент здачі
- Зелений прогін `smoke` на `main`: https://github.com/vhrytsyndyshynquitcode/property-workflows/actions/runs/41431356035 (після розгортання `d81decf`); ручний прогін — https://github.com/vhrytsyndyshynquitcode/property-workflows/actions/runs/41412858327
- `accounts.zip` на SHA: https://github.com/vhrytsyndyshynquitcode/property-workflows/blob/d81decfdeefedefbe1ad89c5502c5da4bbd37380/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test; менеджер — pm-manager@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-EDITOR-07 (відмова в браузері: заборонена роль), AC-EDITOR-09 (відмова в браузері: не увійшов), AC-EDITOR-19 (стан інтерфейсу: помилка «Enter a template name»)
- QA proof pack: https://github.com/vhrytsyndyshynquitcode/property-workflows/blob/d81decfdeefedefbe1ad89c5502c5da4bbd37380/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/32
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/vhrytsyndyshynquitcode/property-workflows/actions/runs/41431301645 (на SHA здачі); перший зелений — https://github.com/vhrytsyndyshynquitcode/property-workflows/actions/runs/41413070904
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога» — з 02.11.2026 (разом зі `spec`, `app`, `conformance`, `db-check`); «Порада: вразливі залежності» — дорадча
- Якість тестів — PR (B): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/33
- Якість тестів — убитий мутант (B): `src/app/templates/actions.ts:46` `if (!name)` → `if (name === null)` (T19) → AC-EDITOR-19 → https://github.com/vhrytsyndyshynquitcode/property-workflows/blob/d81decfdeefedefbe1ad89c5502c5da4bbd37380/tests/templates/editor-actions.test.ts#L66 — на тестах `main` до PR вижив, після — убитий
- SQL-мутація (B): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/33 — E19 (`20261020073540_workflow_runs.sql:50`, `length(btrim(name)) > 0` → `length(name) > 0`, AC-EDITOR-19): SURVIVED → KILLED тестом https://github.com/vhrytsyndyshynquitcode/property-workflows/blob/d81decfdeefedefbe1ad89c5502c5da4bbd37380/tests/db/template-editor-oct27.test.ts#L108; E09 (`grant select … to anon`, AC-EDITOR-09): KILLED
- UAT — специфікації (C): https://github.com/vhrytsyndyshynquitcode/property-workflows/blob/d81decfdeefedefbe1ad89c5502c5da4bbd37380/tests/e2e/templates.spec.ts
- UAT — звіт на проді (C): https://github.com/vhrytsyndyshynquitcode/property-workflows/blob/d81decfdeefedefbe1ad89c5502c5da4bbd37380/docs/qa/uat/2026-11-02/report.md — 3 AC: PASS (R6)
- UAT — PR зі звітом і відео (C): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/36
- UAT — негативний контроль (C): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/36 — NC-1 (AC-EDITOR-07, хибний текст у твердженні) → FAIL (R1); NC-2 (AC-EDITOR-07, «уточнений» `ac-text`) → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-EDITOR-07 (реалізовано), AC-EDITOR-09 (реалізовано), AC-EDITOR-19 (реалізовано) — у кожному додано `tests/e2e/templates.spec.ts` (UAT); рядків `відкладено (e2e — WS8)` у матриці не було
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/37
- Eval рецензента — таблиця й ключ (D): https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/37#issuecomment-6574733748
- Eval рецензента — правило й повторний прогін (D): правило — https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/38; повторний прогін — https://github.com/vhrytsyndyshynquitcode/property-workflows/pull/37#issuecomment-6575137471 (`/code-review` загострив ваду 2 до «must fix, Critical», CodeRabbit лишив Low)
- Відхилення від PM (C): не надходило

## Бонус

—
