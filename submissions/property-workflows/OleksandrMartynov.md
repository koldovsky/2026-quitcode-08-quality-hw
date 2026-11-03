# Здача WS8

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: OleksandrMartynov
- Ваше репо: https://github.com/OleksandrMartynov/property-workflows
- SHA: 56724204d5c3c223ccf3967d14c6f10e645e5acd
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows-rho.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://property-workflows-rho.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/OleksandrMartynov/property-workflows/actions/runs/41442495542
- `accounts.zip` на SHA: https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test, admin@example.test, admin.c@example.test; менеджер — pm-manager@example.test, manager.a@example.test, manager.b@example.test, manager.c@example.test, manager.d@example.test; підрядник — pm-vendor@example.test, vendor.v@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-EDITOR-07 (відмова в браузері: заборонена роль), AC-EDITOR-09 (відмова в браузері: не увійшов), AC-DSYS-04 (стан інтерфейсу: порожній список запусків)
- QA proof pack: https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/OleksandrMartynov/property-workflows/pull/48
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/OleksandrMartynov/property-workflows/actions/runs/41442442657
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога» — додано 02.11.2026, після зеленого прогону `quality` на `main`; ruleset: https://github.com/OleksandrMartynov/property-workflows/rules/25405104
- Якість тестів — PR (B): https://github.com/OleksandrMartynov/property-workflows/pull/51
- Якість тестів — убитий мутант (B): `src/lib/supabase/public-paths.ts:7` `startsWith` → `endsWith` → AC-EDITOR-09 → https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/tests/auth/public-paths.test.ts#L24
- SQL-мутація (B): https://github.com/OleksandrMartynov/property-workflows/pull/51 — E7a, E7b (AC-EDITOR-07, `template_versions_select`) і P1 → KILLED
- UAT — специфікації (C): https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/tests/e2e/template-versions-forbidden.spec.ts, https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/tests/e2e/editor-visitor.spec.ts, https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/tests/e2e/runs-empty.spec.ts
- UAT — звіт на проді (C): https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/OleksandrMartynov/property-workflows/pull/74
- UAT — негативний контроль (C): https://github.com/OleksandrMartynov/property-workflows/pull/74 — NC-1 (навмисно хибне очікування в тесті) → FAIL (R1); NC-2 («Тоді» у вимозі змінено, тест і застосунок — ні) → NEEDS-HUMAN (R3: тест зелений, Haiku і Sonnet — FAIL)
- Рядки `docs/conformance.md` (C): AC-EDITOR-07 (реалізовано, UAT PASS) — https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/docs/conformance.md#L72, AC-EDITOR-09 (реалізовано, UAT PASS) — https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/docs/conformance.md#L74, AC-DSYS-04 (реалізовано, UAT PASS) — https://github.com/OleksandrMartynov/property-workflows/blob/56724204d5c3c223ccf3967d14c6f10e645e5acd/docs/conformance.md#L98
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/OleksandrMartynov/property-workflows/pull/62
- Eval рецензента — таблиця й ключ (D): https://github.com/OleksandrMartynov/property-workflows/pull/62#issuecomment-6572058630
- Eval рецензента — правило й повторний прогін (D): правило https://github.com/OleksandrMartynov/property-workflows/commit/3191d27c8bb2ca53289dc4fed76fc4bafe5c5ae8 (PR #65), повторний прогін https://github.com/OleksandrMartynov/property-workflows/pull/62#issuecomment-6572536347
- Відхилення від PM (C): не надходило

## Бонус

UAT у CI: `.github/workflows/e2e.yml` (з матеріалів курсу) — ті самі `tests/e2e/*.spec.ts` на одноразовому Supabase в раннері, без хмарних секретів; зелений прогін через `workflow_dispatch` на `main`: https://github.com/OleksandrMartynov/property-workflows/actions/runs/41421999130 (звіт і записи — артефакт прогону). Що з цього випливає: перший прогін у CI (PR #63) упав на AC-EDITOR-09 і знайшов справжню ваду — hero сторінки входу показував назву й задачі шаблону «Tenant move-in» відвідувачу без входу; виправлено в #64 ще до прогону на проді, тепер `e2e` — на кожному PR і push у `main`.
