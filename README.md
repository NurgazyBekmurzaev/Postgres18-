

`\c` - pokazyvaet v kakoi BD my nahodimsya i cheres kakogo uzera
`\c` name_of_db - pereklyuchaetsya k etoi BD 
`\l` - pokazyvaet vse BD 
`\dt` - pokazyvaet vse tablicy v BD 
`\du` - pokazyvaet vseh userov
`\q` - vyhod 


```sql
"CREATE DATABASE name_of_db";
--- sozdaet bazu dannyh 
```

``` sql
"CREATE TABLE name_of_table (
    name_of_column1 data_type constraint,
    name_of_column2 data_type constraint,
    ...
);" 
``` 
--- sozdaet tablicu s polyami 



```INSERT INTO name_of_table (name_of_column) VALUES (val1, val2);```
--- dobavlyaet zapis v tablicu 

```SELECT * FROM name_of_table;```
 --- dostaet vse polyai zapisi is tablicy 

```SELECT name_of_column1, name_of_column2 FROM name_of_table;```
 --- dostaet tolko ukazannye stalbcy iz tablicu 
