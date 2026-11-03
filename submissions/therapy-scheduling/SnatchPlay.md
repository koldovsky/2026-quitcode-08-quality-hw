# Здача WS8

## Дані

- Роль: dev
- Команда: therapy-scheduling
- GitHub-логін: SnatchPlay
- Ваше репо: https://github.com/SnatchPlay/therapy-scheduling
- SHA: 8a1e4a2dabf796d0dbd7a608e6964947696fbcc2
- Репо вимог PM: https://github.com/Sofiia-pm/therapy-scheduling-spec
- Прод-URL: https://therapy-scheduling-weld.vercel.app

## PM

—

### Приймання за UAT (трек B)

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://therapy-scheduling-weld.vercel.app/api/health (`"db":"ok"`, `sha` — коміт `9d176ca`; після злиття PR 64 і 65 Vercel перерозгортає `main`, на момент підготовки відповідь ще з `9d176ca`)
- Зелений прогін `smoke` на `main`: https://github.com/SnatchPlay/therapy-scheduling/actions/runs/41713613386
- `accounts.zip` на SHA: https://github.com/SnatchPlay/therapy-scheduling/blob/8a1e4a2dabf796d0dbd7a608e6964947696fbcc2/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test; планувальник — scheduler1@example.test, pm-scheduler@example.test; терапевт — therapist1@example.test, therapist2@example.test, pm-therapist@example.test, pm-therapist2@example.test; без ролі — pm-noaccess@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-CARD-05 (відмова в браузері: чужа картка за прямим посиланням), AC-CARD-16 (стан інтерфейсу: картки немає, різні тексти для двох ролей), AC-HOLD-44 (відмова в браузері: сторінки планувальника для терапевта)
- QA proof pack: https://github.com/SnatchPlay/therapy-scheduling/blob/8a1e4a2dabf796d0dbd7a608e6964947696fbcc2/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/SnatchPlay/therapy-scheduling/pull/60
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/SnatchPlay/therapy-scheduling/actions/runs/41713513351
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога» (поряд зі `spec`, `app`, `conformance`, `db-check`), додано 2026-11-03
- Якість тестів — PR (B): https://github.com/SnatchPlay/therapy-scheduling/pull/61
- Якість тестів — убитий мутант (B): `src/lib/supabase/viewer.ts:23-25` → AC-CARD-05 → https://github.com/SnatchPlay/therapy-scheduling/blob/ce833c15763167af43c68c3adf5190cc42aeb4ab/src/lib/supabase/viewer.test.ts#L53
- SQL-мутація (B): https://github.com/SnatchPlay/therapy-scheduling/pull/61 (`npm run mutation:sql` і `mutation:points`: 9 з 9 убито)
- UAT — специфікації (C): https://github.com/SnatchPlay/therapy-scheduling/blob/8a1e4a2dabf796d0dbd7a608e6964947696fbcc2/tests/e2e/client-card.spec.ts, https://github.com/SnatchPlay/therapy-scheduling/blob/8a1e4a2dabf796d0dbd7a608e6964947696fbcc2/tests/e2e/slots-holds.spec.ts
- UAT — звіт на проді (C): https://github.com/SnatchPlay/therapy-scheduling/blob/8a1e4a2dabf796d0dbd7a608e6964947696fbcc2/docs/qa/uat/2026-11-03/report.md
- UAT — PR зі звітом і відео (C): https://github.com/SnatchPlay/therapy-scheduling/pull/62 (відео — у `test-results/` на машині прогону, не в git)
- UAT — негативний контроль (C): https://github.com/SnatchPlay/therapy-scheduling/pull/65 (розділ C proof pack: NC-1 → FAIL, NC-2 → NEEDS-HUMAN)
- Рядки `docs/conformance.md` (C): AC-CARD-05 (реалізовано), AC-CARD-16 (реалізовано), AC-HOLD-44 (реалізовано); рядків «відкладено (e2e — WS8)» не було
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/SnatchPlay/therapy-scheduling/pull/63 (закрито без злиття)
- Eval рецензента — таблиця й ключ (D): https://github.com/SnatchPlay/therapy-scheduling/pull/63#issuecomment-6615866191
- Eval рецензента — правило й повторний прогін (D): правило https://github.com/SnatchPlay/therapy-scheduling/commit/c66a17c419b0ecd70324ded84f6b9a6bd1ba7b1f (PR 64); повторний прогін https://github.com/SnatchPlay/therapy-scheduling/pull/63#issuecomment-6616033756 — `/code-review high` повторно знайшов усе; повторний прогін CodeRabbit відхилено лімітом («next included review … 43 minutes», https://github.com/SnatchPlay/therapy-scheduling/pull/63#issuecomment-6615979832), тож його не виконано до строку
- Відхилення від PM (C): не надходило

## Бонус

—
