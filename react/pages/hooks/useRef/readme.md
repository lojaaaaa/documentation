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

## 🚩 Пример
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
