## Синхранизация с сервером
* rsync -avzhe ssh * ca77265@ca77265.tmweb.ru:public_html
* rsync -azvh www/upload/ /mnt/
* rsync -avzhe "ssh -p 2222" --progress root@ugautodetal.ru:'/home/vue/\[sharewood.biz\]\ Фреймворк\ NuxtJS/' .
* https://losst.ru/rsync-primery-sinhronizatsii
* --append-verify докачать файл

## Поиск find and grep
* find . -name 'linemedia.' -print -exec grep bitrix {} \\;
* find . -name 'linemedia.' -print -exec grep bitrix {} + вывод с именем файла
* find . -not -name 'test' -print -maxdepth 1 -exec rm -rf {} \\; удалить все кроме текущей папки
* find . -name '\*.php' -exec grep default_old1 {} +
* find . -ctime +0 -name '*.xml' -exec ls -lrth {} +

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

## конвертирование xls to csv cp1251
libreoffice  --convert-to csv --infilter=CSV:44,34,76,1 --headless --outdir dir file.xlsx

## Удалить добавить ip адрес
* ip a del 192.168.20.221/24 dev eth0
* ip a add 192.168.20.221/24 dev eth0
## Netstat
* MAC lsof -nP -i4TCP | grep LISTEN
* Windows netstat -nap tcp | find "9000"
* Linux netstat -nltp
* netstat -np tcp
## Wget
Продолжить закачку -c или -continue
### Внешний ip
* wget -qO- eth0.me
* wget -qO- ipinfo.io/ip
* wget -qO- ipecho.net/plain
* wget -qO- icanhazip.com
* wget -qO- ipecho.net
* wget -qO- ident.me
* wget -qO- myip.gelma.net
alias getip="wget -qO - eth0.me"
## firewalld документация
https://xakep.ru/2017/02/15/firewalld/
## Сброс пароля citrix
https://support.citrix.com/article/CTX214360
## ls
* -d использовать только имена каталога ,без файлов внутри
* ls -d \*/ показать только каталоги
* ls -d  .?* только скрытые
## iconv
* параметр -c пропустить warning
* iconv -fcp1251 -tutf8 file.txt
## vim
* gg -- в начало
* G  -- в конец
* dG удалить все до конца файла
## sudo
sudo -i переход в режим root
## Шпаргалка по Redis
https://habr.com/ru/post/204354/
## Установка Composer
* php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
* php -r "if (hash_file('sha384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
* php composer-setup.php --install-dir=/bin --filename=composer
* php -r "unlink('composer-setup.php');"
## Потребляемая ОЗУ
ps axo rss,comm,pid 
| awk '{ proc_list[$2]++; proc_list[$2 "," 1] += $1; } 
END { for (proc in proc_list) { printf("%d\t%s\n", 
proc_list[proc "," 1],proc); }}' | sort -n | tail -n 10 | sort -rn 
| awk '{$1/=1024;printf "%.0fMB\t",$1}{print $2}'
## Количество записий импорт Excel cron
mysql -e "use sitemanager; select count(id)  from b_iblock_element_prop_s10 join b_iblock_element on id = IBLOCK_ELEMENT_ID where PROPERTY_353 = 'ООО \"Ситилинк\"' and active = 'Y' limit 5;"
## Systemd
https://habr.com/ru/company/southbridge/blog/255845/
## Вытащить сертификаты с сайта
openssl s_client -showcerts -connect lektravs.ru:443
### Выйти из telnet 
*quit*
### Memcached cli
* http://dev-lab.info/2012/08/%D0%BCemcached-telnet-interface-%D0%BF%D0%BE%D0%B4%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BA-memcached-%D1%87%D0%B5%D1%80%D0%B5%D0%B7-telnet/
* Просмотреть весь кэш *memcached-tool localhost:11211 dump | less*
* stats cachedump 39 100

### Emoji github
https://www.webfx.com/tools/emoji-cheat-sheet/
### tail/head Пропустить 20 строк и распечатать 5
tail -25 file.txt | tail -5

### Punycode-конвертация
https://www.reg.ru/whois/

### Проверка порта
nc -z -v [hostname/IP address] [port number]
### Обнавление команды по умолчанию
update-alternatives --install /usr/bin/python python /usr/bin/python3 2
### Проверка SSL сертификатов
* openssl x509 -noout -text -in your.crt
* openssl rsa -noout -text -in your.key
### editor default
sudo update-alternatives --config editor
### Изменить часовой пояс.
sudo unlink /etc/localtime
sudo ln -s /usr/share/zoneinfo/Europe/Moscow /etc/localtime
### Ubuntu
update-alternatives --config php
### Проверка сертификата домена через консоль.
echo | openssl s_client -servername ugautodetal.ru -connect ugautodetal.ru:443 2>/dev/null | openssl x509 -noout -dates
### Передача параметров в конец
ls -rt ~/Downloads | tail -1 | xargs -tI% cp ~/Downloads/% . 
### SED песочница
https://sed.js.org/
### процессы
```
netstat -nltp
ss -nltp
ps afx
```
### Удаления мусора на yug.
ls  | grep -v v8_C187_148c4 |xargs rm

### Прослушивание порта
```sh
nc -l localhost 5555
telnet localhost 5555
```
