## CML2 agroup23 row=6241
```php
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
```

## Bitrix key
 bitrix/modules/main/include.php
 
 ## LineMedia help
 * https://help.linemedia.ru/services/learning/course.php?COURSE_ID=4&INDEX=Y
 * http://auto.linemedia.ru/cms/video
 * https://www.lucidchart.com/documents/view/4e06-0c98-525bd01e-8fb3-56ae0a009f9d алгоритм поиска
 * demo сайта http://vitrina.auto-expert.info/
 * Для debug установить файл LinemediaAutoDebug::setOutputFilename($_SERVER['DOCUMENT_ROOT'] . '/__lm.log');
 
 ## Полезные ссылки 
 * https://forwww.com/bitrix-articul-search-p2/ добавление артикула в поиск
 * новая таблица в админке https://coderun.ru/blog/bitrix-grid-v-adminke-ili-kak-pokazyvat-tablichnye-dannye-v-svojom-module-krasivo/
 * кастомные компоненты http://bbc.samokhvalov.info/
 * апи Артоманова https://github.com/johnkz1981/artamonov.api
 * интерфейс битрикс в ядре d7 https://dev.1c-bitrix.ru/api_d7/bitrix/ui/index.php
 * composer bitrix https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=43&LESSON_ID=4637&LESSON_PATH=3913.4776.2483.4637
 * vue.js bitrix https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=43&CHAPTER_ID=011881&LESSON_PATH=3913.4776.11881
 * https://www.intervolga.ru/blog/projects/poleznye-instrumenty-dlya-tekh-kto-v-odnoy-lodke-s-bitrix/#section6
 * Настройка виртуальной машины битрикс https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=37&CHAPTER_ID=08809&LESSON_PATH=3908.8809
 * Настройка инфоблоков Базаров https://www.youtube.com/watch?v=1KP1cWM26tU
 
 ## Сайт югавтодеталь
 * /www/bitrix/modules/main/admin/partner_modules.php
 ```php
 //$arRequestedModules = CUpdateClientPartner::GetRequestedModules("");
 
 //$arUpdateList = CUpdateClientPartner::GetUpdatesList($errorMessage, LANG, $stableVersionsOnly, $arRequestedModules, Array("fullmoduleinfo" => "Y"));
 $strError_tmp = "";
 // $arClientModules = CUpdateClientPartner::GetCurrentModules($strError_tmp);
 ```
 * /www/bitrix/modules/main/admin/update_system_partner.php
 ```php
 /*
 if (strlen($errorMessage) > 0)
 	echo  CAdminMessage::ShowMessage(Array("DETAILS" => $errorMessage, "TYPE" => "ERROR", "MESSAGE" => GetMessage("SUP_ERROR"), "HTML" => true));
 */
 ```
 ## Вручную убрать модуль из массива
 /www/bitrix/modules/main/interface/prolog_main_admin.php
 
 ```php
 $adminPage->Init();
 unset($adminPage->aModules[49]);
 var_dump($adminPage->aModules);
 // Где 49 ключ модуля в массиве
 ```
## Тикет в техподдержки
https://dev.1c-bitrix.ru/community/forums/messages/forum7/topic129058/message642762/?result=new#message642762
