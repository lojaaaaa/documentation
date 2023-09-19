# `this`
> Контекст, который ссылается на тот объект, в контексте которого он был вызван

<br>

## 🚩 Пример

```javascript
let user = {
  name: "John",
  age: 30,

  sayHi() {
    // "this" - это "текущий объект".
    alert(this.name); // или alert(user.name)
  }

};

user.sayHi(); // John

```
👉 Значение в `this` – это объект «перед точкой», который используется для вызова метода

<br>

### Важно ❗

Стрелочная функция `не` имеет своего «собственного» `this`

```javascript
let user = {
  firstName: "Ilya",
  sayHi() {
    let arrow = () => alert(this.firstName); // this ссылается на контекст метода sayHi(), т.е на объект `user`
    arrow();
  }
};

user.sayHi(); // Ilya

```

