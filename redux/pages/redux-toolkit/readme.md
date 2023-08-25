# `Redux Toolkit`
> Надстройка над редакс, позволяющая экономить время и кол-во написанного кода

<br>

## 🚩 Использование

<br>

### 🔵 Создание хранилища

```jsx
// store.js
import { configureStore } from '@reduxjs/toolkit';
import rootReducer from './rootReducer';

export default configureStore({
  reducer: rootReducer,
});

```

<br>


### 🔵 Объединение редюсеров

```jsx
//rootReducer
import {combineReducers} from "@reduxjs/toolkit";
import todoReducer from './todoSlice';

const rootReducer = combineReducers({
  todos: todoReducer,
})

export default rootReducer
```

<br>

### 🔵 Пример простого редюсера

```jsx
// cashReducer.js

const defaultState = {  // состояние по умолчанию
  cash: 6
}

export const cashReducer = (state = defaultState, action) =>{
  switch(action.type){ // обработка действий
    case 'ADD_CASH':
      return {...state, cash: state.cash + action.payload} // изменение состояния
    case 'GET_CASH':
      return {...state, cash: state.cash - action.payload}
    default:
      return state
  }
}

```

<br>

### 🔵 Оболочка для приложения

```jsx
// index.js

import { Provider } from 'react-redux';
import store from './store';
import App from './App';

ReactDOM.render( // объект store будет доступен во всех дочерних компонентах 
  <Provider store={store}>  
    <App />
  </Provider>,
  document.getElementById('root')
);

```

<br>

### 🔵 Хуки `useDispatch` и `useSelector`

<br>

👉 `useDispatch` - отправка действия для обновления состояния

```jsx
const dispatch = useDispatch();
const handleAddTodo = () => {
    dispatch({type: {действие}, payload: {данные}));
  };

```

<br>

👉 `useSelector` - получение нужных данных из общего состояния

```jsx
const todos = useSelector(state => state.todos);
// или
const otherData = useSelector(state => state.otherData);

```


<br>
<br>

# `Redux Thunk`
> middleware для управления асинхронными действиями

<br>


## Важно ❗


`Middleware` - это слой, через который проходят действия перед тем, как они достигнут редюсера

Он позволяет добавлять дополнительную логику и функциональность, такую как асинхронные операции, логирование или изменение данных, без изменения самих редюсеров

<br>

👇 Пример функции для получения пользователей:

```jsx
import { ADD_MANY_CUSTOMERS} from "../store/customerReducer"

export const fetchUsers = () =>{
  return function(dispatch){
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(json => dispatch({type: ADD_MANY_CUSTOMERS, payload: json}))
  }
}
```

