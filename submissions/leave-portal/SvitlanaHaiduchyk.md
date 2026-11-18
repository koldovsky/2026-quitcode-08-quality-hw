# Здача WS8

## Дані

- Роль: dev
- Команда: leave-portal
- GitHub-логін: SvitlanaHaiduchyk
- Ваше репо: https://github.com/SvitlanaHaiduchyk/course-staff-management
- SHA: 14d69d320967549b1fffc536e4933440de9b7922
- Репо вимог PM: https://github.com/mkozlovskyi-ops/course-staff-management-spec
- Прод-URL: https://course-staff-management.vercel.app

## PM

—

### Приймання за UAT (трек B)

—

## Розробник

### D0 — умова прийняття

- `/api/health`: https://course-staff-management.vercel.app/api/health — `{"ok":true,"sha":"14d69d320967549b1fffc536e4933440de9b7922","env":"production","db":"ok"}`
- Зелений прогін `smoke` на `main`: https://github.com/SvitlanaHaiduchyk/course-staff-management/actions/runs/44322469070
- `accounts.zip` на SHA: https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/accounts.zip
- Ролі тестових акаунтів: адміністратор — admin@example.test; відповідальні менеджери — manager1@example.test, manager2@example.test; працівники — teacher1@example.test, teacher2@example.test. Паролі — лише в `accounts.zip` (архів складає `npm run accounts:zip`: 7-Zip питає пароль курсу з клавіатури, у репо й у чаті його немає)
- Версія `next`: next@16.4.3

### Шар якості для 3 AC

- 3 AC: `AC-DECIDE-04` (стан інтерфейсу: помилка), `AC-DECIDE-14` (стан інтерфейсу: порожній стан), `AC-BALANCE-13` (відмова в браузері: чужі дані за прямим посиланням). Третій — із вимоги про залишки, а не зі зрізу 2: у зрізі 2 немає жодної відмови, яку видно в браузері (інтерфейс не малює кнопок, яких людині не можна натиснути), тож `AC-DECIDE-09` і `AC-DECIDE-18` досяжні лише прямим POST. `AC-BALANCE-13` — єдина відмова, досяжна просто за URL `/balances/<чужий id>`
- QA proof pack: https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/docs/qa/proof-pack.md
- Ворота — PR із розбором знахідок (A): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/37 — дві справжні знахідки виправлено (`toTime`, друга копія `RecordStatus`), три файли лишено з причиною в самому файлі. Головне, що показали ворота: правило `vitest/require-to-throw-message` знайшло **24** відмовні тести з голим `toThrow()` — вони лишалися б зелені й на одруківці в SQL; серед них `AC-DECIDE-09` падав із повідомленням `AC-DECIDE-18`
- Ворота — зелений прогін `quality` на `main` (A): https://github.com/SvitlanaHaiduchyk/course-staff-management/actions/runs/44285111989
- Ворота — обов'язкові перевірки в `solo-main` (A): додано 03.11.2026 два jobs workflow `quality` — «Ворота: fallow audit» і «Покриття: доменна підлога». Разом зі `spec`, `app`, `conformance`, `db-check` у ruleset зараз шість обов'язкових перевірок
- Якість тестів — PR (B): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/38 — таблиця рівнів на кожен AC, покриття по файлах, Stryker на `src/lib/leave/decision.ts` **76.60 % → 100 %** (вижилих 22 → 0), жодного мутанта не прибрано й не вимкнено
- Якість тестів — убитий мутант (B): `src/lib/leave/decision.ts:130` — `comment === null` → `false`, AC-DECIDE-04 → тест https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/8b367b49ccc9a827a66b66a50baf2eeb8ec2ba6c/tests/leave-decision.test.ts#L56 (посилений із тексту AC: «без коментаря» — це і порожнє поле `null`, і самі пробіли)
- SQL-мутація (B): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/38 — `npm run mutation:sql` на PGlite-гарнесі, **5 із 5 убито**. Найцінніший — `D2` (`AC-DECIDE-04`, обмеження `leave_decisions_return_needs_comment_check`): спершу **SURVIVED**, бо обмеження бази не доводив жоден тест — усі йшли через `decide_leave_record`, яка відмовляє до вставки. Додано тест, що б'є в таблицю напряму, повз функцію
- UAT — специфікації (C): https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/tests/e2e/decisions-return-no-comment.spec.ts , https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/tests/e2e/decisions-empty.spec.ts , https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/tests/e2e/balances-forbidden.spec.ts
- UAT — звіт на проді (C): https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/docs/qa/uat/2026-11-04/report.md — усі три AC **PASS** за правилом R6 (перевірка Playwright passed + вердикт агента PASS). Рецензент `claude-haiku-5-5`, суперечки → `claude-sonnet-5-5`, $0.0056 за розбір. Перший звіт — https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/docs/qa/uat/2026-11-03/report.md , лишено в репо як є: переписувати історію приймання не можна
- UAT — PR зі звітом і відео (C): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/45 (прогін 03.11) і https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/52 (виправлення за зауваженнями PM, після нього — прогін 04.11 на чистому дереві). Гарнес і виправлення зламаного `/decisions` — https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/44
- UAT — негативний контроль (C): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/45 — `NC-1` (`AC-DECIDE-14`, навмисно хибне очікування): перевірка Playwright **впала**, агент сказав **PASS** (кадр справді відповідає критерію), підсумок — **FAIL** за правилом R1. Тобто від хибного PASS захищає код правил вердикту, а не судження агента
- Рядки `docs/conformance.md` (C): AC-DECIDE-04 (реалізовано), AC-DECIDE-14 (реалізовано), AC-BALANCE-13 (реалізовано) — у колонці «Тест» кожного з них тепер стоїть і e2e-специфікація UAT (https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/47)
- Eval рецензента — PR з вадами, не злитий (D): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/42 — повторний прогін, закрито без злиття. **Перший прогін — https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/39 — помилково злито замість закриття** (див. «Що пішло не так» нижче)
- Eval рецензента — таблиця й ключ (D): https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/39#issuecomment-6595321361 — опубліковано після того, як обидва рецензенти відпрацювали. Рахунок: `/code-review high` — 3 з 3, CodeRabbit — 2 з 3, обидва без хибної тривоги на приманці. Пропущена вада 3 — заміна межі `>` на `>=` з `AC-BALANCE-08`; CodeRabbit її **побачив і описав як задум**, а в перевірці перед злиттям порадив закріпити хибну поведінку тестом із тим самим AC ID
- Eval рецензента — правило й повторний прогін (D): правило — https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/40 (розділ «Межі» в `AGENTS.md`: оператор порівняння на межі з AC — частина вимоги; заміна `>` ↔ `>=` без нового AC від PM — «must fix» навіть із зеленими тестами). Повторний прогін — https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/42 , розбір — https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/46 . Цього разу CodeRabbit ваду **зловив** (Major · Functional Correctness, із посиланням на AC-BALANCE-08 і на розходження інтерфейсу з базою). **Застереження: приписати це нашому правилу не можна** — джерелом знахідки CodeRabbit вказує власні «Learnings» (пам'ять про #39), а не coding guidelines. Правило й навчання спрацювали одночасно, і цим експериментом їх не розділити
- Відхилення від PM (C): issues «Відхилення від вимог» не надходило. Приймання 03.11 пройшло — усі три AC прийнято, із двома зауваженнями в чаті команди: `clause` у `thenStep(…)` був переказом українською замість дослівного «Тоді» з AC, і попередній звіт зроблено з незакоміченими змінами. Обидва закрито в https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/52 , після чого — новий прогін UAT на чистому дереві (звіт 2026-11-04)

### Що пішло не так із самим eval — пишу як є

PR #39 (гілка з трьома навмисними вадами) мали закрити після рев'ю, а його **злили в `main`**. За рубрикою злитий PR із вадами не зараховують.

Наслідки й виправлення — https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/41 :

1. `getSession()` замість `getClaims()` і межа `>=` побували в `main` і на проді ≈1 годину.
2. `db-deploy` **застосував** у продакшн-базу міграцію з `security definer` без `set search_path = ''`. Прибрано новою міграцією (застосовану не редагуємо): функцію видалено, бо її ніхто не кликав — найменша поверхня ризику.
3. Додано тест на межу `exceedsBalance(100, 100) === false`. Саме його відсутність зробила ваду невидимою для CI.

Висновок для конвеєра: вада, яку не зловили ні ворота, ні два рецензенти, ловиться мутацією — Stryker убив би цього мутанта. Але Stryker не в обов'язкових перевірках, бо повільний. Отже, для AC з числовою межею тест на саму межу обов'язковий, і це тепер записано правилом в `AGENTS.md`.

### Чесно про строк

Робота зроблена в строк — усі PR вище датовані 28.10–04.11. Цей файл здачі я не подала вчасно через власний недогляд: PR у репо домашки не було відкрито. Подаю із запізненням, без змін у самій роботі.

## Бонус

**UAT у CI** — https://github.com/SvitlanaHaiduchyk/course-staff-management/blob/14d69d320967549b1fffc536e4933440de9b7922/.github/workflows/e2e.yml : на кожен PR і `workflow_dispatch`, з артефактами (відео й кадри). Зелений прогін на PR — https://github.com/SvitlanaHaiduchyk/course-staff-management/actions/runs/44280471436 ; прогону саме `workflow_dispatch` ще не робила.

Що з цього випливає. У CI без `SUPABASE_SECRET_KEY` специфікації з тегом `@writes` пропускаються самі, тож на PR реально біжить лише `AC-DECIDE-14` — решта доводиться локальним `npm run uat`. Це свідомий розмін: секретний ключ у CI дав би повний набір, але він ніколи не потрапляє нікуди, крім мого `.env.local`. Головне, що дав цей workflow, — `ac:coverage` тепер рахує e2e-специфікації як покриття AC, і зміна заголовка сторінки більше не ламає прийнятий AC мовчки (а саме так `/decisions` одного разу зламав два).
