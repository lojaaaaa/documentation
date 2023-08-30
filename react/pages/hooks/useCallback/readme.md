# `useCallback`
> Хук, который используется для кэширования результатов вычислительных функций, чтобы избежать повторных вычислений в случаях, когда входные данные не изменились

<br>

## 🚩 Синтаксис
```jsx
const memoizedCallback = useCallback(callbackFunction, dependenciesArray);
```
`callbackFunction ` - функция, которую надо мемоизировать

`dependenciesArray ` - массив зависимостей


<br>


## 🚩 Когда лучше использовать

<br>

### 🔴 Передача колбэков в дочерние компоненты:
```jsx
const ParentComponent = () => {
  const handleButtonClick = useCallback(() => { // ф-ия не будет перендериваться при кажому ререндере родителя
    // Обработка клика
  }, []); // Нет зависимостей, так как функция стабильна

  return (
    <ChildComponent onClick={handleButtonClick} />
  );
};

const ChildComponent = ({ onClick }) => {
  return (
    <button onClick={onClick}>Click Me</button>
  );
};


```
👉 Колбэк-функция `handleButtonClick` не будет пересоздаваться при каждом рендере `ParentComponent`

<br>

### 🔴 Мемоизация обработчиков событий:
```jsx
const Counter = () => {
  const [count, setCount] = useState(0);

  const handleIncrement = useCallback(() => {
    setCount(prevCount => prevCount + 1);
  }, []);

  const handleDecrement = useCallback(() => {
    setCount(prevCount => prevCount - 1);
  }, []);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  );
};



```
👉 Позволяет сохранить стабильные версии обработчиков событий `handleIncrement` и `handleDecrement`, избегая ненужных пересозданий при каждом рендере


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
