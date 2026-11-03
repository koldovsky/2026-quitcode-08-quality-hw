# Здача WS8

## Дані

- Роль: dev
- Команда: therapy-scheduling
- GitHub-логін: maryan-qc
- Ваше репо: https://github.com/maryan-qc/therapy-scheduling
- SHA: d34c516a7cd1b4b1811ecd103928e740415e2ee1
- Репо вимог PM: https://github.com/Sofiia-pm/therapy-scheduling-spec
- Прод-URL: https://therapy-scheduling-sigma.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://therapy-scheduling-sigma.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/maryan-qc/therapy-scheduling/actions/runs/41687032800
- `accounts.zip` на SHA: https://github.com/maryan-qc/therapy-scheduling/blob/d34c516a7cd1b4b1811ecd103928e740415e2ee1/accounts.zip
- Ролі тестових акаунтів: адміністратор — admin1@example.test, pm-admin@example.test, admin@example.test; планувальник — scheduler1@example.test, scheduler2@example.test, pm-scheduler@example.test; терапевт — therapist1@example.test, therapist2@example.test, pm-therapist@example.test; без ролі — newuser1@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-CARD-05 (відмова в браузері: чужі дані за прямим посиланням), AC-CARD-12 (стан інтерфейсу: помилки форми з дослівним текстом), AC-CARD-11 (відмова в браузері: користувач без ролі) — зріз 2
- QA proof pack: https://github.com/maryan-qc/therapy-scheduling/blob/d34c516a7cd1b4b1811ecd103928e740415e2ee1/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/maryan-qc/therapy-scheduling/pull/33
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/maryan-qc/therapy-scheduling/actions/runs/41624326257
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога», додано 03.11.2026 (після зеленого `quality` на `main`); «Порада: вразливі залежності» — дорадча
- Якість тестів — PR (B): https://github.com/maryan-qc/therapy-scheduling/pull/34
- Якість тестів — убитий мутант (B): `src/app/clients/actions.ts:22` `field("guardian_name")` → `field("")` (Stryker, вижив) → AC-CARD-12 → https://github.com/maryan-qc/therapy-scheduling/blob/d34c516a7cd1b4b1811ecd103928e740415e2ee1/tests/clients/actions.test.ts#L88 → убитий (actions.ts 67,65 % → 73,53 %)
- SQL-мутація (B): https://github.com/maryan-qc/therapy-scheduling/pull/34 — `npm run mutation:sql`: 5 з 9 → 9 з 9 (разом із ручними TS-мутантами T1–T2 — 7 з 11 → 11 з 11) (C5 `grant update (full_name, role, email)` на `profiles`, C7 тригер дати `>` → `>=`, C8 дитина без мови, C9 `clients_name_not_blank` → `true` — вижили й убиті новими тестами бази)
- UAT — специфікації (C): https://github.com/maryan-qc/therapy-scheduling/blob/d34c516a7cd1b4b1811ecd103928e740415e2ee1/tests/e2e/client-cards.spec.ts, https://github.com/maryan-qc/therapy-scheduling/blob/d34c516a7cd1b4b1811ecd103928e740415e2ee1/tests/e2e/negative-controls.spec.ts
- UAT — звіт на проді (C): https://github.com/maryan-qc/therapy-scheduling/blob/d34c516a7cd1b4b1811ecd103928e740415e2ee1/docs/qa/uat/2026-11-03/report.md
- UAT — PR зі звітом і відео (C): https://github.com/maryan-qc/therapy-scheduling/pull/35
- UAT — негативний контроль (C): https://github.com/maryan-qc/therapy-scheduling/pull/35 — NC-1 (хибне очікування в тесті) → FAIL (R1), NC-2 (інший текст «Тоді» в ac-text) → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-CARD-05 (реалізовано), AC-CARD-11 (реалізовано), AC-CARD-12 (реалізовано) — зі шляхом `tests/e2e/client-cards.spec.ts`; рядків «відкладено (e2e — WS8)» у матриці не було
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/maryan-qc/therapy-scheduling/pull/36
- Eval рецензента — таблиця й ключ (D): https://github.com/maryan-qc/therapy-scheduling/pull/36#issuecomment-6608519705
- Eval рецензента — правило й повторний прогін (D): правило в `AGENTS.md` — PR https://github.com/maryan-qc/therapy-scheduling/pull/37 (коміт https://github.com/maryan-qc/therapy-scheduling/commit/48cbd82); повторний прогін обох рецензентів — https://github.com/maryan-qc/therapy-scheduling/pull/36#issuecomment-6610619853
- Відхилення від PM (C): issues «Відхилення від вимог» станом на 03.11 не надходило; форма `.github/ISSUE_TEMPLATE/deviation.yml` і мітка `відхилення` — у репо

## Бонус

—
