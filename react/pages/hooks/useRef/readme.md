# `useRef`
> Хук, который используется для создания и управления ссылками на DOM-элементы или для хранения данных

<br>

## 🚩 Синтаксис

```jsx
const ref = useRef(initialValue);
```

`initialValue` - начальное значение ref

<br>

### Важно ❗

В отличие от `useState`, изменение значения `ref` не вызывает перерендеринг компонента

<br>

## 🚩 Примеры

### Привязка к DOM-элементу
```jsx
import React, { useRef } from 'react';

function FocusableInput() {
    const inputRef = useRef(null);

    const focusInput = () => {
        inputRef.current.focus();
    };

    return (
        <div>
            <input ref={inputRef} type="text" />
            <button onClick={focusInput}>Focus Input</button>
        </div>
    );
}


```
<br>

### Сохранение данных между рендерами
```jsx
function MyComponent() {
  const dataRef = useRef(0);

  const incrementData = () => {
    dataRef.current += 1;
    console.log(dataRef.current);
  };

  return (
    <div>
      <p>Значение: {dataRef.current}</p>
      <button onClick={incrementData}>Инкрементировать</button>
    </div>
  );
}


```
<br>

### Хранение предыдущих значений
```jsx
import React, { useEffect, useRef } from 'react';

function MyComponent(props) {
  const prevPropsRef = useRef();

  useEffect(() => {
    prevPropsRef.current = props;
  });

  const prevProps = prevPropsRef.current;

  if (prevProps.someValue !== props.someValue) {
    // Делать что-то при изменении определенного пропса
  }

  // ...
}


```
