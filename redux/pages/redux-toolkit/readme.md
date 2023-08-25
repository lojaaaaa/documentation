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
//rootReducer.js
import {combineReducers} from "@reduxjs/toolkit";
import todoReducer from './todoSlice';

const rootReducer = combineReducers({
  todos: todoReducer,
})

export default rootReducer
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


### 🔵 Пример Слайса

```jsx
// todoSlice.js

const todoSlice = createSlice({
    name: 'todos',
    initialState: {
        todos: [],
    },
    reducers: {
        addTodo(state, action) {
            state.todos.push(action.payload);
        },
        removeTodo(state, action) {
            state.todos = state.todos.filter(todo => todo.id !== action.payload.id);
        }
    },

});

```

<br>
