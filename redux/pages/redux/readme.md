# `Redux`
> Библиотека для управлением состоянием

<br>

## 🚩 Наглядная разница

<br>

<img src="./img/1.svg" style="width: 500px">

<br>

## 🚩 Как работает?

<br>

<img src="./img/1.png" style="width: 500px">

<br>

`Dispatch` - Процесс передачи действия редюсеру

`Action` - Объекты, которые описывают, что произошло в приложении.  

&emsp;&emsp;❗ Обязательно должны иметь свойство `type`

`Reducer` - Функция, которая принимает текущее состояние и действие, и возвращает новое состояние. 

`Store` - Объект, который содержит все данные

`View` - Само приложение, в котором так или иначе можно вызывать `dispatch`

<br>

## 🚩 Использование

<br>

### Создание хранилища

```jsx
// store.js
import { legacy_createStore as createStore } from 'redux';
import rootReducer from './reducers';

export const store = createStore(rootReducer, composeWithDevTools);
```
