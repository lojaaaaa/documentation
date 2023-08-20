# `useRef`
> Хук, который используется для создания и управления ссылками на DOM-элементы или для хранения данных

<br>

## 🚩 Синтаксис

```jsx
const ref = useRef(initialValue);
```

`initialValue` - начальное значение ref

<br>

### Важно ❗

В отличие от `useState`, изменение значения `ref` не вызывает перерендеринг компонента

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
