## Менеджер пакетов
Brew
* просмотр процессов brew services list
* остановка процесса brew services stop php@7.2
## nginx
* Запуск "nginx"
* Стоп nginx -s stop
* Конфиги в /usr/local/etc/nginx
* Каталог с сайтами $domain.test в /Users/medvedevevgenij/nginx/servers/
## Dnsmasq
/usr/local/etc/dnsmasq.conf
## Снимки экрана
* Поностью shift + cmd + 3
* Облость shift + cmd + 4
## Docker
* /var/www/bitrixdock
* docker-compose start
### Список сетей
docker network ls
### Получение информации о сети
docker network inspect MyOverlayNetwork
### Подключение работающего контейнера к сети
docker network connect MyOverlayNetwork nginx
### Подключение работающего контейнера к консоли
docker exec -it webserver bash


