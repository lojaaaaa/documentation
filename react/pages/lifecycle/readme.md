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
    
❗ Здесь можно выполнять запросы к серверу, устанавливать подписки на события и выполнять другие побочные эффекты  
</details>
