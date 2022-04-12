* `\с` - показывает в какой бд мы находимся и через какого юзера

* `\с name_of_db` - переключается к этой бд

* `\l` - показывает все бд

* `\dt` - показывает все таблицы в бд

* `\du` - показывает всех юзеров

* `\q` - выход


```sql
CREATE DATABASE name_of_db; 
-- создает базу данных
```

```sql
CREATE TABLE name_of_table (
    name_of_column1 data_type constraint,
    name_of_column2 data_type constraint,
    ...
); 
-- создает таблицу с полями
```

```sql
INSERT INTO name_of_table (name_of_column1, name_of_column2) 
VALUES (val1, val2);
-- добавляет запись в таблицу
```

```sql
SELECT * FROM name_of_table; 
-- достает все поля и записи из таблицы

SELECT name_of_column1, name_of_column2 FROM name_of_table; 
-- достает только указанные столбцы из таблицы

> primary key (pk)- pervichnyi klyuch
> eto ogranichenie, kotorye my ukazyvaem na te polya, 
kotorye doljny byt unikalnymi dlya togo
chto by potom ih ispolsovat v svyazyah (naprimer id)

> foreign key (kf) - vneshnii klyuch
> eto ogranichenie, kotoroe my ukazyvaem na te polya,
kotorye budut ssylatsya na pk v drugoi tablice, dlya sozdania svyazi 
```

```sql
CREATE TABLE author (
    id serial primary key,
    first_name varchar(50),
    last_name varchar(50),
)

CREATE TABLE book (
    id serial,
    title varchar(100),
    puplished year
    author_id int foreign key references author (id)
)
```
> JOIN - instrukcia, kotoraya pozvolyaet v zaprosah SELECT
brat dannye iz neskolkih tablic
> INNER JOIN (JOIN) - kogda dostayutsya tolko te zapisi, 
u kotoryh est polnaya svyaz  

> FULL JOIN - kogda dostayutsya absolyutno vse zapisi so vseh tablic
> LEFT JOIN - kogda dostayutsya vse zapisi s levoi tablicy i takje te zapisi s polnoi svyazyu 
> RIGHT JOIN - kogda dostayutsya vse zapisi s pravoi tablicy i takje te zapisi s polnoi svyazyu 

```sql
SELECT author.first_name, book.title
FROM author
JOIN book ON author.id = book.author_id
```

