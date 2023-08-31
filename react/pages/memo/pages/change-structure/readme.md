  # `Как обойтись без меморизации?`

<br>

### Почему нельзя всегда использовать ❓

Неправильное или избыточное применение мемоизации может даже привести к ухудшению производительности вместо улучшения

<br>


## 🚩 Без меморизации

Исходный код
```js
const [input, setInput] = useState("");

  return (
    <div className="App">
      <input value={input} onChange={(e) => setInput(e.target.value)} />
      {cars.map((name) => (
        <CarMemo name={name} key={name} />
      ))}
    </div>
  );
  
```

### Отделение компонентов

```jsx

return (
    <div className="App">
        <Input /> {// Изменение стейта инпута происходит внутри, не заставляя перередндривать Car при каждом изменении
        {cars.map((name) => (
            <Car name={name} key={name} />
        ))}
    </div>
);


```
👉 Компонент `User` обернут в `React.memo`, и он будет перерисовываться только тогда, когда пропсы пользователя (`user`) действительно изменились

<details>
<summary>Подробнее 📗</summary>
  
<br>

❗ Без использования `memo`, при каждом обновлении родительского компонента `UserList` все компоненты `User` бы перерисовывались, даже если пропсы не изменились

</details>

<br>

## 🚩 Схема для использования `memo`

<br>

<img src="../../img/1.png" style="width: 700px">

<a href="./pages/change-structure/readme.md">❓ Как можно изменить структуру</a>
