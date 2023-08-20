# `useEffect`
> Хук, который позволяет выполнять побочные эффекты в функциональных компонентах
>
>  Например, выполнение кода после рендеринга компонента, обработка сетевых запросов, подписка и отписка на события

<br>

## 🚩 Синтаксис
```jsx
useEffect(callback, [depends]);
```
`callback` - функция, внутри которой будет что-то

`[depends]` - массив зависимостей

<br>

### Важно ❗

`[]` выполнится только после первого рендеринга компонента

Чтобы сделать очистку компонента (или чтобы отписаться от события) `callback` внутри useEffect должен возвращать функцию

```jsx
  useEffect(() => {
        window.addEventListener('resize', handleResize);

        // Возвращаем функцию очистки для отписки от события
        return () => {
            window.removeEventListener('resize', handleResize);
        };

```


<br>

## 🚩 Пример
```jsx
import React, { useState, useEffect } from 'react';

function DataFetching() {
    const [data, setData] = useState(null);

    useEffect(() => {
        fetch('https://api.example.com/data')
            .then(response => response.json())
            .then(data => setData(data))
            .catch(error => console.error(error));
    }, []);

    return (
        <div>
            {data ? (
                <p>Data: {data}</p>
            ) : (
                <p>Loading...</p>
            )}
        </div>
    );
}


```
