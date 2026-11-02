# Здача WS8

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: ylehenkyi-qc
- Ваше репо: https://github.com/ylehenkyi-qc/property-workflows
- SHA: 8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://pmwp-ylehenkyi.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://pmwp-ylehenkyi.vercel.app/api/health (на момент здачі: `"ok":true`, `"sha":"8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b"`, `"env":"production"`, `"db":"ok"`)
- Зелений прогін `smoke` на `main`: https://github.com/ylehenkyi-qc/property-workflows/actions/runs/41479039056
- `accounts.zip` на SHA: https://github.com/ylehenkyi-qc/property-workflows/blob/8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b/accounts.zip
- Ролі тестових акаунтів: адміністратор — admin@example.test, pm-admin@example.test; менеджер — manager1@example.test, manager2@example.test, pm-manager@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-DSYS-02 (відмова в браузері: заборонена роль), AC-EDITOR-07 (відмова в браузері: заборонена роль, прямий запит), AC-DSYS-04 (стан інтерфейсу: порожній список). Усі зі зрізу 2.
- QA proof pack: https://github.com/ylehenkyi-qc/property-workflows/blob/8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/ylehenkyi-qc/property-workflows/pull/32
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/ylehenkyi-qc/property-workflows/actions/runs/41478977459
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit» і «Покриття: доменна підлога» (поруч із `spec`, `app`, `conformance`, `db-check`), додано 02.11.2026
- Якість тестів — PR (B): https://github.com/ylehenkyi-qc/property-workflows/pull/33
- Якість тестів — убитий мутант (B): `src/lib/auth/require-role.ts:29` `status: "ok"` → `status: ""` → AC-DSYS-02 → тест https://github.com/ylehenkyi-qc/property-workflows/blob/8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b/src/lib/auth/require-role.test.ts#L52
- SQL-мутація (B): https://github.com/ylehenkyi-qc/property-workflows/pull/41 (мутанти W1–W3 на політику й grant `template_versions` для AC-EDITOR-07: 3 з 3 KILLED; таблиця в proof pack, розділ B; раніше у https://github.com/ylehenkyi-qc/property-workflows/pull/33 було 6 з 6 для AC-TASK-10, замінений на AC-EDITOR-07, бо AC-TASK-10 зі зрізу 1)
- UAT — специфікації (C): https://github.com/ylehenkyi-qc/property-workflows/blob/8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b/tests/e2e/access-and-states.spec.ts
- UAT — звіт на проді (C): https://github.com/ylehenkyi-qc/property-workflows/blob/8cc6a6dfdf7cd415f0cd8adbef989fe9dea9ca3b/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/ylehenkyi-qc/property-workflows/pull/41 (відео вкладенням в описі)
- UAT — негативний контроль (C): https://github.com/ylehenkyi-qc/property-workflows/pull/34: NC-1 → FAIL (R1), NC-2 → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-DSYS-02 (реалізовано), AC-EDITOR-07 (реалізовано), AC-DSYS-04 (реалізовано)
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/ylehenkyi-qc/property-workflows/pull/38 (перший прогін) і https://github.com/ylehenkyi-qc/property-workflows/pull/40 (чиста копія для повторного прогону); обидва закриті без злиття
- Eval рецензента — таблиця й ключ (D): https://github.com/ylehenkyi-qc/property-workflows/pull/38#issuecomment-6580600689
- Eval рецензента — правило й повторний прогін (D): правило https://github.com/ylehenkyi-qc/property-workflows/commit/2ad9cf2e97c628614f6a69810edbd681be41ff9c (PR https://github.com/ylehenkyi-qc/property-workflows/pull/39), повторний прогін https://github.com/ylehenkyi-qc/property-workflows/pull/40#issuecomment-6581854483
- Відхилення від PM (C): не надходило

## Бонус

—
