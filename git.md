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
### new repository
```
Глобальные настройки Git
git config --global user.name "johnkz1981"
git config --global user.email "johnkz@inbox.ru"

Создать новый репозиторий
git clone git@gitlab.com:johnkz1981/test.git
cd test
git switch -c main
touch README.md
git add README.md
git commit -m "add README"
git push -u origin main

Отправить существующую папку
cd existing_folder
git init --initial-branch=main
git remote add origin git@gitlab.com:johnkz1981/test.git
git add .
git commit -m "Initial commit"
git push -u origin main

Отправить существующий репозиторий Git
cd existing_repo
git remote rename origin old-origin
git remote add origin git@gitlab.com:johnkz1981/test.git
git push -u origin --all
git push -u origin --tags
```
### Check ignore
git check-ignore -v
### Оформление коммитов BELVG
https://youtrack.belvgdev.com/articles/ADM-A-58/General-rules
