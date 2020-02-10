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
* SET GLOBAL time_zone = 'Europe/Moscow';
* Если ошибка то вначале  mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql mysql

## Гит работа с ветками
git clone --branch=johnkz git@gitlab.com:netlab-cod/cod-new-front.git .

git brunch -r # просмотр ветки

git push origin johnkz

## Синхранизация с сервером
* rsync -avzhe ssh * ca77265@ca77265.tmweb.ru:public_html
* rsync -azvh www/upload/ /mnt/
* rsync -avzhe "ssh -p 2222" --progress root@ugautodetal.ru:'/home/vue/\[sharewood.biz\]\ Фреймворк\ NuxtJS/' .
* https://losst.ru/rsync-primery-sinhronizatsii

## CML2 agroup23 row=6241

    $START_ID = 148150;
    $LAST_ID = 148200;

    if($this->next_step["LAST_ID"] == $LAST_ID){
      $this->next_step["LAST_ID"]++;
    }

		if(is_array($arElementFilter))
		{
			$arFilter = $arElementFilter;
		}
		else
		{
			if($arElementFilter === "none")
				return 0;
			$arFilter = array (
				"IBLOCK_ID"=> $this->arIBlock["ID"],
				"ACTIVE" => "Y",
				"><ID" => [$START_ID > $this->next_step["LAST_ID"] ? $START_ID: $this->next_step["LAST_ID"], $LAST_ID],
			);
			if($arElementFilter === "all")
				unset($arFilter["ACTIVE"]);
		}

## Generate and copy public key
* ssh-keygen -t rsa -b 4096 -C "johnkz@inbox.ru"
* ssh-copy-id -i ~/.ssh/id_rsa.pub bitrix@192.168.0.102

## Git откат коммита 
git revert 263f6a51
 ### Временное переключение
* git checkout '214f4d7e'
* Возврат git checkout johnkz 
## Bitrix key
 bitrix/modules/main/include.php
## Backup sql
* day_month=`date +%d`
* /usr/bin/mysqldump sitemanager > /home/bitrix/backup/sql/$day_month.sql
* /usr/bin/zip /home/bitrix/backup/sql/$day_month.sql.zip /home/bitrix/backup/sql/$day_month.sql
* /usr/bin/rm /home/bitrix/backup/sql/$day_month.sql
## ssconvert centos 7
* wget http://repo.iotti.biz/CentOS/7/noarch/lux-release-7-1.noarch.rpm
* rpm -Uvh lux-release-7-1.noarch.rpm 
* yum install gnumeric

## Table example
one|two|free|for
---|---|---|---
1  | 2 | 3 | 4
3  | 4 | 5 | 6
5  | 6 | 7 | 8
 
## LineMedia help
* https://help.linemedia.ru/services/learning/course.php?COURSE_ID=4&INDEX=Y
* http://auto.linemedia.ru/cms/video
## PhpStorm
* ctrl + shift + del удаление тега
* ctrl + shift + ins множественный буфер обмена
## https://coderun.ru/blog/bitrix-grid-v-adminke-ili-kak-pokazyvat-tablichnye-dannye-v-svojom-module-krasivo/
