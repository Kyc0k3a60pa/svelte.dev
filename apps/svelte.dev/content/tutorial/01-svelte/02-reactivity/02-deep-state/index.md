---
title: Deep state  ( _глубокое состояние_ ?)
---

Как мы видели в предыдущем упражнении, состояние реагирует на _переназначения_ ( _reassignments_ ). Но оно также реагирует на _мутации_ ( _mutations_ ) — мы называем это _глубокой реактивностью_ ( _deep reactivity_ ).

Сделаем `numbers` реактивным массивом:

```js
/// file: App.svelte
let numbers = +++$state([1, 2, 3, 4])+++;
```

Теперь, когда мы изменяем массив...

```js
/// file: App.svelte
function addNumber() {
	+++numbers[numbers.length] = numbers.length + 1;+++
}
```

...компонент обновляется. Или, что еще лучше, мы можем вместо этого `push` в массив:

```js
/// file: App.svelte
function addNumber() {
	+++numbers.push(numbers.length + 1);+++
}
```

> [!ПРИМЕЧАНИЕ] Глубокая реактивность реализована с использованием [прокси](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy), и мутации в прокси не влияют на исходный объект.
