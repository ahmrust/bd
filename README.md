### Домашнее задание к занятию «Базы данных»-Рустам Ахмадеев
### Инструкция по выполнению домашнего задания
1. Сделайте fork репозитория c шаблоном решения к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды git clone.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
впишите вверху название занятия и ваши фамилию и имя;
4. в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
для корректного добавления скриншотов воспользуйтесь инструкцией «Как вставить скриншот в шаблон с решением»;
при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в инструкции по MarkDown.
5. После завершения работы над домашним заданием сделайте коммит (git commit -m "comment") и отправьте его на Github (git push origin).
6. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
7. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.
Желаем успехов в выполнении домашнего задания.

Легенда
Заказчик передал вам файл в формате Excel, в котором сформирован отчёт.

На основе этого отчёта нужно выполнить следующие задания.
---
Задание 1
Опишите не менее семи таблиц, из которых состоит база данных:

какие данные хранятся в этих таблицах;
какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.
Приведите решение к следующему виду:

Сотрудники (

идентификатор, первичный ключ, serial,
фамилия varchar(50),
...
идентификатор структурного подразделения, внешний ключ, integer).

Решение 1
```
1. Сотрудники (Employees):
- employee_id (идентификатор, первичный ключ, serial)
- last_name (фамилия, varchar(50))
- first_name (имя, varchar(50))
- position_id (идентификатор должности, внешний ключ, integer)
- department_id (идентификатор структурного подразделения, внешний ключ, integer)
- address (адрес, varchar(100))
- project_id (идентификатор проекта, внешний ключ, integer)

Тип данных в PostgreSQL:
- employee_id serial PRIMARY KEY
- last_name varchar(50)
- first_name varchar(50)
- position_id integer REFERENCES Positions(position_id)
- department_id integer REFERENCES Departments(department_id)
- address varchar(100)
- project_id integer REFERENCES Projects(project_id)

2. Оклад (Salaries):
- salary_id (идентификатор, первичный ключ, serial)
- employee_id (идентификатор сотрудника, внешний ключ, integer)
- amount (сумма оклада, numeric(10,2))

Тип данных в PostgreSQL:
- salary_id serial PRIMARY KEY
- employee_id integer REFERENCES Employees(employee_id)
- amount numeric(10,2)

3. Должность (Positions):
- position_id (идентификатор, первичный ключ, serial)
- title (название должности, varchar(50))

Тип данных в PostgreSQL:
- position_id serial PRIMARY KEY
- title varchar(50)

4. Структурное подразделение (Departments):
- department_id (идентификатор, первичный ключ, serial)
- name (название подразделения, varchar(50))

Тип данных в PostgreSQL:
- department_id serial PRIMARY KEY
- name varchar(50)

5. Адрес (Addresses):
- address_id (идентификатор, первичный ключ, serial)
- employee_id (идентификатор сотрудника, внешний ключ, integer)
- address (адрес, varchar(100))

Тип данных в PostgreSQL:
- address_id serial PRIMARY KEY
- employee_id integer REFERENCES Employees(employee_id)
- address varchar(100)

6. Проект (Projects):
- project_id (идентификатор, первичный ключ, serial)
- name (название проекта, varchar(50))

Тип данных в PostgreSQL:
- project_id serial PRIMARY KEY
- name varchar(50)

7. Сотрудники-проекты (EmployeesProjects):
- employee_id (идентификатор сотрудника, внешний ключ, integer)
- project_id (идентификатор проекта, внешний ключ, integer)

Тип данных в PostgreSQL:
- employee_id integer REFERENCES Employees(employee_id)
- project_id integer REFERENCES Projects(project_id)

```
---
Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

## Задание 2*
Перечислите, какие, на ваш взгляд, в этой денормализованной таблице встречаются функциональные зависимости и какие правила вывода нужно применить, чтобы нормализовать данные.
