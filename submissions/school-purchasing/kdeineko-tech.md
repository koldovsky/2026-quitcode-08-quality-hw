# Здача WS8

## Дані

- Роль: dev
- Команда: school-purchasing
- GitHub-логін: kdeineko-tech
- Ваше репо: https://github.com/kdeineko-tech/school-purchasing
- SHA: 862704422c223ab784924c9840d1d87c751a0004
- Репо вимог PM: https://github.com/ValiaBihun/2026-quitcode-dream-team
- Прод-URL: https://school-purchasing-lemon.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://school-purchasing-lemon.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/kdeineko-tech/school-purchasing/actions/runs/41695240491
- `accounts.zip` на SHA: https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test, admin@example.test; схвалювач — pm-approver@example.test, member2@example.test; заявник — pm-requester@example.test, member1@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-APR-04 (відмова в браузері — заборонена роль), AC-FRM-06 (стан інтерфейсу — помилка «Add at least one line»), AC-FRM-03 (права в інтерфейсі — типи закупівлі за дозволом); усі — зріз 2
- QA proof pack: https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/kdeineko-tech/school-purchasing/pull/53 (доповнення розбору — https://github.com/kdeineko-tech/school-purchasing/pull/54)
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/kdeineko-tech/school-purchasing/actions/runs/41528293073
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога» — з 2026-11-02
- Якість тестів — PR (B): https://github.com/kdeineko-tech/school-purchasing/pull/55
- Якість тестів — убитий мутант (B): `src/lib/org/permissions.ts:42–43` (`permissionsFromRow` → `{}`, губить дозволи з профілю) → AC-FRM-03 → https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/tests/purchases/pages.test.ts#L73 (Stryker 92,67 % → 94,00 %, `permissions.ts` 90,48 % → 100 %)
- SQL-мутація (B): https://github.com/kdeineko-tech/school-purchasing/pull/55 — `npm run mutation:sql`: A1, A2 (AC-APR-04), F1 (AC-FRM-06) — KILLED, 3 з 3
- UAT — специфікації (C): https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/tests/e2e/purchases.spec.ts, https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/tests/e2e/negative-controls.spec.ts
- UAT — звіт на проді (C): https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/docs/qa/uat/2026-11-03/report.md
- UAT — PR зі звітом і відео (C): https://github.com/kdeineko-tech/school-purchasing/pull/57 (перший прогін знайшов ваду AC-FRM-06 — виправлено в https://github.com/kdeineko-tech/school-purchasing/pull/56)
- UAT — негативний контроль (C): https://github.com/kdeineko-tech/school-purchasing/pull/57 — NC-1 (AC-APR-04, навмисно «Access denied») → FAIL (R1; Haiku сказав PASS)
- Рядки `docs/conformance.md` (C): AC-APR-04 (реалізовано), AC-FRM-06 (реалізовано), AC-FRM-03 (реалізовано) — зі шляхом до `tests/e2e/purchases.spec.ts` і звіту UAT
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/kdeineko-tech/school-purchasing/pull/58
- Eval рецензента — таблиця й ключ (D): https://github.com/kdeineko-tech/school-purchasing/pull/58#issuecomment-6619467379
- Eval рецензента — правило й повторний прогін (D): правило — https://github.com/kdeineko-tech/school-purchasing/pull/59 (коміт https://github.com/kdeineko-tech/school-purchasing/commit/f464c9e); повторний прогін обох рецензентів — розділ «Прогін 2» у https://github.com/kdeineko-tech/school-purchasing/pull/58#issuecomment-6619467379 і розділ D proof pack https://github.com/kdeineko-tech/school-purchasing/blob/862704422c223ab784924c9840d1d87c751a0004/docs/qa/proof-pack.md#d-eval-рецензента
- Відхилення від PM (C): не надходило

## Бонус

Eval скіла `spec-review`: https://github.com/kdeineko-tech/school-purchasing/pull/61 (таблиця й висновок — `evals/spec-review/README.md` у цьому PR).
4 кейси з посадженою проблемою перекладу вимог PM у специфікацію (загублений AC, інше число, вигадане правило, AC у
HTML-коментарі PM) × 3 прогони зі скілом і без, цикл `claude -p`, `claude-sonnet-5-5`, 24 прогони, $4,97 за цінами API.
Pass rate на знаходженні проблем — 12/12 і 12/12 (Δ = 0): кейси легкі для Sonnet. Скіл додає процес і форму звіту
(серйозність, БЛОКЕР, звірка ID, детерміновані перевірки) — 12/12 проти 0/12 — ціною ≈1,5× часу. Наступний крок —
тонші кейси й слабша модель.
