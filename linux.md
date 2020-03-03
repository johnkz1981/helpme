## Синхранизация с сервером
* rsync -avzhe ssh * ca77265@ca77265.tmweb.ru:public_html
* rsync -azvh www/upload/ /mnt/
* rsync -avzhe "ssh -p 2222" --progress root@ugautodetal.ru:'/home/vue/\[sharewood.biz\]\ Фреймворк\ NuxtJS/' .
* https://losst.ru/rsync-primery-sinhronizatsii

## Поиск find and grep
*  find . -name 'linemedia.' -print -exec grep bitrix {} \\;
*  find . -name 'linemedia.' -print -exec grep bitrix {} + вывод с именем файла
*  find . -not -name 'test' -print -maxdepth 1 -exec rm -rf {} \\; удалить все кроме текущей папки

## Generate and copy public key
* ssh-keygen -t rsa -b 4096 -C "johnkz@inbox.ru"
* ssh-copy-id -i ~/.ssh/id_rsa.pub bitrix@192.168.0.102
## SSH тунель
* ssh -p2222 -N -L 3336:127.0.0.1:3306 bitrix@ugautodetal.ru
* mysql -ubitrix0 -p -h127.0.0.1 -P3336

## Backup sql
* day_month=`date +%d`
* /usr/bin/mysqldump sitemanager > /home/bitrix/backup/sql/$day_month.sql
* /usr/bin/zip /home/bitrix/backup/sql/$day_month.sql.zip /home/bitrix/backup/sql/$day_month.sql
* /usr/bin/rm /home/bitrix/backup/sql/$day_month.sql

## ssconvert centos 7
* wget http://repo.iotti.biz/CentOS/7/noarch/lux-release-7-1.noarch.rpm
* rpm -Uvh lux-release-7-1.noarch.rpm 
* yum install gnumeric

## Удалить добавить ip адрес
* ip a del 192.168.20.221/24 dev eth0
* ip a add 192.168.20.221/24 dev eth0
## Netstat
* MAC lsof -nP -i4TCP | grep LISTEN
* Windows netstat -nap tcp | find "9000"
* Linux netstat -nltp
## Wget
Продолжить закачку -c или -continue
## firewalld документация
https://xakep.ru/2017/02/15/firewalld/
## Сброс пароля citrix
https://support.citrix.com/article/CTX214360

