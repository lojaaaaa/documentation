# `React Router DOM`
> библиотека для навигации и маршрутизации в приложениях React

<br>

## 🚩 Компоненты
<details>
<summary>🔹 BrowserRouter</summary>
    
<br>

```sh
Оборачивает приложение, предоставляя маршрутизацию на стороне клиента
```
</details>

<br>

<details>
<summary>🔹 Route</summary>
    
<br>

```sh
Определяет путь и соответствующий компонент для отображенияа
```
</details>

<br>

<details>
<summary>🔹 Switch | Routes</summary>
    
<br>

```sh
Оборачивает несколько <Route> и отображает только первый, который соответствует текущему URL
```
</details>

<br>

<details>
<summary>🔹 Link</summary>
    
<br>
      
```sh
Создает ссылку на другой маршрут
```
</details>

<br>

<details>
<summary>🔹 NavLink</summary>
    
<br>
      
```sh
Аналог <Link>, но позволяет добавлять стили или классы активности для активного маршрута
```
</details>

<br>

<details>
<summary>👇 Пример использования</summary>

```jsx
import { BrowserRouter, Route, Switch, Link } from 'react-router-dom';

function App() {
    return (
        <BrowserRouter>
            <nav>
                <ul>
                    <li><Link to="/">Home</Link></li>
                    <li><Link to="/about">About</Link></li>
                </ul>
            </nav>
            <Switch>
                <Route path="/" exact component={Home} />
                <Route path="/about" component={About} />
            </Switch>
        </BrowserRouter>
    );
}

```
</details>

<br>

## 🚩 Динамический маршрут

🔴 Определение динамического маршрута:
```jsx
<Route path="/users/:id" component={UserProfile} />
```

<br>

🔴 Извлечение параметров в компоненте:
```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
    const { id } = useParams();

    return <p>User ID: {id}</p>;
}

```
