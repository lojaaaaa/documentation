# `Типы и интерфейсы`

<br>

## 🚩 `Интерфейсы` 
>Используются для определения структуры объектов, функций или классов

<br>

### Интерфейсы могут быть объединены и расширены другими интерфейсами:   

🔵 Могут быть расширены через `extends`

```typescript
interface User {
  name: string
}

interface Developer {
  direction: string
}

interface Student extends User, Developer {
  // 👉🏼 name: string будет унаследованно  
  // 👉🏼 direction: string будет унаследованно  
  age: number
}
```
🔵 Могут быть объединены в тип путем использования оператора `&` (пересечение)

```typescript
interface X {
    commonProp: string;
    uniqueX: number;
}

interface Y {
    commonProp: string;
    uniqueY: boolean;
}

type XY = X & Y;
```

&emsp;&emsp; 🛑 Нельзя екстендиться от типов которые содержат в себе `union`
```typescript
interface User {
  name: string
}

interface Developer {
  direction: string
}

interface Student extends User, Developer {
  // 👉🏼 name: string будет унаследованно  
  // 👉🏼 direction: string будет унаследованно  
  age: number
}
```

<br>

&emsp;&emsp; 🔹 Интерфейсы с одинаковым названием дополняют друг друга
```typescript
interface User {
  name: string
}

interface User {
  age: number
}

const user:User = {
  name: 'Jon',
  age: 22
}
```

<br>

&emsp;&emsp; 🔹 Синтаксис типизации `function Expression`     
```typescript
interface GetData {
  (name: string, age: number): string;
}

// 🎯 Arrow expression
let getData1: GetData = (name, age) => {
  return `${name} ${age}`
}

// 🎯 Function expression
let getData2: GetData = function(name, age) {
  return `${name} ${age}`
}

// 🎯 Expression after typing 
let getData3: GetData

getData3 = function(name, age) {
            return `${name} ${age}`
}
``` 

<br>

&emsp;&emsp; 🔹 у `function Declaration`, может типизировать только аргументы по одному    
```typescript
interface Data {
  name: string,
  age: number
}

function getData(props:Data, count: number) {
  const {age, name} = props

  return `${name} ${age}`;
}
```

<br><br>

💠 **Тип**   
👆🏽 Переменная описывающий типизацию, но не реализацию

<br>

&emsp;&emsp; 🔹 Могут наследоваться друг от друга, при помощи `пересечения типов`  
&emsp;&emsp;&emsp;&emsp; 👆 Поддерживают множественное наследование            
```typescript
type User = {
  name: string
}

type Developer = {
  direction: string
}

type Student = User & Developer & {age: number} // 👉🏼 {name: string, direction: string, age:number}
```

<br>

<br>

&emsp;&emsp; 🔹 Могут указать группу типов возможных для наследования
```typescript
type User = {
    name: string
}

type Developer = {
    direction: string
}

type Student = User | Developer

const student1:Student = { // 👉🏼 Valid
    name: 'Alex',
    direction: 'Frontend'
}

const student2:Student = { // 👉🏼 Valid
    name: 'Alex'
}

const student3:Student = { // 👉🏼 Valid
    direction: 'Frontend'
}

const student4:Student = { // 👉🏼 Invalid
    
}
```

&emsp;&emsp; 🔹 Одинаковые название вызывают ошибку      

&emsp;&emsp; 🔹 Синтаксис типизации `function Expression`
```typescript
type GetDataLikeInterface = {
  (name: string, age: number): string;
};

type GetData = (name: string, age: number) => string;

let getData: GetData = function (name, age) {
  return `${name} ${age}`;
};
```      

<br>

&emsp;&emsp; 🔹 у `function Declaration`, может типизировать только аргументы по одному    
```typescript
interface Data {
  name: string,
  age: number
}

function getData(props:Data, count: number) {
  const {age, name} = props

  return `${name} ${age}`;
}
```

<br>

&emsp;&emsp; 🔹 Типизировать конкретные значения
```typescript
type sizes = 'sm' | 'md' | 'lg'
```

<br>

### ⟵ **<a href="../../readme.md">Назад</a>**
