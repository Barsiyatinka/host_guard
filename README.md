# Домашнее задание к занятию   
**"`Базы данных`"** - `Воскобойников Арсений Петрович`  
   
**Задание 1**  
``` 
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

``` 

**Ответ**  

**1. Сотрудники (employees)**  
employees (  
    id serial PRIMARY KEY,  
    full_name varchar(100),  
    salary numeric(10,2),  
    position_id integer REFERENCES positions(id),  
    unit_type_id integer REFERENCES unit_types(id),  
    structural_unit_id integer REFERENCES structural_units(id),  
    hire_date date,  
    branch_id integer REFERENCES branches(id),  
    project_id integer REFERENCES projects(id)  
)  

**2. Должности (positions)**  

positions (  
    id serial PRIMARY KEY,  
    name varchar(50)  
)  

Примеры данных:  

старший инженер  

ведущий инженер  

разработчик  

специалист по персоналу   

ведущий QA инженер  

ведущий архитектор  

руководитель проектов и т.п.  

**3. Типы подразделений (unit_types)**  

unit_types (  
    id serial PRIMARY KEY,  
    name varchar(20)  
)  

Примеры данных:  

Группа  

Департамент  

Отдел  

**4. Структурные подразделения (structural_units)**  

structural_units (  
    id serial PRIMARY KEY,  
    name varchar(100)  
)  

Примеры данных:  

Группа Billing  

Центр анализа и архитектуры Medio  

Центр разработки Medio  

Департамент Rating and Charging и т.д.  

**5. Филиалы (branches)**  

branches (  
    id serial PRIMARY KEY,  
    postal_code varchar(10),  
    region varchar(100),  
    city varchar(100),  
    address varchar(200)  
)  

Примеры:  

31017, Краснодарский край, г. Краснодар, ул Путевая, д. 1  

230620, Ростовская обл, г. Ростов-на-Дону, ул 2-я Краснодарская, д. 135/2  

200113, Приморский край, г. Владивосток, ул Нижнепортовая, д. 1  

**6. Проекты (projects)**  

projects (  
    id serial PRIMARY KEY,  
    name varchar(150)  
)  

Примеры данных:  

{Газпромбанк Аквамарин АН, Гурзуф}  

{ИКСпФОН (РД)}  

{17110_2_ТМК}  

{Сколково}  

{Пансионат Дельфин (Крым)} и т.д.  

**7. Связи сотрудников и проектов (employee_projects) (если сотрудники могут быть назначены на несколько проектов)**  

employee_projects (  
    id serial PRIMARY KEY,  
    employee_id integer REFERENCES employees(id),  
    project_id integer REFERENCES projects(id)  
)  