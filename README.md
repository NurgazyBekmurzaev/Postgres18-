# Slash commands

* `\с` - показывает в какой бд мы находимся и через какого юзера

* `\с name_of_db` - переключается к этой бд

* `\l` - показывает все бд

* `\dt` - показывает все таблицы в бд

* `\du` - показывает всех юзеров

* `\q` - выход

# sozdanie BD i tablicy
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

# zapolnenie tablic

```sql
INSERT INTO name_of_table (name_of_column1, name_of_column2) 
VALUES (val1, val2);
-- добавляет запись в таблицу
```

# vyvod dannyh iz tablicy
```sql
SELECT * FROM name_of_table; 
-- достает все поля и записи из таблицы

SELECT name_of_column1, name_of_column2 FROM name_of_table; 
-- достает только указанные столбцы из таблицы

# svyazi 
## pk i fk
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
);

CREATE TABLE book (
    id serial,
    title varchar(100),
    puplished year
    author_id int foreign key references author (id)
);
```

## Vidy svyazi (teoria)

> One to one - (odin k odnomu)
naprimer:
* odin avtor  - odna biografia
* odin flag - odna strana
* odin chelovek - odna serdce

> one to many - (odin ko mnogim)
naprimer:
* odin chelovek - mnogo kletok, no u odnoi kletki tolko odin chelovek
* odni roditeli - mnogo detei, no u odnogo rebenka tolko odni roditeli
* odin akaunt mnogo postov, no u odnogo posta tolko odin akaunt
* odin makers - mnogo mentorov, no u odnogo mentora tolko odin makers

> many to many - (mnogie ko mnogim)
* u odnogo cheloveka mnogo druzei i u odnogo druga mnogo drugih druzei
* u doktora mnogo pacientov i u pacienta mnogo doktorov
* u polzovatelya mnogo socsetei i u odnoi secseti mnogo polzovatelei

## vidy svyazi (praktika)
### one to one 
```sql
create table flag (
    id serial primary key,
    photo text
)
create table country (
    id serial primary key,
    title varchar(50),
    gimn text,
    flad_id int unique,
    constraint fk_country_flag foreign key (flag_id) references flag(id)
);
```
### one to many 

```sql
create table account (
    id serial primary key,
    nick_name varchar(25) unique,
    u_password varchar(255)
)
create table post (
    id serial primary key,
    title varchar(100),
    body text,
    photo text,
    account_id int, 
    
    constraint fk_account_post foreign key (account_id) references account(id)
);

```
### many to many 

```sql
create table doctor (
    id serial primary key,
    first_name varchar(25),
    last_name varchar(50)
);

create table patient (
    id serial primary key,
    first_name varchar(25),
    last_name varchar(50)
 
);

create table doctor_patient (
    doctor_id int,
    patient_id int,

    constraint fk_doctor foreign key (doctor_id) references doctor(id), 
    
    constraint fk_patient foreign key (patient_id) references patient(id)
);
```




# JOIN
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
JOIN book ON author.id = book.author_id;
```
```sql
select first_name, last_name from customer order by first_name asc;
select first_name, last_name from customer order by first_name desc;
select first_name, length(first_name) as len from customer order by len desc;
select customer.customer_id, first_name, last_name, amount, payment_date from customer inner join payment on payment.customer_id = customer.customer_id order by payment_date;
```

# Import i export dannyh 
write from to db
```bash
psql db_name  < file.sql 
```
write from db to file
```bash
pg_dump db_name > file.sql
```




<!-- task1 -->

<!-- SELECT plaintext FROM wordform limit 10; -->

<!-- task2 -->

<!-- SELECT plaintext FROM wordform WHERE plaintext LIKE 'a%'; -->


<!-- task3  -->

<!-- SELECT title, genretype FROM work WHERE genretype = 'p'; -->

<!-- task4 -->

<!-- SELECT AVG( totalparagraphs ) AS avg FROM work where genretype = 't'; -->
