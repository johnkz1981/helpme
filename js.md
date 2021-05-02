### Observer
https://habr.com/ru/post/494670/
### Дерективы VUE
https://webdevblog.ru/15-obyazatelnyh-direktiv-vue-kotorye-znachitelno-uvelichat-vashu-proizvoditelnost/
### reactive time vuejs
https://cushionapp.com/journal/reactive-time-with-vuejs
### Сервер JSON
* https://jsonplaceholder.typicode.com/
* https://restcountries.eu/ *API стран*
* https://www.boredapi.com/
### SOAP
Программа для тестирования https://www.soapui.org/
### get_obj_methods
```js
const getMethods = (obj) => {
    let properties = new Set()
    let currentObj = obj
    do {
      Object.getOwnPropertyNames(currentObj).map(item => properties.add(item))
    } while ((currentObj = Object.getPrototypeOf(currentObj)))
    return [...properties.keys()].filter(item => typeof obj[item] === 'function')
  };
  ```
### Нативные аналоги jQuery 
https://dev-gang.ru/article/nativnye-analogi-jquery-93vqf10ia8/
