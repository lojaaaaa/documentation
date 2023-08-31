  # `Как обойтись без меморизации?`

<br>

### Почему нельзя всегда использовать ❓

Неправильное или избыточное применение мемоизации может привести к ухудшению производительности вместо улучшения

<br>
<br>

## Исходный код 👇
```jsx
const [input, setInput] = useState("");

  return (
    <div className="App">
      <input value={input} onChange={(e) => setInput(e.target.value)} />
      {cars.map((name) => (
        <Car name={name} key={name} />
      ))}
    </div>
  );
  
```
👉 При каждом изменении инпута происходит изменение состояния => перендер всего компонента. Однако, состояние инпута не влияет на компонент `Car`, а значит перендер этого компонента не оправдан

❗ Для решения этой проблемы можно обернуть `Car` в `memo` или:

<br>
<br>


  ## 🚩 Без меморизации

### 🔴&emsp;`Отделение компонентов`

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
👉 Выносим всю работу со стейтом и изменением инпута в отдельный компонент. Благодаря этому при изменении инпута будет происходить лишь ререндер `Input`

<br>


### 🔴&emsp;`children`

```jsx
const [input, setInput] = useState("");

const InputWrapper = ({children}) => {
    const [input, setInput] = useState("");

    return (
        <div className="App">
            <input value={input} onChange={(e) => setInput(e.target.value)} />
            {children}
        </div>
    );
}

export default function App() {
    return (
        <div className="App">
            <InputWrapper>
                {// children, внутри InputWrapper, не будет ререндериться при изменении стейта InputWrapper */}
                {// Для ререндера children, нужно чтобы произошел ререндер того компонента, где children обьявлен как компонент
                {cars.map((name) => (
                    <Car name={name} key={name}/>
                ))}
            </InputWrapper>
        </div>
    );
}
```
👉 Создаем оболочку, в которой изменяем состояние и передаем через `children` список машин. Тем самым будет происходить лишь ререндер инпута внутри оболочки

