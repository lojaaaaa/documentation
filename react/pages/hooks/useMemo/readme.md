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

`useMemo` Может кэшировать не только значения, но и комопненты

<br>

## 🚩 Пример
```jsx
import React, { useState, useMemo } from 'react';

const CircleArea = ({ radius }) => {
  const area = useMemo(() => {
    return Math.PI * radius * radius;
  }, [radius]);

  return (
    <div>
      Радиус: {radius}
      <br />
      Площадь круга: {area}
    </div>
  );
};

const App = () => {
  const [radius, setRadius] = useState(5);

  return (
    <div>
      <CircleArea radius={radius} />
      <button onClick={() => setRadius(radius + 1)}>Увеличить радиус</button>
    </div>
  );
};

```
