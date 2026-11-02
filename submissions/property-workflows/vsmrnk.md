# Здача WS8

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: vsmrnk
- Ваше репо: https://github.com/vsmrnk/property-workflows
- SHA: 9f1faa4dcccac343ba89acea74672e9804c73924
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://property-workflows.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/vsmrnk/property-workflows/actions/runs/41303833213
- `accounts.zip` на SHA: https://github.com/vsmrnk/property-workflows/blob/9f1faa4dcccac343ba89acea74672e9804c73924/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test; менеджер — pm-manager@example.test; другий менеджер — manager-b@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-EDITOR-07 (відмова в браузері, заборонена роль), AC-EDITOR-09 (відмова в браузері, не увійшов), AC-EDITOR-18 (стан інтерфейсу, порожній стан)
- QA proof pack: https://github.com/vsmrnk/property-workflows/blob/9f1faa4dcccac343ba89acea74672e9804c73924/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/vsmrnk/property-workflows/pull/34
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/vsmrnk/property-workflows/actions/runs/41216448430
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога», 2026-10-31
- Якість тестів — PR (B): https://github.com/vsmrnk/property-workflows/pull/37
- Якість тестів — убитий мутант (B): `src/app/templates/[id]/versions/page.tsx:15` → AC-EDITOR-07 → https://github.com/vsmrnk/property-workflows/blob/9f1faa4dcccac343ba89acea74672e9804c73924/tests/templates/versions-pages.test.tsx#L92
- SQL-мутація (B): https://github.com/vsmrnk/property-workflows/pull/37
- UAT — специфікації (C): https://github.com/vsmrnk/property-workflows/blob/9f1faa4dcccac343ba89acea74672e9804c73924/tests/e2e/template-versions.spec.ts, https://github.com/vsmrnk/property-workflows/blob/9f1faa4dcccac343ba89acea74672e9804c73924/tests/e2e/editor-access.spec.ts
- UAT — звіт на проді (C): https://github.com/vsmrnk/property-workflows/blob/9f1faa4dcccac343ba89acea74672e9804c73924/docs/qa/uat/2026-10-31/report.md
- UAT — PR зі звітом і відео (C): https://github.com/vsmrnk/property-workflows/pull/33
- UAT — негативний контроль (C): https://github.com/vsmrnk/property-workflows/pull/33
- Рядки `docs/conformance.md` (C): AC-EDITOR-07 (реалізовано), AC-EDITOR-09 (реалізовано), AC-EDITOR-18 (реалізовано)
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/vsmrnk/property-workflows/pull/35
- Eval рецензента — таблиця й ключ (D): https://github.com/vsmrnk/property-workflows/pull/35#issuecomment-6544252242
- Eval рецензента — правило й повторний прогін (D): https://github.com/vsmrnk/property-workflows/pull/36, https://github.com/vsmrnk/property-workflows/pull/35#issuecomment-6544589909
- Відхилення від PM (C): не надходило

## Бонус

UAT у CI: зелений прогін `workflow_dispatch` https://github.com/vsmrnk/property-workflows/actions/runs/41211591229. Специфікації йдуть на одноразовому Supabase в раннері, без хмарних секретів, тому перевірку UAT можна повторити без доступу до прод-бази.
