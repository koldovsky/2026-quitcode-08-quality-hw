# Здача WS8

## Дані

- Роль: dev
- Команда: school-purchasing
- GitHub-логін: YarynaPankivv
- Ваше репо: https://github.com/YarynaPankivv/school-purchasing
- SHA: 26eda178e6a6c488a3e4f9d703fa14abfb31839a
- Репо вимог PM: https://github.com/ValiaBihun/2026-quitcode-dream-team
- Прод-URL: https://school-purchasing.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://school-purchasing.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/YarynaPankivv/school-purchasing/actions/runs/41639491268
- `accounts.zip` на SHA: https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/accounts.zip
- Ролі тестових акаунтів: адміністратор — admin@example.test, pm-admin@example.test; працівник — member1@example.test, member2@example.test, approver@example.test, pm-requester@example.test, pm-approver@example.test; працівник без відділів — pm-empty@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-FRM-09 (відмова в браузері: гість без входу), AC-FRM-14 (стан інтерфейсу: порожній список «Мої заявки»), AC-APR-03 (відмова в браузері: чужі дані за прямим посиланням)
- QA proof pack: https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/YarynaPankivv/school-purchasing/pull/47
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/YarynaPankivv/school-purchasing/actions/runs/41663140240
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога» додано в ruleset 02.11.2026 (поруч зі `spec`, `app`, `conformance`, `db-check`); «Порада: вразливі залежності» не обов'язкова — запис у proof pack https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/docs/qa/proof-pack.md#L27, PR воріт https://github.com/YarynaPankivv/school-purchasing/pull/47
- Якість тестів — PR (B): https://github.com/YarynaPankivv/school-purchasing/pull/48
- Якість тестів — убитий мутант (B): `src/lib/supabase/proxy.ts:24–44` (гілка гостя в `updateSession`, NoCoverage) → AC-FRM-09 → тест https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/tests/auth/proxy-guest.test.ts#L18
- SQL-мутація (B): https://github.com/YarynaPankivv/school-purchasing/pull/48 — вивід `npm run mutation:sql`: 5 з 6 мутантів убито, 1 прийнято як еквівалентний (F1) з поясненням
- UAT — специфікації (C): https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/tests/e2e/slice2.spec.ts, https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/tests/e2e/negative-controls.spec.ts
- UAT — звіт на проді (C): https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/YarynaPankivv/school-purchasing/pull/49
- UAT — негативний контроль (C): https://github.com/YarynaPankivv/school-purchasing/pull/49 — NC-1 (AC-FRM-14) → FAIL, NC-2 (AC-FRM-09) → NEEDS-HUMAN
- Рядки `docs/conformance.md` (C): AC-FRM-09 (реалізовано) https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/docs/conformance.md#L155, AC-APR-03 (реалізовано) https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/docs/conformance.md#L158, AC-FRM-14 (реалізовано) https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/docs/conformance.md#L173; рядків «відкладено (e2e — WS8)» не лишилось
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/YarynaPankivv/school-purchasing/pull/52
- Eval рецензента — таблиця й ключ (D): https://github.com/YarynaPankivv/school-purchasing/pull/52#issuecomment-6578245575
- Eval рецензента — правило й повторний прогін (D): правило — коміт https://github.com/YarynaPankivv/school-purchasing/commit/b75262a9e1a5d59487a5af7cbb8b83d36bbfd507 (PR https://github.com/YarynaPankivv/school-purchasing/pull/53); повторний прогін — https://github.com/YarynaPankivv/school-purchasing/pull/54#issuecomment-6581159803
- Відхилення від PM (C): не надходило

## Бонус

UAT у CI: зелений прогін `workflow_dispatch` специфікацій `tests/e2e/*.spec.ts` на одноразовому Supabase у раннері: https://github.com/YarynaPankivv/school-purchasing/actions/runs/41664169418 на фінальному SHA (7 пройшли, 0 впали, 0 пропущено, 0 нестабільних; звіт і записи — артефактом; перший зелений прогін — https://github.com/YarynaPankivv/school-purchasing/actions/runs/41620421190). Workflow `e2e.yml` — https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/.github/workflows/e2e.yml, сід даних для AC-APR-03 — https://github.com/YarynaPankivv/school-purchasing/blob/26eda178e6a6c488a3e4f9d703fa14abfb31839a/scripts/e2e-seed.mjs, PR https://github.com/YarynaPankivv/school-purchasing/pull/56, опис — розділ «Бонус: UAT у CI» у proof pack. Висновок: без сіда AC-APR-03 у CI тільки пропускався; із сідом виконується, а крок «no skipped tests» валить прогін при будь-якому пропуску. Після merge e2e показав флейк очікування сторінки (скелет «Loading…»), виправлено в https://github.com/YarynaPankivv/school-purchasing/pull/62.
