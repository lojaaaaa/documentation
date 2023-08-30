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

## 🚩 Когда лучше использовать

<br>

### 🔴 Кэширование сложных вычислений:
```jsx
const ExpensiveCalculation = () => {
  const data = fetchData(); // Сложная операция получения данных

  const processedData = useMemo(() => {
    // Сложные вычисления на основе data
    return processData(data);
  }, [data]);

  return <div>{processedData}</div>;
};


```
👉 Позволяет избежать повторного выполнения сложных вычислений на каждом рендере, сохраняя результат в `processedData` до тех пор, пока `data` не изменится

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


<br>

### 🔴 Мемоизация результатов вычислений
```jsx
const RecipeCard = ({ recipe }) => {
  const ingredientCount = useMemo(() => {
    return recipe.ingredients.length;
  }, [recipe.ingredients]);

  return (
    <div>
      <h3>{recipe.title}</h3>
      <p>Ingredients: {ingredientCount}</p>
    </div>
  );
}


```
👉 Если есть сложные вычисления, результаты которых используются в компонентах
