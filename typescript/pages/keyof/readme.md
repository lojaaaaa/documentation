# keyof
> Позволяет получать набор всех ключей (свойств или методов) объекта или типа

<br>

## Основной синтаксис
```typescript
interface Person {
    name: string;
    age: number;
}

type PersonKey = keyof Person; // "name" | "age"

```       

<br>
<br>

## Использование

<br>

<details>
<summary>🔹 Использование в `generic`</summary>

<br>
    
```typescript
interface Person {
    name: string;
    age: number;
}

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}

const person: Person = {
    name: "Alice",
    age: 30
};

const nameValue = getProperty(person, "name"); // nameValue - 'Alice'
const ageValue = getProperty(person, "age");   // ageValue - 30

```
<br>

🎯 `T` содержит типизированый объект `{name: string, age: number}`              
🎯 `K` при помощи `keyof` вынимает все ключи в виде строки из `T`  `'name' | 'age'`  
🎯 Вторым аргументом функции может быть только ключ, который есть в объекте первого аргумента

</details>

<br>    

<details>
<summary>🔹 Использование в цикле `key in`</summary>

<br>
    
```typescript
type FormProps = {
  name: string,
  age: number
}

type ValidationScheme<T> = {
  [K in keyof T]: {
      value: T[K],
      check: boolean,
      inputName: K
  }
}

type ValidationSchemeForm = ValidationScheme<FormProps>
```  
🎯 `FormProps` содержит имена инпутов формы, и тип их значения    
🎯 `ValidationScheme` служит как динамический генератор типов, параметров для каждого из инпута формы  
🎯 `ValidationSchemeForm` соеденительное звено, которое прокидывает через `generic`, все инпуты в генератор  

<br>

👆 `[K in keyof T]` конструкция делает следующиее  
&emsp;&emsp; 🎯 `keyof T` получает все ключи из полученного `generic` 👉🏼 (`'name' | 'age'`)  
&emsp;&emsp; 🎯 Все ключи перебираються в цикле, создавая новый типизированный объект с свойствами `{value: T[K], check: boolean, inputName: K}`   
&emsp;&emsp; 🎯 В переменную `K` по очередно попадают все ключи из `keyof T`: `'name', 'age'`   
&emsp;&emsp; 🎯 Имея ключ, можно получить и значение каждого ключа из `generic`, это происходит в переменной `value: T[K]`

```typescript
type ValidationSchemeForm = { // => результат работы K in keyof T 
     name: {
            value: string;
            check: boolean;
            inputName: "name";
     },
     age: {
         value: number;
         check: boolean;
         inputName: "age";
     }
}
```
</details>

