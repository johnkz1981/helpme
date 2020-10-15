
## Mysql
## При подключении PHPSTORM не забыть проверить прослушиваемый tcp
## Сброс пароля 
```shell
systemctl stop mysqld
systemctl set-environment MYSQLD_OPTS="--skip-grant-tables"
systemctl start mysqld
mysql -u root
```
```sql
UPDATE mysql.user SET authentication_string = PASSWORD('>ufdnjltnfkm!@#$%*') WHERE User = 'root' AND Host = 'localhost';
FLUSH PRIVILEGES;
quit
```
```shell
systemctl stop mysqld
systemctl unset-environment MYSQLD_OPTS
systemctl start mysqld
```
## Сменить пользователя
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY '>ufdnjltnfkm!@#$%*';
```
## Создать БД
```sql
CREATE DATABASE sitemanager CHARACTER SET utf8 COLLATE utf8_general_ci;
GRANT ALL PRIVILEGES ON sad.* TO bitrix0@localhost;
flush privileges;
```
## Просмотр количество строк
```sql
select TABLE_NAME, table_rows from information_schema.tables where table_name like 'b_iblock_el%';
```
## Размер бд
```sql
SELECT table_schema AS "Имя базы данных",
в Мб"> ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS "Размер  
    -> FROM information_schema.TABLES
    -> GROUP BY table_schema;
```
## Размер таблиц в бд
```sql
SELECT table_name AS "Имя таблицы",
ROUND(((data_length + index_length) / 1024 / 1024), 2) AS "Size in (MB)"
FROM information_schema.TABLES
WHERE table_schema = "wpfc_options"
ORDER BY (data_length + index_length) DESC;
```
## timezone
```sql
* SELECT @@global.time_zone;
* SET GLOBAL time_zone = 'Europe/Moscow';
* Если ошибка то вначале  mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql mysql
* [mysqld]
* default-time-zone="Europe/Moscow"
```
## sql light to csv
```shell
sqlite3  -csv v8_6533_13dce.db  "select * from Goods limit 2;" > tracks.csv
```
## Портицирование
0. alter table b_iblock_element_prop_s10 drop primary key;
0. alter table b_iblock_element_prop_s10
add primary key (IBLOCK_ELEMENT_ID, PROPERTY_540);
0.  alter table b_iblock_element_prop_s10
    PARTITION BY LIST(PROPERTY_540) (
          PARTITION citilink VALUES IN (12),
          PARTITION other VALUES IN (0)
    );
0. SELECT TABLE_NAME, PARTITION_NAME, TABLE_ROWS, AVG_ROW_LENGTH, DATA_LENGTH
      FROM INFORMATION_SCHEMA.PARTITIONS
       WHERE TABLE_NAME = 'b_iblock_element_prop_s10';
## Обычный индекс с ограничением на 10 символов
```sql
 create index articul on b_iblock_element_prop_s10 (PROPERTY_389(10));
 ```
## Информация о таблице в том числе и следующий *autoincrement*
```sql
SHOW TABLE STATUS FROM `database` LIKE 'table'
```
## sqlite info table
```sql
pragma table_info('Remainder');
```
