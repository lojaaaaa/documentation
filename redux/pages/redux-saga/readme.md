# `Redux-Saga`
> Middleware, которое умеет подписываться на экшены, и выполнять ассинхронные действия, как поэтапно, так и парралельно

<br>

### Важно ❗

`Сага (Saga)` - генераторная функция

<br>

## 🚩 Основа

### ♦️ Вотчеры 
👆🏽 Функции которые вызывают воркер, когда отработал екшен, на который был поставлен вотчер

```typescript
export function* watchClickSaga() { // определяет сагу, которая будет слушать действия с типом 'LOAD_DATA'
  yield takeEvery('LOAD_DATA', workerSage) // и вызывать функцию workerSage при каждом вхождении этого действия
}
```

<br>
<br>

### ♦️ Воркеры   
👆🏽 Могут выполнять ассинхронные запросы, эффекты, диспатчить результаты своей работы в стор

```typescript
export function* workerSage() {
  const planets = yield call(swapiGet, 'planets') // функция swapiGet('planets') возвращает данные 
  yield put({type: 'SET_PLANETS', payload: planets.results}) // диспатч в редюсер
}
```

<br>
<br>

### 💥 Эффекты
👆🏽 Специальные методы саги, которые позволяют вызывать ассинхронные функции как последовательно, так и парралельно (и не только)

<br>
<br>

## 🚩 Методы эффектов

<br>

<details>
<summary>🔹 take</summary>
  
<br>
  
👆 Позволяет `саге` ожидать определенного экшена и приостанавливать выполнение до тех пор, пока это действие не будет диспетчеризовано стор
</details>

<br>

<details>
<summary>🔹 put</summary>
  
<br>

👆 Позволяет осуществлять диспатч

</details>


<br>

<details>
<summary>🔹 call</summary>
  
<br>

👆 Используется для вызова функций (для асинхронных и синхронных вызовов)

</details>

<br>

<details>
<summary>🔹 fork</summary>
  
<br>

👆 Позволяет запустить другую `сагу` параллельно, не блокируя выполнение текущей `саги`

</details>
<br>

<details>
<summary>🔹 takeEvery</summary>
  
<br>

👆 Слушает каждое вхождение определенного действия и запускает `сагу` при каждом вхождении

</details>
