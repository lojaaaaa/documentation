# `Типы и интерфейсы`

<br>

## 🚩 `Интерфейсы` 
>Используются для определения структуры объектов, функций или классов

<br>

<details>
<summary>🔹 Интерфейсы могут быть объединены и расширены другими интерфейсами:</summary>

<br>

👇 Могут быть расширены через `extends`

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
👇 Могут быть объединены в тип путем использования оператора `&` (пересечение)

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

</details>

<br>

<details>
<summary>🔹 Интерфейсы с одинаковым названием дополняют друг друга</summary>

<br>

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

</details>
<br>

## 🚩 `Типы` 
>Используются для определения пользовательских типов данных и простых алиасов для существующих типов

<br>

<details>
<summary>🔹 Типы могут быть объединены в тип путем использования оператора `&` (пересечение)</summary>

<br>

```typescript
type Pet = { name: string };
type Dog = Pet & { breed: string };
```

</details>

<br>

<summary>🔹 Типы с одинаковым названием вызывают ошибку</summary>
