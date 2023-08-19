# Generic
> Обобщенные типы, которые нужны для описания похожих, но отличающихся какими-то характеристиками типов

❗ Имеют доступ друг к другу, вне зависимости от порядка объявления

<br>

## 🚩 Наименование

🔹 E - Element        
🔹 K - Key  
🔹 T - Type  
🔹 V - Value  
🔹 S,U,V etc. - 2nd, 3rd, 4th types

<br>

## 🚩 Основной синтаксис

<details>
<summary>🔹 Generic в type</summary>
 
<br>
 
👇 В конструкцию `type`, дженерик требует указать тип, или данные, которые попадут в `T`

```typescript
type MyType<T> = T

type A = MyType<string>  // A: string
type B = MyType<'hello'> // A: 'hello'
```
 </details>

<br>

<details>
<summary>🔹 Generic в интерфейсах</summary>
 
<br>
 
👇 В конструкцию `interface`, дженерик требует указать тип, или данные, которые попадут в `T`

```typescript
interface MyType<T> {
    element: T
}

type A = MyType<string>  // A: {element: string}
type B = MyType<'hello'> // A: {element: 'hello'}
```
 </details>

<br>

<details>
<summary>🔹 Generic в функциях</summary>
 
<br>
 
👇 В функциях, дженерик могу преобразовывать переданные параметры функции, помещать их в `<T>`

```typescript
function myFn<T>(data: T, name: string):T {
  return data
}

const myFnResult = myFn(55, 'Den') // myFnResult: number
```

🎯 При вызове `myFn`, `55` было преобразованно к типу `typeof 55`, получилось `number`  
🎯 Вместо `T` везде будет установлен `number`

</details>
 
<br>

## 🚩 Ограничение дженериков
> Дженерик может принимать в себя любой тип, но есть методы с узить его диапазон

<br>

Конструкция `extends` описывает от какого типа должен быть унаследован дженерик

```typescript
function myFn<T extends {name: string}>(data: T, adress: string):T {
  return data
} // 🎯 data должна обязательно сожержать в себе свойство name

interface MyType<T extends number | boolean> {
  element: T
} // 🎯 T должен быть либо number либо boolean

type A = MyType<number>
```

<br>

## 🚩 Never для исключения типов
> never в generic часто используют для исключения каких либо типов

<br>

```typescript
type GetValues<T, R extends T> = T extends R ? T : never

type sizes = 'sm' | 'md' | 'lg'

type gridSize = GetValues<sizes, 'sm' | 'md'> // 👉🏼 gridSize: 'sm' | 'md'
``` 
🎯 Когда в `generic` попадает `union` тип, они по очереди проходят через конструкцию `generic`
🎯 Сначала `sm` сравниваеться с `'sm' | 'md'`
🎯 Если `sm` подходит под тип `'sm' | 'md'`
🎯 То `sm` помещаеться в результат
🎯 Если нет, то этого типа не будет в результате

<br>

