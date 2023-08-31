  # `Как обойтись без меморизации?`

<br>

### Почему нельзя всегда использовать ❓

Неправильное или избыточное применение мемоизации может даже привести к ухудшению производительности вместо улучшения

<br>


## 🚩 Без меморизации

```jsx
import React from 'react';

const User = ({ user }) => {
  console.log(`User ${user.name} рендерится`);
  return (
    <div>
      <h3>{user.name}</h3>
      <p>Email: {user.email}</p>
    </div>
  );
};

const MemoizedUser = React.memo(User);

const UserList = ({ users }) => {
  return (
    <div>
      {users.map(user => (
        <MemoizedUser key={user.id} user={user} />
      ))}
    </div>
  );
};

export default UserList;



```
👉 Компонент `User` обернут в `React.memo`, и он будет перерисовываться только тогда, когда пропсы пользователя (`user`) действительно изменились

<details>
<summary>Подробнее 📗</summary>
  
<br>

❗ Без использования `memo`, при каждом обновлении родительского компонента `UserList` все компоненты `User` бы перерисовывались, даже если пропсы не изменились

</details>

<br>

## 🚩 Схема для использования `memo`

<br>

<img src="../../img/1.png" style="width: 700px">

<a href="./pages/change-structure/readme.md">❓ Как можно изменить структуру</a>