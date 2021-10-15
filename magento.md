```text
if (!(bool)$debugMode && extension_loaded('xdebug')) {
    if (function_exists('xdebug_disable')) {
        xdebug_disable();
    }
}

https://magetv.belvgdev.com/mAcademyUiComponents/180%20Binding%20data%20from%20UI%20Components%20to%20KnockoutJS.mp4
https://magetv.belvgdev.com/mAcademyUiComponents/140%20Alternate%20UI%20Component%20JSON%20syntax.mp4
https://magetv.belvgdev.com/mAcademyUiComponents/190%20Create%20a%20KnockoutJS%20template.mp4

debug
https://magetv.belvgdev.com/mAcademyUiComponents/200%20Debug%20UI%20Components%20with%20uiRegistry.mp4
https://magetv.belvgdev.com/mAcademyUiComponents/210%20Get,%20set%20&%20remove%20UI%20Component%20properties.mp4

intercepter
5 - 2
plugin
5 - 4
filter
6 - 9
select, join, distinct
6 - 10
```
bin/magento setup:static-content:deploy -f -t Solera/wine

### Дима
```bash
php bin/magento setup:store-config:set --base-url="http://casadiluce.local:3010/"
php bin/magento setup:store-config:set --base-url-secure="https://casadiluce.local:3010/"
php bin/magento config:set web/secure/use_in_frontend 0
php bin/magento config:set web/cookie/cookie_domain 0                
php bin/magento config:set web/cookie/cookie_httponly 0
php bin/magento config:set web/secure/use_in_adminhtml 0

php bin/magento setup:upgrade
php bin/magento setup:di:compile
php bin/magento setup:static-content:deploy -f
php bin/magento cache:flush
chmod -R 777 var/ pub/ generated/

php bin/magento cache:flush

COMPOSER_MEMORY_LIMIT=-1 composer install --ignore-platform-reqs -vvv
```
### Log
```php
$objectManager = \Magento\Framework\App\ObjectManager::getInstance();
$log = $objectManager->create(\Psr\Log\LoggerInterface::class);
$log->debug($this->getQuoteId());
```
### Diag Js
```js
require('uiRegistry').get((uiItem) => console.log(uiItem.name))
```
