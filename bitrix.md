## Избранное
* [Константы битрикса](https://dev.1c-bitrix.ru/api_help/main/general/constants.php)
* [Полезные вещи для Битрикса sadigi](https://github.com/sidigi/bitrix-info)
* [Потрясающий Битрикс](https://github.com/awesomebitrix/awesome-bitrix)
* [Битрикс проект](https://github.com/regiomedia/bitrix-project)

 ## LineMedia help
 * https://help.linemedia.ru/services/learning/course.php?COURSE_ID=4&INDEX=Y
 * http://auto.linemedia.ru/cms/video
 * https://www.youtube.com/watch?v=zB8mcpunMew
 * https://www.youtube.com/watch?v=4hevVnHXik8&t=1677s
 * https://www.lucidchart.com/documents/view/4e06-0c98-525bd01e-8fb3-56ae0a009f9d алгоритм поиска
 * demo сайта http://vitrina.auto-expert.info/
 * Для debug установить файл LinemediaAutoDebug::setOutputFilename($_SERVER['DOCUMENT_ROOT'] . '/__lm.log'); 
### Удаление события
```sql
delete from b_module_to_module where FROM_MODULE_ID = 'linemedia.autosuppliers' and MESSAGE_ID = 'OnAfterAdminMenuBuild';
```
### Распаковка архива битрикс
```sh
cat *$(ls -v  agroup23.ru_20220628_064101_full_eb4473d3.tar.gz*) | tar xzf -
```
### Чистый шаблон.
https://github.com/KarionovV/bitrixclear
### ORM
```php
$arRes = \Bitrix\Iblock\Elements\ElementElectronicsTable::query()
            ->registerRuntimeField("CNT", array(
                    "data_type" => "integer",
                    "expression" => array("count(%s)", "ID")
                )
            )
            ->registerRuntimeField("GROUP", array(
                    "data_type" => "string",
                    "expression" => array("group_concat(%s order by %s)", "ID", "ID")
                )
            )
            ->addSelect('CNT')
            ->addSelect('GROUP')
            ->addSelect('NO.VALUE', 'NO_')
            ->whereNotNull('NO.VALUE')
            ->addGroup('NO.VALUE')
            ->having('CNT', '>', '1')
            ->setLimit(10)
            //->getQuery();
            ->exec();

        //var_dump($arRes);
        while ($el = $arRes->fetch()){
            var_dump($el);
        }
   ```     
### Преобразавоние строки к нужному шаблону
```php
CComponentEngine::makePathFromTemplate('/personal/cancel/#ID#?', ['ID' => 6666])
```
### Меркуриал
hg diff -r436..437 php.d/30*

### Выборка конкретных полей
```php
\Bitrix\Iblock\Elements\ElementLmAutoDiscountTable::getByPrimary(296311, ['select' => ['NAME', 'discount']])->fetchObject();
```
### MailHog
http://ua.test/bitrix/admin/smtp_edit.php?ID=1&lang=ru
Поменять порт и сервер на localhost:1025
Сбросить кэш запустить агенты
./jedi cache:clear
./jedi agent:execute
