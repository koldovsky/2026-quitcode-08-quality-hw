# Здача WS8

## Дані

- Роль: dev
- Команда: leave-portal
- GitHub-логін: lukian-tomochko
- Ваше репо: https://github.com/lukian-tomochko/leave-portal
- SHA: 1b5beca870c2f1e77dca7000180437fbbc19c31f
- Репо вимог PM: https://github.com/mkozlovskyi-ops/course-staff-management-spec
- Прод-URL: https://leave-portal-blush.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://leave-portal-blush.vercel.app/api/health — `{"ok":true,"sha":"1b5beca870c2f1e77dca7000180437fbbc19c31f","env":"production","db":"ok","reason":""}` (sha збігається з `main` на момент здачі)
- Зелений прогін `smoke` на `main`: https://github.com/lukian-tomochko/leave-portal/actions/runs/41607858206
- `accounts.zip` на SHA: https://github.com/lukian-tomochko/leave-portal/blob/1b5beca870c2f1e77dca7000180437fbbc19c31f/accounts.zip
- Ролі тестових акаунтів: працівник — teacher1@example.test, teacher2@example.test; менеджер — manager1@example.test, manager2@example.test; адміністратор — admin@example.test. Паролі — лише в accounts.zip
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-BALANCE-13 (відмова в браузері, чужі дані), AC-DECIDE-14 (стан інтерфейсу: порожній список), AC-BALANCE-01 (початкові баланси, лише читання). Зріз 2 — «рішення менеджера й баланс». AC-DECIDE-12 і AC-DECIDE-08 додатково доведені мутацією, але без UAT: для AC-DECIDE-12 потрібен схвалений запис (запис у спільний прод), «Тоді» AC-DECIDE-08 невидиме в браузері
- QA proof pack: https://github.com/lukian-tomochko/leave-portal/blob/1b5beca870c2f1e77dca7000180437fbbc19c31f/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/lukian-tomochko/leave-portal/pull/36
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/lukian-tomochko/leave-portal/actions/runs/41607808908
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога» додано 03.11.2026 о 10:37 за Києвом (ruleset `solo-main`: `spec`, `app`, `conformance`, `db-check` + ці дві); «Порада: вразливі залежності» не обов'язкова
- Якість тестів — PR (B): https://github.com/lukian-tomochko/leave-portal/pull/37
- Якість тестів — убитий мутант (B): `src/lib/leave/decision.ts:183` (`if (error instanceof DecisionDeniedError)` → `if (true)`) → AC-DECIDE-08 → тест https://github.com/lukian-tomochko/leave-portal/blob/1b5beca870c2f1e77dca7000180437fbbc19c31f/src/lib/leave/decision.test.ts#L253; для AC-BALANCE-01 ручні мутанти (`GRANTED_CENTS` 1800 → 1700 тощо) убиті `src/lib/leave/balance.test.ts`, див. proof pack
- SQL-мутація (B): https://github.com/lukian-tomochko/leave-portal/pull/37 — вивід `npm run mutation:sql`: S1, S2, S3 KILLED, S1b еквівалентний (прийнято)
- UAT — специфікації (C): https://github.com/lukian-tomochko/leave-portal/blob/1b5beca870c2f1e77dca7000180437fbbc19c31f/tests/e2e/balances.spec.ts, https://github.com/lukian-tomochko/leave-portal/blob/1b5beca870c2f1e77dca7000180437fbbc19c31f/tests/e2e/decisions.spec.ts
- UAT — звіт на проді (C): https://github.com/lukian-tomochko/leave-portal/blob/1b5beca870c2f1e77dca7000180437fbbc19c31f/docs/qa/uat/2026-11-02/report.md — AC-BALANCE-01, AC-BALANCE-13, AC-DECIDE-14: PASS (R6)
- UAT — PR зі звітом і відео (C): https://github.com/lukian-tomochko/leave-portal/pull/39 (перший прогін без агента — https://github.com/lukian-tomochko/leave-portal/pull/38)
- UAT — негативний контроль (C): https://github.com/lukian-tomochko/leave-portal/pull/39 — NC-1 → FAIL (R1), NC-2 → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-BALANCE-01 (реалізовано), AC-BALANCE-13 (реалізовано), AC-DECIDE-14 (реалізовано), усі зі шляхом до специфікації в `tests/e2e/`; рядків `відкладено (e2e — WS8)` у матриці не було
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/lukian-tomochko/leave-portal/pull/40 (закрито без злиття)
- Eval рецензента — таблиця й ключ (D): https://github.com/lukian-tomochko/leave-portal/pull/40#issuecomment-6598424934
- Eval рецензента — правило й повторний прогін (D): правило https://github.com/lukian-tomochko/leave-portal/commit/e78a5a79731fe40e3053fbf85cefc99ab0afed23 (PR https://github.com/lukian-tomochko/leave-portal/pull/41); повторний прогін CodeRabbit знайшов пропущену ваду https://github.com/lukian-tomochko/leave-portal/pull/40#issuecomment-6599444888
- Відхилення від PM (C): не надходило станом на 2026-11-03 (issues «Відхилення від вимог» у репо немає). Виправлення після здачі — коментарем «Виправлено: …» у тому ж issue до кінця Сб 07.11

## Бонус

—
