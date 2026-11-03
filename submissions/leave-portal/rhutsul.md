# Здача WS8

## Дані

- Роль: dev
- Команда: leave-portal
- GitHub-логін: rhutsul
- Ваше репо: https://github.com/rhutsul/leave-portal
- SHA: 6e80770c1013fc525d4751bedc174ace7dd885da
- Репо вимог PM: https://github.com/mkozlovskyi-ops/course-staff-management-spec
- Прод-URL: https://leave-portal-olive.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://leave-portal-olive.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/rhutsul/leave-portal/actions/runs/41693397900
- `accounts.zip` на SHA: https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/accounts.zip
- Ролі тестових акаунтів: працівник — teacher1@example.test, teacher2@example.test; менеджер — manager1@example.test, manager2@example.test; адміністратор — admin@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-BALANCE-13 (відмова в браузері: чужі дані за прямим посиланням), AC-LEAVE-06 (стан інтерфейсу: помилка), AC-LEAVE-19 (стан інтерфейсу: помилка поля). Усі зі зрізу 1: PM не опублікував вимог зрізу 2 (рядок у roadmap PM має статус `planned`, файлу вимог немає), за домовленістю з PM зріз 2 перенесено. Усі три AC на проді лише читають дані.
- QA proof pack: https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/rhutsul/leave-portal/pull/37
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/rhutsul/leave-portal/actions/runs/41693275563
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога» — додано 02.11.2026 (поряд зі `spec`, `app`, `conformance`, `db-check`; «Порада: вразливі залежності» — не обов'язкова): https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/docs/qa/proof-pack.md#L28
- Якість тестів — PR (B): https://github.com/rhutsul/leave-portal/pull/39
- Якість тестів — убитий мутант (B): `src/lib/leave/time.ts:214` (`blocks.length === 0` → `false`) → AC-LEAVE-06 → https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/src/lib/leave/time.test.ts#L85
- SQL-мутація (B): https://github.com/rhutsul/leave-portal/pull/39 (вивід `npm run mutation:sql -- --markdown`: S1–S9 KILLED; S1 — `private.can_view_balances` → `true`, AC-BALANCE-13)
- UAT — специфікації (C): https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/tests/e2e/balances.spec.ts, https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/tests/e2e/new-request.spec.ts
- UAT — звіт на проді (C): https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/rhutsul/leave-portal/pull/38
- UAT — негативний контроль (C): https://github.com/rhutsul/leave-portal/pull/38 — NC-1 → FAIL (R1), NC-2 → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-BALANCE-13 (реалізовано) https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/docs/conformance.md#L100, AC-LEAVE-06 (реалізовано) https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/docs/conformance.md#L44, AC-LEAVE-19 (реалізовано) https://github.com/rhutsul/leave-portal/blob/6e80770c1013fc525d4751bedc174ace7dd885da/docs/conformance.md#L46
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/rhutsul/leave-portal/pull/41
- Eval рецензента — таблиця й ключ (D): https://github.com/rhutsul/leave-portal/pull/41#issuecomment-6585039202
- Eval рецензента — правило й повторний прогін (D): https://github.com/rhutsul/leave-portal/commit/e4074a8ae6fb9058033ba4f089faa48172649d12 (PR https://github.com/rhutsul/leave-portal/pull/42) і https://github.com/rhutsul/leave-portal/pull/41#issuecomment-6599172263
- Відхилення від PM (C): не надходило

## Бонус

UAT у CI: зелений прогін `workflow_dispatch` https://github.com/rhutsul/leave-portal/actions/runs/41690197432 (6 passed, 0 skipped, артефакт зі звітом і трасами) — `.github/workflows/e2e.yml` (PR https://github.com/rhutsul/leave-portal/pull/45) підіймає одноразовий Supabase у раннері, створює синтетичних користувачів і проганяє Playwright-специфікації трьох AC без хмарних секретів; пароль генерується на кожен прогін і маскується. Тепер ті самі специфікації, що доводять AC на проді, ще й ганяються на кожен PR і push у `main` (job `e2e` зелений на 6e80770c1013fc525d4751bedc174ace7dd885da), тож регресію AC-BALANCE-13, AC-LEAVE-06 чи AC-LEAVE-19 видно до злиття, а не лише в ручному UAT.
