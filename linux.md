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
* ``` find . -ctime -5 -regex '.*csv\|.*\.xls' ```

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
## ls
* -d использовать только имена каталога ,без файлов внутри
* ls -d \*/ показать только каталоги
* ls -d  .?* только скрытые
## vim
* gg -- в начало
* G  -- в конец
* dG удалить все до конца файла
## Вытащить сертификаты с сайта
openssl s_client -showcerts -connect lektravs.ru:443

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
### SED песочница
https://sed.js.org/
### процессы
```
netstat -nltp
ss -nltp
ps afx
```
### Прослушивание порта
```sh
nc -l localhost 5555
telnet localhost 5555
```
### Инфо о файле
stat

### Добавления и удаления пользователя из группы.
  ```bash
  usermod -aG wheel bitrix  
  gpasswd -d bitrix wheel
  ```
### Переменные: все, код ошибки, шелл, path
```
set
echo $?
echo $0 echo $SHELL
echo $PATH
```
### Чистый конфиг
```
egrep -vn '^;|^$' /etc/php/8.2/fpm/pool.d/www.conf
```
