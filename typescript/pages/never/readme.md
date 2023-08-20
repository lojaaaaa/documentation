# `Never`
> Значение или состояние, которое никогда не может произойти

<br>

## 🚩 Когда происходит

<br>

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

## 🚩 Паттерны

<br>

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
            <Badge number={5} string={"ABC"} /> // Здесь будет ошибка, поскольку в качестве пропса может быть передано лишь что-то одно
        </div>
    );
};

```

<br>

❗ Паттерн, когда один компонент может принимать разные наборы пропсов в зависимости от контекста. 

Использование типов "never" в определении интерфейсов помогает контролировать, какие типы пропсов могут быть использованы в каждом случае

</details>

<br>

<details>
<summary>🔹 Обработка 'невозможного' кейса</summary>
    
<br>
      
```typescript
type CarBrand = 'lada' | 'bmw' | 'toyta'

interface CarBase {
    year: number,
    brand: CarBrand
}

interface BMW extends CarBase {
    brand: 'bmw',
    climatControl: boolean
}

interface LADA extends CarBase {
    brand: 'lada',
    climatControl: boolean
}

interface TOYTA extends CarBase {
    brand: 'toyta',
    climatControl: boolean
}

type Car = LADA | BMW | TOYTA




function exhaustiveCheck (car: never){
    console.log('Необходимо обработать это значение:', car)
}

function withCar (car: Car) {
    switch(car.brand){
        case 'bmw':
            //do smt
            break

        case 'lada':
            //do smt
            break

        default:
            exhaustiveCheck(car) // Здесь будет ошибка, поскольку в car будет находится type TOYTA, а не never
            break
    }
}


```

<br>

❗ Паттерн, который демонстрирует практику обработки всех возможных вариантов в объединении типов с помощью "exhaustive type checking".

Такой подход помогает обнаружить и избежать ошибок в коде, связанных с упущенными случаями в обработке типов.

</details>
