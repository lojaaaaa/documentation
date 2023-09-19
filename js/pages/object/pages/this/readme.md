# this
> Контекст, который ссылается на тот объект, в контексте которого он был вызван

```javascript
let user = {
  name: "John",
  age: 30,

  sayHi() {
    // "this" - это "текущий объект".
    alert(this.name);
  }

};

user.sayHi(); // John


```
