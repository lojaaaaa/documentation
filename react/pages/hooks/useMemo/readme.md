# `useMemo`
> Хук, который используется для кэширования результатов вычислительных функций, чтобы избежать повторных вычислений в случаях, когда входные данные не изменились

<br>

## 🚩 Синтаксис
```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
`computeExpensiveValue` - функция, результат которой нужно кэшировать

`[a, b]` - массив зависимостей


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
