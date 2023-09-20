# `Объекты`

<br>


## Важно ❗

🔴 `Переменные`, в которые помещают объекты, хранят в себе `не сам объект`, а `ссылку` на его место в памяти

🔴 Свойства объекта `изменяемые` даже если он был создан с помощью `const`

```javascript

const person = {
    firstName: "John",
    age: 30
};

person.age = 20

// Как будет выглядеть person
person = {
  firstName: "John",
  age: 20
};

```

❗ Если необходимо сделать объект `неизменяемым`, тогда `Object.freeze(person)`

<br>

## 🚩 Способы создания объекта

<br>

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

</details>

<br>

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

👆 Позволяет создавать новые объекты с указанным прототипом (существующим объектом)

❗ Это позволяет наследовать свойства и методы от другого объекта

</details>

<br>

<details>
<summary> 🔹 Конструктор класса (ES6+)</summary>
  
<br>

```javascript
class Person {
    constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
}

const john = new Person("John", "Doe", 30);

const john = {
  firstName = John,
  lastName = Doe,
  age = 30
}

```

👆 Позволяет создавать новые объекты с указанным прототипом (существующим объектом)

❗ Это позволяет наследовать свойства и методы от другого объекта

</details>

<br>

## 🚩 Способы обращения к свойствам

```javascript
const person = {
    firstName: "John",
    age: 30
};

// через .
console.log(person.firstName); // "John"

// через []
console.log(person["age"]); // 30


```


<br>

## 🚩 Сравнение объектов

<br>

<details>
<summary> 🔹 == </summary>
  
<br>

```javascript

// ссылаются на разные области в памяти (ссылки разные)
console.log({a: 1} == {a: 1}) // false

// ссылаются на одну и ту же область в памяти (ссылка одна и та же)
const a = { name: "John" };
const b = a;

console.log(a == b); // true


```

</details>

<br>

<details>
<summary> 🔹 json </summary>
  
<br>

```javascript

// Приводим объекты в json и сравниваем
JSON.stringify({a: 1}) === JSON.stringify({a: 1}) // true

```

❗ Свойства объектов должные иметь `одинаковый порядок`, иначе строки будут разными

</details>

