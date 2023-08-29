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

Если вы возвращаете новый объект или массив с теми же значениями, `useMemo` по-прежнему выполнит вычисления

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


<br>

## 🚩 Когда лучше использовать

<br>

### 🔴 Мемоизация входящих данных
```jsx
import React from 'react';

const RecipeCard = ({ recipe }) => {
  return (
    <div>
      <h3>{recipe.title}</h3>
      {/* Остальной код */}
    </div>
  );
}

export default React.memo(RecipeCard); // Мемоизация компонента


```
👉 Если данные из Redux редко изменяются и передаются в компонент через пропсы, мемоизация этих пропсов помогает избежать ненужных ререндеров

<br>

### 🔴 Мемоизация обработчиков событий
```jsx
const RecipeCard = ({ recipe, onDelete }) => {
  const handleClick = useCallback(() => {
    onDelete(recipe.id);
  }, [onDelete, recipe.id]);

  return (
    <div>
      <h3>{recipe.title}</h3>
      <button onClick={handleClick}>Delete</button>
    </div>
  );
}

```
👉 Позволяет избежать лишних перерендеров дочерних компонентов, если обработчики зависят от статических данных

