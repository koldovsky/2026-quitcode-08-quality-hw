# Здача WS8

## Дані

- Роль: dev
- Команда: therapy-scheduling
- GitHub-логін: pavmys
- Ваше репо: https://github.com/pavmys/therapy-scheduling
- SHA: 9d64398610c40b849517939c1a6ef0d097a9fdc8
- Репо вимог PM: https://github.com/Sofiia-pm/therapy-scheduling-spec
- Прод-URL: https://therapy-scheduling-three.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://therapy-scheduling-three.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/pavmys/therapy-scheduling/actions/runs/41599671088
- `accounts.zip` на SHA: https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test; планувальник — pm-scheduler@example.test; терапевт — pm-therapist@example.test; без ролі — newuser1@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-CARD-06 (відмова в браузері — заборонена роль), AC-CARD-16 (стан інтерфейсу — помилка), AC-CARD-07 (відмова в браузері — не увійшов)
- QA proof pack: https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/pavmys/therapy-scheduling/pull/35
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/pavmys/therapy-scheduling/actions/runs/41599628295
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога» (jobs https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/.github/workflows/quality.yml) додано до `spec`, `app`, `conformance`, `db-check` — 02.11.2026; перелік — https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/docs/qa/proof-pack.md#a-ворота
- Якість тестів — PR (B): https://github.com/pavmys/therapy-scheduling/pull/38
- Якість тестів — убитий мутант (B): `supabase/migrations/20261022040716_roles_and_clients.sql:61` `grant insert (full_name, email) … to authenticated` → `… to authenticated, anon` (C4, до посилення тесту вижив) → AC-CARD-07 → https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/tests/db/app-access.test.ts#L47 ; Stryker на модулях AC — 95,38 %, вижилих на рядках AC немає, ручні мутанти T1 (AC-CARD-16) і T2 (AC-CARD-07) убиті
- SQL-мутація (B): https://github.com/pavmys/therapy-scheduling/pull/38 — `npm run mutation:sql`: 5 з 6 вбито, 1 еквівалентний (C6) прийнято з причиною
- UAT — специфікації (C): https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/tests/e2e/client-cards.spec.ts, https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/tests/e2e/negative-controls.spec.ts
- UAT — звіт на проді (C): https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/pavmys/therapy-scheduling/pull/36
- UAT — негативний контроль (C): https://github.com/pavmys/therapy-scheduling/pull/36 — `npm run uat:nc`: NC-1 (AC-CARD-16, хибний текст у твердженні) → FAIL (R1); NC-2 (AC-CARD-16, уточнений текст «Тоді» в анотації) → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-CARD-06 (реалізовано) — https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/docs/conformance.md#L82, AC-CARD-07 (реалізовано) — https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/docs/conformance.md#L83, AC-CARD-16 (реалізовано) — https://github.com/pavmys/therapy-scheduling/blob/9d64398610c40b849517939c1a6ef0d097a9fdc8/docs/conformance.md#L92
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/pavmys/therapy-scheduling/pull/39
- Eval рецензента — таблиця й ключ (D): https://github.com/pavmys/therapy-scheduling/pull/39#issuecomment-6581143652
- Eval рецензента — правило й повторний прогін (D): https://github.com/pavmys/therapy-scheduling/commit/36fb2fe026c91d4239b55891c63e29a3f32c0190 (PR https://github.com/pavmys/therapy-scheduling/pull/40) і https://github.com/pavmys/therapy-scheduling/pull/39#issuecomment-6588017356
- Відхилення від PM (C): не надходило

## Бонус

—
