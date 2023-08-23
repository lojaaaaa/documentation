# `Redux-Saga`
> Middleware, которое умеет подписываться на экшены, и выполнять ассинхронные действия, как поэтапно, так и парралельно

<br>

## 🚩 Основа

### Вотчеры 
👆🏽 Функции которые вызывают воркер, когда отработал екшен на который был поставлен вотчер

```typescript
export function* watchClickSaga() {
  yield takeEvery('LOAD_DATA', workerSage)
}
```

<br>
<br>

### Воркеры   
👆🏽 Могут выполнять ассинхронные запросы, эффекты, диспатчить результаты своей работы в стор

```typescript
export function* workerSage() {
  const planets = yield call(swapiGet, 'planets')
  yield put({type: 'SET_PLANETS', payload: planets.results})
}
```

<br>
<br>

### Эффекты
👆🏽 Специальные методы саги, которые позволяют вызывать ассинхронные функции как последовательно, так и парралельно (и не только)

<br>
<br>
