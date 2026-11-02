# Здача WS8

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: dmudryk
- Ваше репо: https://github.com/dmudryk/property-workflows
- SHA: 0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows-bravo16.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://property-workflows-bravo16.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/dmudryk/property-workflows/actions/runs/41469946514
- `accounts.zip` на SHA: https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/accounts.zip
- Ролі тестових акаунтів: адміністратор — pm-admin@example.test; менеджер — pm-manager@example.test; менеджер без
  жодного запуску (AC-DSYS-04, AC-DSYS-02) — manager.c@example.test; менеджер запуску «Apartment 12, move-in»
  (AC-DSYS-08) — manager.a@example.test; вендор (зріз 3) — vendor@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-DSYS-02 (відмова в браузері — заборонена роль: менеджер відкриває редактор за прямим посиланням),
  AC-DSYS-04 (стан інтерфейсу — порожній список запусків), AC-DSYS-08 (не увійшов → вхід → та сама сторінка запуску)
- QA proof pack: https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/dmudryk/property-workflows/pull/29
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/dmudryk/property-workflows/actions/runs/41052507777
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога» — додано 02.11.2026 (разом зі spec, app, conformance, db-check — 6 обов'язкових)
- Якість тестів — PR (B): https://github.com/dmudryk/property-workflows/pull/31
- Якість тестів — убитий мутант (B): `src/lib/auth/next-path.ts:7` `value.startsWith("//")` → `value.endsWith("//")`
  → AC-DSYS-08 → https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/src/app/login/actions.test.ts#L64
  (ще `next-path.ts:19` `startsWith("/login/")` → `endsWith` → `actions.test.ts#L40`); Stryker `next-path.ts`
  87,80 % → 92,68 %
- SQL-мутація (B): https://github.com/dmudryk/property-workflows/pull/31 — D1 (`save_template_draft` без перевірки
  ролі) і D2 (політика `template_drafts` → `true`) — обидва KILLED (`npm run mutation:sql`)
- UAT — специфікації (C): https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/tests/e2e/editor-forbidden.spec.ts,
  https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/tests/e2e/runs-empty.spec.ts,
  https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/tests/e2e/return-after-sign-in.spec.ts
- UAT — звіт на проді (C): https://github.com/dmudryk/property-workflows/blob/0d0c0dd1f4214d8164dcef0f65e0b1aaf199e549/docs/qa/uat/2026-11-02/report.md
- UAT — PR зі звітом і відео (C): https://github.com/dmudryk/property-workflows/pull/32
- UAT — негативний контроль (C): https://github.com/dmudryk/property-workflows/pull/32 — NC-1 → FAIL (R1), NC-2 →
  NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-DSYS-02 (реалізовано), AC-DSYS-04 (реалізовано), AC-DSYS-08 (реалізовано) — з
  e2e-специфікаціями; рядків `відкладено (e2e — WS8)` у матриці не було
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/dmudryk/property-workflows/pull/36
- Eval рецензента — таблиця й ключ (D): https://github.com/dmudryk/property-workflows/pull/36#issuecomment-6579620905
- Eval рецензента — правило й повторний прогін (D): https://github.com/dmudryk/property-workflows/pull/38 і
  https://github.com/dmudryk/property-workflows/pull/36#issuecomment-6580677567 (CodeRabbit тепер знаходить ваду 3, але як Trivial; /code-review — 3 з 3)
- Відхилення від PM (C): не надходило

## Бонус

—
