#js
![[vue-big.png|300]]
## Реактивные состояния
Объявляем реактивное состояние, используя `reactive()` 
```js
import { reactive } from 'vue'

const counter = reactive({
  count: 0
})
```
>[!Note]
>`reactive()` только для объектов, для любого типа можем использовать `ref()` и получать его значение через атрибут `.value`
>```js
>import { ref } from 'vue'
>
>const message = ref('Привет мир!')
>
>console.log(message.value) // "Привет мир!"
>message.value = 'Изменено'
>```

## Связывание атрибутов
