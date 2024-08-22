# useRef

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A useRef

A useRef kampót akkor használjuk, ha olyan értéket szeretnénk tárolni, ami nincs hatással a megjelenítésre. Információt tárolhatunk a renderelések között.

Mikor használjuk. Például szeretnénk valamit megszámolni, de az eredmény megjeleníteni nem szeretnénk.

## Számláló

src/App.js:

```javascript
import { useRef } from "react"

function App() {
  const ref = useRef(0)

  const handleClick = () => {
    ref.current++
    console.log(ref.current)
  }
  return (
    <>      
      <button onClick={handleClick}>Mehet</button>
    </>
  )
}

export default App
```

## Fókuszba

src/App.jsx:

```javascript
import { useRef } from "react"

function App() {
  const ref = useRef(null)

  const handleClick = () => {
    ref.current.focus()
  }

  console.log('Renderelés')
  return (
    <>
      <input ref={ref} />
      <button onClick={handleClick}>Focus</button>
    </>
  )
}

export default App
```

* [https://react.dev/reference/react/useRef](https://react.dev/reference/react/useRef)
