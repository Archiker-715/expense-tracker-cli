# expense-tracker
Project from https://roadmap.sh/projects/expense-tracker

Результат немного перерос задание и получился полноценный CRUD на CSV-файл.


Работа с приложениеим: билдим исполняемый файл (go build main.go), затем приложение готово принимать терминальные команды. 
CSV-файл "expenses.csv" будет создан в той же директории, где находится main.go.

Сами флаги (--example) регистронезависимы.

Пример работы с приложением:
1. Добавить запись: main.exe add --description desc --amount 100 --testAmount 500 --category eat
2. Модифицировать запись: main.exe update --id 1 --description descUpdate --amount 150
3. Получить содержимое файла: main.exe list
4. Получить содержимое одной колонки: main.exe list --description
5. Удалить колонку: main.exe delcat --category
6. Посчитать сумму всех значений в колонке: main.exe summary --amount --testamount 
7. Посчитать сумму всех значений в колонке за месяц в определённом году: main.exe summary --month 7 --year 2026 --amount --testamount
8. Установить бюджет на определённую колонку: main.exe setbudget --month 7 --budget 10 --checkcol amount (если бюджет установлен будет автоматическая проверка превышения бюджета и соответствующее сообщение при превышении). 
При первом создании бюджета в текущей директории будет создан файл expense-options.json
9. Обновить бюджет: main.exe updatebudget --month 7 --budget 100 --checkcol amount
10. Получить список установленных бюджетов: main.exe listbudget
11. Удалить бюджет: main.exe deletebudget --month 7
12. Экспорт нового CSV с нужными колонками: main.exe export --id --description --amount (файл будет создан в текущей директории)


TODO:
clean-code: вынести отдельно анонимные функции для улучшения читаемости кода
tests: покрыть тестами
funcs: добавить экспорт CSV с фильтрами: по месяцу и году; по колонкам с числами (where column_value >= 0; <= 0)