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

`useMemo` Может кэшировать не только значения, но и компоненты

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

### 🔴 Оптимизация дорогостоящих рендеров:
```jsx
const UserList = ({ users }) => {
  const sortedUsers = useMemo(() => {
    return users.sort((a, b) => a.name.localeCompare(b.name));
  }, [users]);

  return (
    <ul>
      {sortedUsers.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};


```
👉 Сортировка `users` производится только при изменении зависимости `users`, что позволяет избежать частых дорогостоящих операций сортировки


<br>

### 🔴 Кэширование результатов API-запросов
```jsx
const UserProfile = ({ userId }) => {
  const user = useMemo(() => {
    return fetchUser(userId); // Запрос данных пользователя
  }, [userId]);

  return <div>{user.name}</div>;
};



```
👉 Запрос на получение данных пользователя будет выполнен только при изменении `userId`


<br>

### 🔴 Оптимизация контекстов:
```jsx
const MyComponent = () => {
  const contextValue = useContext(MyContext);

  const processedValue = useMemo(() => {
    return expensiveProcessing(contextValue);
  }, [contextValue]);

  return <div>{processedValue}</div>;
};

```
👉 Позволяет избежать повторных вычислений, когда значение из контекста остается неизменным

<br>
<br>

# `memo`
> (HOC), который принимает компонент и возвращает новый компонент, мемоизированный по пропсам

<br>

### Важно ❗

Если компонент обернут в `React.memo`, он будет перерисовываться только при изменении его пропсов, а не при каждом рендере родительского компонента

<br>
