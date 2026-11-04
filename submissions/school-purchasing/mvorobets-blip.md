# Здача WS8

## Дані

- Роль: dev
- Команда: school-purchasing
- GitHub-логін: mvorobets-blip
- Ваше репо: https://github.com/mvorobets-blip/school-purchasing
- SHA: 2c68c499b90130ce162770ee0087fd4628809cba
- Репо вимог PM: https://github.com/ValiaBihun/2026-quitcode-dream-team
- Прод-URL: https://therapy-scheduling-ten.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://therapy-scheduling-ten.vercel.app/api/health — `{"ok":true,"sha":"2c68c499b90130ce162770ee0087fd4628809cba","env":"production","db":"ok"}`
- Зелений прогін `smoke` на `main`: https://github.com/mvorobets-blip/school-purchasing/actions/runs/41827699160
- `accounts.zip` на SHA: https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/accounts.zip
- Ролі тестових акаунтів: працівник (заявник «Primary School») — pm-requester@example.test, member1@example.test; працівник без заявок — member2@example.test; схвалювач — pm-approver@example.test; адміністратор — pm-admin@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-FRM-08 (відмова в браузері — чужі дані за прямим посиланням), AC-FRM-14 (стан інтерфейсу — порожній список з дослівним текстом), AC-FRM-15 (стан інтерфейсу — помилка з дослівним текстом «Заповніть усі поля рядка»); зріз 2 (вимога #47), вибір погоджено з PM
- QA proof pack: https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/mvorobets-blip/school-purchasing/pull/43 (таблиці P15: https://github.com/mvorobets-blip/school-purchasing/pull/43#issuecomment-6599955391 — CodeRabbit, https://github.com/mvorobets-blip/school-purchasing/pull/43#issuecomment-6600253725 — `/code-review`; перед ним — https://github.com/mvorobets-blip/school-purchasing/pull/42)
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/mvorobets-blip/school-purchasing/actions/runs/41827640639
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога» (jobs `quality.yml`; «Порада: вразливі залежності» — дорадча, не обов'язкова) — додано 03.11.2026; ruleset — https://github.com/mvorobets-blip/school-purchasing/rules/25407855, зелений прогін цих jobs на `main` — https://github.com/mvorobets-blip/school-purchasing/actions/runs/41827640639
- Якість тестів — PR (B): https://github.com/mvorobets-blip/school-purchasing/pull/46 — таблиця рівнів, покриття, Stryker 85,33 % → 96,74 % (на рядках AC вижилих 6 → 0)
- Якість тестів — убитий мутант (B): `src/lib/purchase/form.ts:47–49` (`parseLines`: `?? ""` → `?? "Stryker was here!"` і без `.trim()` для мети, кількості, ціни) → AC-FRM-15 → тести https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/tests/purchase/form.test.ts#L79 і https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/tests/purchase/form.test.ts#L85 (посилено з тексту AC окремою сесією агента)
- SQL-мутація (B): https://github.com/mvorobets-blip/school-purchasing/pull/46 — `npm run mutation:sql` 4/9 → 11/11 KILLED (S5–S9 вижили → тест https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/tests/db/purchase.test.ts#L124)
- UAT — специфікації (C): https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/tests/e2e/purchase.spec.ts, https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/tests/e2e/negative-controls.spec.ts
- UAT — звіт на проді (C): https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/docs/qa/uat/2026-11-04/report.md (PASS 3, фінальний; попередній — https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/docs/qa/uat/2026-11-03/report.md)
- UAT — PR зі звітом і відео (C): https://github.com/mvorobets-blip/school-purchasing/pull/44 (03.11) і https://github.com/mvorobets-blip/school-purchasing/pull/48 (04.11, за зауваженнями PM; відео — вкладеннями в описах)
- UAT — негативний контроль (C): https://github.com/mvorobets-blip/school-purchasing/pull/48 — `npm run uat:nc`: NC-1 → FAIL (R1), NC-2 → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/docs/conformance.md — AC-FRM-08 (реалізовано), AC-FRM-14 (реалізовано), AC-FRM-15 (реалізовано) — у колонці тестів `tests/e2e/purchase.spec.ts` (UAT на проді)
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/mvorobets-blip/school-purchasing/pull/47
- Eval рецензента — таблиця й ключ (D): https://github.com/mvorobets-blip/school-purchasing/pull/47#issuecomment-6628253643
- Eval рецензента — правило й повторний прогін (D): правило — https://github.com/mvorobets-blip/school-purchasing/pull/50 (https://github.com/mvorobets-blip/school-purchasing/commit/60024f58095f3de89540e1a49fdfb786c389100b); повторний прогін — https://github.com/mvorobets-blip/school-purchasing/pull/47#issuecomment-6629867295 (уточнення «закрито частково» — https://github.com/mvorobets-blip/school-purchasing/pull/47#issuecomment-6630280675)
- Відхилення від PM (C): не надходило — PM прийняла 3 з 3 (https://github.com/mvorobets-blip/school-purchasing/pull/44#issuecomment-6607154130); її 7 зауважень до тестів і звіту закрито в https://github.com/mvorobets-blip/school-purchasing/pull/48, відповідь — https://github.com/mvorobets-blip/school-purchasing/pull/44#issuecomment-6627659502

## Бонус

UAT у CI — зелений прогін `workflow_dispatch` на `main`: https://github.com/mvorobets-blip/school-purchasing/actions/runs/41827667461 (артефакт `e2e-41827667461-1`); workflow — https://github.com/mvorobets-blip/school-purchasing/blob/2c68c499b90130ce162770ee0087fd4628809cba/.github/workflows/e2e.yml, PR — https://github.com/mvorobets-blip/school-purchasing/pull/51.

Що зробили: ті самі специфікації `tests/e2e/*.spec.ts`, що й UAT на проді, ідуть у GitHub Actions на одноразовому Supabase в раннері (`supabase start` з нашими міграціями, `users:demo` з випадковим паролем, збірка, Playwright) — без хмарних секретів. Наші специфікації писались для проду з даними, тож дані (відділи, членства, заявка автора) створює `npm run e2e:fixtures`: заявку подає сам автор через `rpc('submit_purchase')`, а скрипт працює лише з localhost.

Що з цього випливає: UAT-специфікації тепер перевіряються на кожен PR із кодом (≈3 хв), а не лише руками перед здачею; перший же прогін показав, що специфікація, написана під прод, у CI потребує явного опису даних — і цей опис (фікстури) став документацією передумов «Дано».
