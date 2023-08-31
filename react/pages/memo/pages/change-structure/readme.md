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
        <CarMemo name={name} key={name} />
      ))}
    </div>
  );
  
```
👉 При каждом изменении инпута происходит изменение состояния => перендер всего компонента. 

Однако, состояние инпута не влияет на компонент `CarMemo`, а значит перендер этого компонента не оправдан

<br>


  ## 🚩 Способы исправить без меморизации

<br>

### `Отделение компонентов`

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

<br>


### `children`

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
                {/* 👉🏼 children, внутри InputWrapper, не будет ререндериться при изменении стейта InputWrapper */}
                {/* 👉🏼 Для ререндера children, нужно что-бы произошел ререндер того компонента где children обьявлен как компонент, т.е <App /> */}
                {cars.map((name) => (
                    <Car name={name} key={name}/>
                ))}
            </InputWrapper>
        </div>
    );
}
```


