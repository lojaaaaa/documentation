# `Кастомные хуки`

<br>

## 🚩 `useInput`
```jsx
//useInput.js
import { useState } from "react";

export default function useInput (initialValue) {

  const [value, setValue] = useState(initialValue)

  const onChange = (e) =>{
    setValue(e.target.value)
  }

  return {value, onChange}
}

//App.jsx
function App() {
  
  const name = useInput('')

  return (
    <div>
      <input {...name} type="text" placeholder="name"/>
      <button onClick={() => console.log(name.value)}>tap</button>
    </div>
  )
}

```
👉 Хук для получения значения инпута


https://usehooks.com/
