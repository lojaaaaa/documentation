# `bind`, `call` и `apply`
> Методы, которые позволяют изменить контекст

<br> 

## 🚩 bind

Синтаксис
```javascript
function.bind(context, arg1, ..., argN)
```
<br>

Пример
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

## 🚩 function.call(context, arg1, ..., argN)


<br>


## 🚩 function.apply(context, [array])
