# Здача WS8

## Дані

- Роль: dev
- Команда: therapy-scheduling
- GitHub-логін: markkern-hyra
- Ваше репо: https://github.com/markkern-hyra/therapy-scheduling
- SHA: 02a761a57c5383cdbd83c173b05aff227ed2e03c
- Репо вимог PM: https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling-spec
- Прод-URL: https://therapy-scheduling-theta.vercel.app

## PM

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://therapy-scheduling-theta.vercel.app/api/health
- Зелений прогін `smoke` на `main`: https://github.com/markkern-hyra/therapy-scheduling/actions/runs/41699473914
- `accounts.zip` на SHA: https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/accounts.zip
- Ролі тестових акаунтів: адміністратор — admin@example.test, admin1@example.test; планувальник — scheduler1@example.test, scheduler2@example.test; терапевт — therapist1@example.test, therapist2@example.test; без ролі — newuser1@example.test
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: AC-CARD-06 (відмова в браузері: заборонена роль), AC-CARD-12 (стан інтерфейсу: помилки форми), AC-CARD-16 (відмова в браузері й стан інтерфейсу: картка, якої не існує)
- QA proof pack: https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/markkern-hyra/therapy-scheduling/pull/30
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/markkern-hyra/therapy-scheduling/actions/runs/41699384081
- Ворота — обов'язкові перевірки в `solo-main` (A): «Ворота: fallow audit», «Покриття: доменна підлога», додано 2026-11-03: https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/docs/qa/proof-pack.md#L27
- Якість тестів — PR (B): https://github.com/markkern-hyra/therapy-scheduling/pull/34
- Якість тестів — убитий мутант (B): `src/lib/scheduling/clients.ts:27`, `?? ""` → `?? "Stryker was here!"` → AC-CARD-12 → https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/tests/scheduling/client-card-action.test.ts#L97
- SQL-мутація (B): https://github.com/markkern-hyra/therapy-scheduling/pull/34 — вивід `npm run mutation:sql`, 8 із 8 KILLED
- UAT — специфікації (C): https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/tests/e2e/client-cards.spec.ts, https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/tests/e2e/negative-controls.spec.ts
- UAT — звіт на проді (C): https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/docs/qa/uat/2026-11-03/report.md
- UAT — PR зі звітом і відео (C): https://github.com/markkern-hyra/therapy-scheduling/pull/35
- UAT — негативний контроль (C): https://github.com/markkern-hyra/therapy-scheduling/pull/35 — рядки звіту `npm run uat:nc`: NC-1 → FAIL (R1), NC-2 → NEEDS-HUMAN (R3)
- Рядки `docs/conformance.md` (C): AC-CARD-06 (реалізовано): https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/docs/conformance.md#L86, AC-CARD-12 (реалізовано): https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/docs/conformance.md#L92, AC-CARD-16 (реалізовано): https://github.com/markkern-hyra/therapy-scheduling/blob/02a761a57c5383cdbd83c173b05aff227ed2e03c/docs/conformance.md#L96
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/markkern-hyra/therapy-scheduling/pull/36
- Eval рецензента — таблиця й ключ (D): https://github.com/markkern-hyra/therapy-scheduling/pull/36#issuecomment-6609830440
- Eval рецензента — правило й повторний прогін (D): https://github.com/markkern-hyra/therapy-scheduling/pull/37, https://github.com/markkern-hyra/therapy-scheduling/commit/f03b602, повторний прогін — https://github.com/markkern-hyra/therapy-scheduling/pull/36#issuecomment-6611217257
- Відхилення від PM (C): не надходило на момент здачі

## Бонус

UAT у CI: зелений прогін `workflow_dispatch` https://github.com/markkern-hyra/therapy-scheduling/actions/runs/41689396140, артефакт `e2e-41689396140` (відео, траси, HTML-звіт Playwright). Той самий workflow зелений і на `push` цього SHA: https://github.com/markkern-hyra/therapy-scheduling/actions/runs/41699383989.

Це `e2e.yml` із матеріалів курсу без змін: одноразовий локальний Supabase в раннері, випадковий пароль на кожен прогін, без хмарних секретів. Три специфікації проходять так само, як на проді: 6 тестів разом із входом ролей і прибиранням, 13 с, пропущених немає. Отже, регресію за цими AC тепер видно на кожному PR, а не лише після ручного прогону на проді. Межі: це не UAT з вердиктом агента, а лише твердження Playwright; негативні контролі тут не запускаються; job не входить в обов'язкові перевірки `solo-main`.
