# `never`
> Значение или состояние, которое никогда не может произойти

<br>

### 🚩 Когда происходит

  <details>
   <summary>🔹 При обработке ошибок:</summary>
    
  <br>
      
  ```typescript
  function throwError(message: string): never {
    throw new Error(message);
  }
  
  const errorMessage = "Something went wrong!";
  throwError(errorMessage); // Вызовет ошибку и завершит выполнение

  ```
  </details>

  <br>

  <details>
   <summary>🔹 Бесконечный цикл или условие с постоянным false:</summary>
    
  <br>
      
  ```typescript
function infiniteLoop(): never {
    while (true) {
        // Бесконечный цикл
    }
}

  ```
  </details>

<br>

### 🚩 Конкретные примеры


<details>
<summary>🔹 Исключение пропсов</summary>
    
<br>
      
```typescript
export interface StringProps {
    string: string;
    number?: never;
    icon?: never;
}

export interface IconProps {
    icon: ReactElement;
    number?: never;
    string?: never;
}

export interface NumberProps {
    number: number;
    string?: never;
    icon?: never;
}

export type BadgeProps = StringProps | IconProps | NumberProps;

const Badge: FC<BadgeProps> = (props) => {
    return <div {...props}>test</div>;
};

export const TestComponent = () => {
    return (
        <div>
            <Badge number={5} string={"ABC"} />
        </div>
    );
};

```

<br>

❗ Паттерн, когда один компонент может принимать разные наборы пропсов в зависимости от контекста. 

Использование типов "never" в определении интерфейсов помогает контролировать, какие типы пропсов могут быть использованы в каждом случае

</details>

