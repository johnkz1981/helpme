
## Mysql
## Сброс пароля 
1. Stop mysql:
systemctl stop mysqld

2. Set the mySQL environment option 
systemctl set-environment MYSQLD_OPTS="--skip-grant-tables"

3. Start mysql usig the options you just set
systemctl start mysqld

4. Login as root
mysql -u root

5. Update the root user password with these mysql commands
mysql> UPDATE mysql.user SET authentication_string = PASSWORD('>ufdnjltnfkm!@#$%*') WHERE User = 'root' AND Host = 'localhost';
mysql> FLUSH PRIVILEGES;
mysql> quit

6. Stop mysql
systemctl stop mysqld

7. Unset the mySQL envitroment option so it starts normally next time
systemctl unset-environment MYSQLD_OPTS

8. Start mysql normally:
systemctl start mysqld

## Сменить пользователя
ALTER USER 'root'@'localhost' IDENTIFIED BY '>ufdnjltnfkm!@#$%*';

## Создать БД
CREATE DATABASE sitemanager CHARACTER SET utf8 COLLATE utf8_general_ci;

## Просмотр количество строк
select TABLE_NAME, table_rows from information_schema.tables where table_name like 'b_iblock_el%';

## timezone
* SELECT @@global.time_zone;
* SET GLOBAL time_zone = 'Europe/Moscow';
* Если ошибка то вначале  mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql mysql
* [mysqld]
* default-time-zone="Europe/Moscow"

## sql light to csv
sqlite3  -csv v8_6533_13dce.db  "select * from Goods limit 2;" > tracks.csv

