# `typeof`
>  Используется для извлечения типа значения или переменной

<br>

🔹 Примитив
```typescript
const userAge = 22

type User = {
  age: typeof userAge // 👉🏼 age: number
}
```   
&emsp;&emsp; 👆 `typeof any` возвращает типы, которые могут быть ключами объекта `(string | number | symbol)`    
   

🔹 Объект      
```typescript
const user = {
  name: 'myUser'
}

type User = typeof user // 👉🏼 type User = {name: string}
```

🔹 Массив      
```typescript
const arrayData = [1, 2, '3', true]

type TypedArray= typeof arrayData // 👉🏼 type TypedArray = (string | number | boolean)[]
```

<br>
