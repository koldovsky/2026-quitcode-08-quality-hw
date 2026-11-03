# Здача WS8

## Дані

- Роль: pm
- Команда: leave-portal
- GitHub-логін: mkozlovskyi-ops
- Ваше репо: https://github.com/mkozlovskyi-ops/course-staff-management-spec
- SHA: 818bad5c4c7521280fa59bb814b2317f92857eb2
- Репо вимог PM: https://github.com/mkozlovskyi-ops/course-staff-management-spec
- Прод-URL: —

## PM

- Сховище вимог: docs/
- Зріз 3: адміністратор закриває дні й години в шкільному календарі (свята, канікули, раннє закінчення), і їх не можна взяти як відпустку. Це рядок WS7 у roadmap: WS7 я пропустив (відпустка), у розробників календаря теж немає, тож він наступний ненаписаний зріз і йде в конвеєр WS9
- Вимоги зрізу 3 (A): https://github.com/mkozlovskyi-ops/course-staff-management-spec/blob/818bad5c4c7521280fa59bb814b2317f92857eb2/docs/requirements/04-school-calendar.md
- Відмовні AC і AC про стан інтерфейсу (A): вимога https://github.com/mkozlovskyi-ops/course-staff-management-spec/blob/818bad5c4c7521280fa59bb814b2317f92857eb2/docs/requirements/04-school-calendar.md — AC-CAL-12 (заборонена роль: працівник за прямим посиланням), AC-CAL-13 (заборонена роль: менеджер напряму, оминаючи сторінки), AC-CAL-14 (не увійшов); стан — AC-CAL-15 (порожній календар), помилки з дослівним текстом — AC-CAL-03, AC-CAL-05, AC-CAL-07, AC-CAL-10, AC-CAL-11
- Самоперевірка за чеклістом (A): https://github.com/mkozlovskyi-ops/course-staff-management-spec/blob/818bad5c4c7521280fa59bb814b2317f92857eb2/docs/requirements/04-school-calendar.md#L108
- Roadmap і матриця прав для зрізу 3 (A): https://github.com/mkozlovskyi-ops/course-staff-management-spec/commit/818bad5c4c7521280fa59bb814b2317f92857eb2
- Як доводимо — AC зрізів 1–2 (C): https://github.com/mkozlovskyi-ops/course-staff-management-spec/blob/818bad5c4c7521280fa59bb814b2317f92857eb2/docs/product.md#як-доводимо, коміт «Зміна: …» https://github.com/mkozlovskyi-ops/course-staff-management-spec/commit/d04c4816bd7dde60f23a6d28267dadab89d202e1
- Питання, на які ви відповіли (D): https://github.com/mkozlovskyi-ops/course-staff-management-spec/issues/19, https://github.com/mkozlovskyi-ops/course-staff-management-spec/issues/20, https://github.com/mkozlovskyi-ops/course-staff-management-spec/issues/21
- Зміни вимог із журналом змін (D): AC-LEAVE-22 (#21) — https://github.com/mkozlovskyi-ops/course-staff-management-spec/commit/a4ef0ec8bafea93c63f8db50c88c3ca298e5517a; AC-CAL-07, AC-CAL-08 (#20) — https://github.com/mkozlovskyi-ops/course-staff-management-spec/commit/818bad5c4c7521280fa59bb814b2317f92857eb2

### Приймання за UAT (трек B)

- Таблиця приймання PM (B): заповнено: вкладка leave-portal, розробники @rhutsul, @lukian-tomochko, @SvitlanaHaiduchyk
- Відхилення від вимог (B): відхилень немає (усі 9 AC — оцінка 2–3)
- Звірка «вердикт агента ↔ запис» і «AC ↔ специфікація» (B): «вердикт агента ↔ запис» — розбіжностей немає. Звірено кадри «Тоді» з описом агента для всіх 9 AC і «Тоді» в tests/e2e/*.spec.ts з текстом AC (9 AC, 3 розробники). Розбіжність «AC ↔ специфікація»: @SvitlanaHaiduchyk AC-BALANCE-13, AC-DECIDE-04, AC-DECIDE-14 — «Тоді» в thenStep і звіті переказано українською, а не дослівно (вада звіту; повідомлення в твердженнях дослівні; у PR попрошено виправити). Знахідки поза «Тоді»: @lukian-tomochko AC-BALANCE-13 — текст відмови схожий на збій (оцінка 2); AC-BALANCE-01 і AC-DECIDE-14 — порожній крок «Дано» (вада тесту, коментар розробнику); @SvitlanaHaiduchyk AC-DECIDE-04 — тип відпустки показано як «sick» замість «Sick leave» (оцінка 2)
- Підпис у репо розробників (B): https://github.com/rhutsul/leave-portal/pull/38#issuecomment-6614598721, https://github.com/lukian-tomochko/leave-portal/pull/39#issuecomment-6614599271, https://github.com/SvitlanaHaiduchyk/course-staff-management/pull/45#issuecomment-6614890174

## Розробник

—

## Бонус

—
