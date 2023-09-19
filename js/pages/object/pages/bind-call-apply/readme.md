# `bind`, `call` и `apply`
> Методы, которые позволяют изменить контекст

<br> 

## 🚩 bind

### Синтаксис 👇
```javascript
function.bind(context, arg1, ..., argN)
```
<br>

### Пример 👇
```javascript
function myFn(phrase) {
  return `${phrase} ${this.name}`
}

const myObject = {
    name: 'Ben'
}

const fnWithContext = myFn.bind(myObject, 'Hi'),
      fnWithContext2 = myFn.bind(myObject)

fnWithContext()      //Hi Ben
fnWithContext2('By') //By Ben
```

<br>

### Важно ❗

🔴 `Не вызывает` возвращаемую функцию

🔴 Аргументы можно пробросить как при `bind`, так и через результат `bind`

<br>
<br>


## 🚩 call

### Синтаксис 👇
```javascript
function.call(context, arg1, ..., argN)
```
<br>

### Пример 👇
```javascript
function myFn(phrase) {
  return `${phrase} ${this.name}`
}

const myObject = {
    name: 'Ben'
}

const fnWithContext = myFn.bind(myObject, 'Hi'),
      fnWithContext2 = myFn.bind(myObject)

fnWithContext()      //Hi Ben
fnWithContext2('By') //By Ben
```

<br>

### Важно ❗

🔴 Сразу `вызывает` возвращаемую функцию

<br>
<br>


## 🚩 apply

### Синтаксис 👇
```javascript
function.apply(context, [array])
```
<br>

### Пример 👇
```javascript
function myFn(phrase) {
  return `${phrase} ${this.name}`
}

const myObject = {
    name: 'Ben'
}

const fnWithContext = myFn.bind(myObject, 'Hi'),
      fnWithContext2 = myFn.bind(myObject)

fnWithContext()      //Hi Ben
fnWithContext2('By') //By Ben
```

<br>

### Важно ❗

🔴 Сразу `вызывает` возвращаемую функцию

🔴 Принимает в качестве параметров `context` и `массив аргументов`

<br>
<br>


