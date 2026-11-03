# Здача WS8

## Дані

- Роль: pm
- Команда: school-purchasing
- GitHub-логін: ValiaBihun
- Ваше репо: https://github.com/ValiaBihun/2026-quitcode-dream-team
- SHA: 8f0fee554e7d6c50ba62e995aefda3eab7156eaa
- Репо вимог PM: https://github.com/ValiaBihun/2026-quitcode-dream-team
- Прод-URL: —

## PM

- Сховище вимог: issues
- Зріз 3: схвалювач частково схвалює чи повертає заявку, автор виправляє й подає знову; кожна заявка має номер, суми рядків і історію рішень (реалізує конвеєр у WS9)
- Вимоги зрізу 3 (A): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/63, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/64
- Відмовні AC і AC про стан інтерфейсу (A): вимога https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/63 — AC-DEC-08 (чужі дані), AC-DEC-09 (заборонена роль), AC-DEC-10 (не увійшов); стан — AC-DEC-03, AC-DEC-06. Вимога https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/64 — AC-HIST-10 (чужі дані), AC-HIST-11 (не увійшов); стан — AC-HIST-03, AC-HIST-04, AC-HIST-05
- Самоперевірка за чеклістом (A): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/63#issuecomment-6503351793, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/64#issuecomment-6503352592
- Roadmap і матриця прав для зрізу 3 (A): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/1#issuecomment-6503343940
- Як доводимо — AC зрізів 1–2 (C): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/1 (розділ «### Як доводимо») і коментар «Зміна: …» https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/1#issuecomment-6608087607
- Питання, на які ви відповіли (D): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/65, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/66, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/67, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/68, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/69
- Зміни вимог із журналом змін (D): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/63#issuecomment-6571579042, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/64#issuecomment-6571579441, https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/1#issuecomment-6571579859

### Приймання за UAT (трек B)

- Таблиця приймання PM (B): заповнено: вкладка school-purchasing, розробники @YarynaPankivv, @kdeineko-tech, @mvorobets-blip
- Відхилення від вимог (B): відхилень немає
- Звірка «вердикт агента ↔ запис» і «AC ↔ специфікація» (B): перевірено в браузері на проді; розбіжностей, що змінюють оцінку, немає. @YarynaPankivv — вердикт збігається із записом, «Тоді» збігається зі специфікацією для AC-FRM-09, AC-FRM-14, AC-APR-03. @kdeineko-tech — збігається, крім кадру AC-FRM-03 (без розкритого списку; відсутність «Self-purchase» перевірено в браузері) і AC-APR-04 («статуси не змінилися» агент з кадру не оцінив; змін не побачено). @mvorobets-blip — вердикт збігається із записом, «Тоді» зі специфікації збігається з текстом AC для AC-FRM-08, AC-FRM-14, AC-FRM-15
- Підпис у репо розробників (B): https://github.com/YarynaPankivv/school-purchasing/pull/49#issuecomment-6605570889, https://github.com/kdeineko-tech/school-purchasing/pull/57#issuecomment-6613405817, https://github.com/mvorobets-blip/school-purchasing/pull/44#issuecomment-6607154130

## Розробник

—

## Бонус

10 golden cases для AI-пропозиції рядків закупівлі (WS10): https://github.com/ValiaBihun/2026-quitcode-dream-team/issues/70. Функція: працівник вставляє вільний опис покупки, AI пропонує заповнені рядки; серед кейсів складні (кілька предметів, типове значення) і відмови (чужі запити, межі кількості й ціни).
