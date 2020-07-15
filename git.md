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
#### Решить вопрос с git push 
warning: push.default is unset; its implicit value is changing in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the current behavior after the default changes, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, use:

  git config --global push.default simple

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)
