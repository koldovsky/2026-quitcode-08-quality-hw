# Здача WS8

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: yuriivynar
- Ваше репо: https://github.com/yuriivynar/property-workflows
- SHA: 3e7f0b1e7e495ab5cedd52b8255b5182314544ca
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows-eta.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://property-workflows-eta.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/yuriivynar/property-workflows/actions/runs/41480254148
- `accounts.zip` на SHA: https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/accounts.zip
- Ролі тестових акаунтів: менеджер — pm-manager@example.test; адміністратор — pm-admin@example.test; вендор — pm-vendor@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-EDITOR-07 (відмова в браузері — заборонена роль: менеджер на списку версій), AC-EDITOR-19 (стан інтерфейсу — помилка «Enter a template name»), AC-EDITOR-09 (відмова в браузері — не увійшов: редактор за прямим посиланням). Усі зі зрізу 2.
- QA proof pack: https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/yuriivynar/property-workflows/pull/37
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/yuriivynar/property-workflows/actions/runs/41480184535
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога», з 02.11.2026 («Порада: вразливі залежності» — не обов'язкова)
- Якість тестів — PR (B): https://github.com/yuriivynar/property-workflows/pull/39
- Якість тестів — убитий мутант (B): SQL E19 — `supabase/migrations/20261026133459_template_versions.sql`, обмеження `templates_name_not_blank` без `btrim` (назва лише з пробілів проходить базу) → AC-EDITOR-19 («name … consisting only of spaces … no template is created») → https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/tests/db/template-clarify.test.ts#L151 (до посилення — SURVIVED, після — KILLED). TS (Stryker): `src/lib/templates/domain.ts:119` (`cleanName`, `typeof value === "string"` → `true`) → AC-EDITOR-19 → https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/src/lib/templates/domain.test.ts#L93
- SQL-мутація (B): https://github.com/yuriivynar/property-workflows/pull/39 — `npm run mutation:sql`: E07, E09, E19 → KILLED (до посилення тесту E19 — SURVIVED)
- UAT — специфікації (C): https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/tests/e2e/template-versions-forbidden.spec.ts, https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/tests/e2e/template-name-required.spec.ts, https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/tests/e2e/template-editor-signed-out.spec.ts
- UAT — звіт на проді (C): https://github.com/yuriivynar/property-workflows/blob/3e7f0b1e7e495ab5cedd52b8255b5182314544ca/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/yuriivynar/property-workflows/pull/40 (відео й негативні контролі); чистий прогін на `main @ a2c2bcc` (3 × PASS) — https://github.com/yuriivynar/property-workflows/pull/52
- UAT — негативний контроль (C): https://github.com/yuriivynar/property-workflows/pull/40 — `npm run uat:nc`: NC-1 (хибний текст у тесті) → FAIL (R1), NC-2 (уточнений «Тоді» в `ac-text`) → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-EDITOR-07 (реалізовано), AC-EDITOR-09 (реалізовано), AC-EDITOR-19 (реалізовано) — у кожному рядку e2e-специфікація UAT; уся матриця — 77 з 77 «реалізовано», зокрема AC-VENDOR-01…10 зрізу 3
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/yuriivynar/property-workflows/pull/41
- Eval рецензента — таблиця й ключ (D): https://github.com/yuriivynar/property-workflows/pull/41#issuecomment-6574406386
- Eval рецензента — правило й повторний прогін (D): https://github.com/yuriivynar/property-workflows/commit/6d7352d79b31929bf90e2b86cb85ee91bd0a199d (PR https://github.com/yuriivynar/property-workflows/pull/42), повторний прогін — https://github.com/yuriivynar/property-workflows/pull/41#issuecomment-6575184268
- Відхилення від PM (C): не надходило

## Бонус

UAT у CI (`workflow_dispatch`): PR https://github.com/yuriivynar/property-workflows/pull/48, зелений прогін на `main` — https://github.com/yuriivynar/property-workflows/actions/runs/41462285946 (`6 passed`, 0 пропущених, артефакт `e2e-<run_id>`).

Обрали простіший шлях із матеріалів (`e2e.yml`): одноразовий Supabase у раннері з нашими міграціями, `seed.sql` і користувачами з `supabase/demo-users.json` з випадковим паролем на кожен прогін, тож хмарних секретів немає зовсім, а прод не зачіпається. Довелося додати один крок — SQL-фікстур з версією 2 «Tenant move-in» для «Дано» AC-EDITOR-07: у `seed.sql` її класти не можна, бо його читають і тести бази PGlite, що чекають версію 1. Висновок: ті самі специфікації, що дають звіт UAT на проді, тепер ловлять регрес на кожному PR — зріз 3 (вендор, https://github.com/yuriivynar/property-workflows/pull/50) пройшов їх ще до злиття.
