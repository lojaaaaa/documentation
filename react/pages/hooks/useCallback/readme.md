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
👉 Если данные из Redux редко изменяются и передаются в компонент через пропсы, мемоизация этих пропсов помогает избежать ненужных ререндеров

<br>

### 🔴 Мемоизация функций внутри map или filter
```jsx
const RecipeList = ({ recipes }) => {
  const filteredRecipes = useMemo(() => {
    return recipes.filter(recipe => recipe.isFavorite);
  }, [recipes]);

  return (
    <ul>
      {filteredRecipes.map(recipe => (
        <li key={recipe.id}>{recipe.title}</li>
      ))}
    </ul>
  );
};


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
