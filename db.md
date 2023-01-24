
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
SHOW GRANTS FOR 'jeffrey'@'localhost';
```
## Просмотр количество строк
```sql
select TABLE_NAME, table_rows from information_schema.tables where table_name like 'b_iblock_el%';
```
## Размер бд
```sql
SELECT table_schema AS "Имя базы данных",
ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS "Размер"  
FROM information_schema.TABLES
GROUP BY table_schema;
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
SELECT @@global.time_zone;
SET GLOBAL time_zone = 'Europe/Moscow';
Если ошибка то вначале  mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql mysql
[mysqld]
default-time-zone="Europe/Moscow"
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
## remove protection
```
sed -i 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' dump.sql
```
## backup mysql
```sh
#!/bin/sh

#var
USER="user"
PASS="password"
DIR="/var/www/backup/mysql/daily"

cd "$DIR"

if [ ! -d "$DIR" ]
then
mkdir -p $DIR
fi

LOG="/var/log/mysql_dump.log"
if [ ! -f "$LOG" ]
then
touch $LOG
fi

TIMENAME=`date +%d.%m.%Y-%H.%M`
db=`mysql -u$USER -p$PASS -Bse 'show databases' | grep -v information_schema | grep -v mysql | grep -v performance_schema | grep -v sys`
for n in $db; do
        TIMEDUMP=`date '+%T %x'`
        echo "backup has been done at $TIMEDUMP : $TIMENAME on db: $n" > $LOG
    nice -n 19 mysqldump --opt --disable-keys --single-transaction --routines --no-tablespaces -u$USER -h localhost -p$PASS $n | gzip -9 > "$DIR/$n-$TIMENAME.sql.gz"
done


#rotate
#cd "$DIR"
if [ ! -d $DIR ];
then
echo "$DIR dir tot found!!!"
exit 1
else
find $DIR -type f -mtime +6 -name "*.sql.gz" | xargs rm -f
fi
```

## Создание и импорт БД
```sql
# mysql -uroot -p
password
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> set global log_bin_trust_function_creators = 1;
mysql> quit;

# zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix

# mysql -uroot -p
password
mysql> set global log_bin_trust_function_creators = 0;
mysql> quit;
```
