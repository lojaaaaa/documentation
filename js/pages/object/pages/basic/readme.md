# `Объекты`

<br>

## 🚩 Способы создания объекта

<details>
<summary> 🔹 {...} или new Object() </summary>
  
<br>

```javascript

// {...}
const person = {
    firstName: "John",
    age: 30
};


// new Object() 
const person = new Object()
person.firstName = "John"
person.age = 30


```

👆 Смена вершины ветки `master`, на коммит вершины ветки `fix`  
&emsp;&emsp; ❗ Произойдет только в том случаи, если вершиной ветки `master` будет тот коммит, от которого был создан `fix`

</details>



<details>
<summary> 🔹 Object.create() </summary>
  
<br>

```javascript
const personPrototype = {
    greet: function() {
        console.log("Hello!");
    }
};

const john = Object.create(personPrototype);
john.firstName = "John";
john.lastName = "Doe";
john.age = 30;



```

👆 Позволяет создавать новые объекты с указанным прототипом (существующим объектом).

Это позволяет наследовать свойства и методы от другого объекта

</details>

