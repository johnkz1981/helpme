```text
if (!(bool)$debugMode && extension_loaded('xdebug')) {
    if (function_exists('xdebug_disable')) {
        xdebug_disable();
    }
}


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
### urn generated
```
dockergento magento dev:urn-catalog:generate 123
sed 's#/var/www/html#/home/johnkz/docker/100web#g' 123 > .idea/misc.xml
```
### mixin
```js
var config = {    
    config: {
        mixins: {
            'Magento_Ui/js/form/element/region': {
                'Vendor_StreetValidate/js/region-mixin': true
            }
        }
    }
};

define(['uiRegistry'], function (registry){
    return function (Select){
        return Select.extend({
            update: function (value) {
                this._super();
                registry.get(this.customName, function (input) {
                    input.validation['max_text_length'] = 30;
                }.bind(this));
            }
        })
    }
})
```
### path base lib js
vendor/magento/module-ui/view/base/web/js/lib
