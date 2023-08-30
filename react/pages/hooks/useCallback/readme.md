# `useCallback`
> Хук, который используется для кэширования стабильных версий функций, чтобы избежать ненужных пересозданий функций при каждом рендере компонента

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

### 🔴 Оптимизация зависимостей useEffect:
```jsx
const UserProfile = ({ userId }) => {
  const [user, setUser] = useState(null);

  const fetchUser = useCallback(async () => {
    const response = await fetch(`/api/user/${userId}`);
    const data = await response.json();
    setUser(data);
  }, [userId]);

  useEffect(() => {
    fetchUser();
  }, [fetchUser]); // Мемоизированный колбэк как зависимость

  if (!user) {
    return <p>Loading...</p>;
  }

  return (
    <div>
      <h2>{user.name}</h2>
      <p>Email: {user.email}</p>
    </div>
  );
};



```
👉 Позволяет создать стабильный fetchUser, который можно использовать в зависимостях useEffect, обеспечивая стабильность в наблюдении за изменениями fetchUser
