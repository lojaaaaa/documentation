# `useState`
> Хук, который позволяет добавить состояние в функциональные компоненты

<br>

## 🚩 Синтаксис
```jsx
const [state, setState] = useState(initialState);
```
`state` - текущее состояние

`setState` - функция для его обновления

`initialValue` - начальное значение состояния

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
