# `useEffect`
> Хук, который позволяет выполнять побочные эффекты в функциональных компонентах
>
>  Например, выполнение кода после рендеринга компонента, обработка сетевых запросов, подписка на события

<br>

## 🚩 Синтаксис
```jsx
useEffect(callback, [depends]);
```
`callback` - функция, внутри которой будет что-то

`[depends]` - массив зависимостей

<br>

### Важно ❗

`useState` имеет доступ к предыщему состоянию
```jsx
setCount(prevCount => prevCount + 1);
```

<br>

## 🚩 Пример
```jsx
import React, { useState } from 'react';

function Counter() {
    // Используем useState с начальным состоянием 0
    const [count, setCount] = useState(0);

    const increment = () => {
        setCount(count + 1); // Обновляем состояние с новым значением
    };

    const decrement = () => {
        setCount(count - 1);
    };

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={increment}>Increment</button>
            <button onClick={decrement}>Decrement</button>
        </div>
    );
}

```
