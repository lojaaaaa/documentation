# `Жизненный цикл`
> Все этапы 'жизни' компонентов
> 
> Состоит из трех основых этапов: создание, обновление и удаление


<br>

## 🚩 Классовый подход


<a href="https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/"><img src="./img/1.png" style="width: 700px"></a>

<br>

### 🔴 Монтирование (Создание)

<br>

<details>
<summary>🔹 constructor()</summary>
<br>
👉 При СОЗДАНИИ компонента. В нем обычно инициализируются начальные значения состояния и привязываются обработчики событий   
</details>

<br>

<details>
<summary>🔹 static getDerivedStateFromProps()</summary>
<br>
👉 Перед РЕНДЕРИНГОМ компонента и позволяет обновить состояние на основе новых свойств (props)   
</details>

<br>

<details>
<summary>🔹 render()</summary>
 <br>
👉 Этот метод обязателен и отвечает за возврат JSX, который будет отображен в DOM 
</details>

<br>

<details>
<summary>🔹 componentDidMount()</summary>
   <br>
👉 Сразу после вставки компонента в DOM
 
 <br>
 <br>
  
❗ Здесь можно выполнять запросы к серверу, устанавливать подписки на события и выполнять другие побочные эффекты  
</details>

<br>

### 🔴 Обновление

<br>

<details>
<summary>🔹 static getDerivedStateFromProps()</summary>
<br>
👉 Вызывается при обновлении, чтобы обновить состояние на основе новых свойств 
</details>

<br>

<details>
<summary>🔹 shouldComponentUpdate()</summary>
<br>
👉 Вызывается перед рендерингом компонента и определяет, следует ли перерисовывать компонент   
</details>

<br>

<details>
<summary>🔹 render()</summary>
 <br>
👉 Перерисовывается на основе новых данных
</details>

<br>

<details>
<summary>🔹 getSnapshotBeforeUpdate()</summary>
   <br>
👉 Вызывается перед тем, как обновленный компонент будет вставлен в DOM
</details>

<br>

<details>
<summary>🔹 componentDidUpdate()</summary>
   <br>
👉 После обновления компонента и позволяет выполнять побочные эффекты после перерисовки
</details>

<br>

### 🔴 Размонтирование (Удаление)

<br>

<details>
<summary>🔹 componentWillUnmount()</summary>
<br>
👉 Вызывается перед удалением компонента из DOM

 <br>
 <br>
  
❗ Здесь можно очищать ресурсы, прекращать подписки и выполнять другие завершающие действия
</details>





<br>

## 🚩 Функциональный подход с хуками


<img src="./img/2.jpg" style="width: 900px">
