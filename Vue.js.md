#js
![[vue-big.png|300]]
Документация: https://ru.vuejs.org/tutorial 
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

Мы можем использовать реактивное состояние объявленное в `<script setup>` в шаблоне для вывода динамического текста.
```js
<h1>{{ message }}</h1>
<p>Количество: {{ counter.count }}</p>
```
>[!Note]
>Причем содержимое `message` автоматически распакуется. Можем даже сделать вот так:
>```js
><h1>{{ message.split('').reverse().join('') }}</h1>
>```
## Связывание атрибутов
Для привязки атрибута к динамическому состоянию можем использовать директиву `v-bind` или более короткую запись `:` 
```js
<div v-bind:id="dynamicId"></div>
<div :id="dynamicId"></div>
```
>[!Note]
>**Директива** - это специальный атрибут, который начинается с префикса `v-`. Они являются частью синтаксиса шаблонов Vue. Подобно текстовым интерполяциям, значения директив представляют собой выражения JavaScript, которые имеют доступ к состоянию компонента.

## Слушатели событий
Чтобы слушать события в DOM можно использовать директиву `v-on` или более короткий вариант `@`:
```js
<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <button v-on:click="increment">Количество: {{ count }}</button>
  <button @click="increment">Количество: {{ count }}</button>
</template>
```
## Привязка форм
Можем привязывать элементы ввода формы, используя `v-bind` и `v-on`:
```js
<script setup>
import { ref } from 'vue'

const text = ref('')

function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <input :value="text" @input="onInput" placeholder="Пишите тут">
  <p>{{ text }}</p>
</template>
```
Для упрощения данной конструкции в Vue существует синтаксический сахар `v-model`
```js
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <input v-model="text" placeholder="Пишите тут">
  <p>{{ text }}</p>
</template>
```
## Условный рендеринг
https://ru.vuejs.org/tutorial/#step-6