### Гит работа с ветками
* git clone --branch=johnkz git@gitlab.com:netlab-cod/cod-new-front.git .
* git brunch -r # просмотр ветки
* git push origin johnkz
## Git откат коммита 
git revert 263f6a51
 ### Временное переключение
* git checkout '214f4d7e'
* Возврат git checkout johnkz
### Git 2.0
git add -A .

### Подключить внешнюю ветку
* git remote add origin git@bitbucket.org:huntworld/main_repo.git
* git remote -v

### Обновить репозиторий
git pull
### Создание ветки и связка с существующей
git checkout -b huntSelf origin/huntSelf

### revert файла
git checkout HEAD cron/_image_optimizer.list 
