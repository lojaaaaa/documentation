# `never`
> Значение или состояние, которое никогда не может произойти

<br>

### Когда происходит

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
