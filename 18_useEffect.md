# A useEffect kampó

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A useEffect-ről

A useEffect() egy React kampó, ami lehetővé teszi olyan kódok futtatását, amelyeknek mellékhatásai lehetnek.

Olyan hívásokra kell gondolni, mint:

* hálózati kérés
* időzítők beállítása
* a DOM közvetlen változtatása
* írás adatbázisba

```javascript
useEffect(() => {
  console.log(count)  
})
```

src/components/Counter.jsx:

```javascript
import { useEffect } from "react"
import { useState } from "react"

function Counter() {
  const [count, setCount] = useState(0)
  useEffect(() => {
    console.log(count)  
  })
  console.log('renderelés')
  
  return (
    <>    
      <h2>Renderelések</h2>
      <button onClick={() => setCount(count + 1)}>Mehet</button>
    </>
  )
}

export default Counter
```

Csak egyszer fut le.

Állítsunk be egy üres tömböt:

```javascript
useEffect(() => {
  console.log(count)  
}, [])
```

Teljes kód:

```javascript
/* eslint-disable react-hooks/exhaustive-deps */
import { useEffect } from "react"
import { useState } from "react"

function Counter() {
  const [count, setCount] = useState(0)
  useEffect(() => {
    console.log(count)  
  }, [])
  console.log('renderelés')
  
  return (
    <>    
      <h2>Renderelések</h2>
      <button onClick={() => setCount(count + 1)}>Mehet</button>
    </>
  )
}

export default Counter
```

Így csak az első megjelenéskor fut le.

Adjuk meg a függőségként a count változót:

```javascript
  useEffect(() => {
    console.log(count)  
  }, [count])
```

A teljes kód:

src/components/Counter.jsx:

```javascript
import { useEffect } from "react"
import { useState } from "react"

function Counter() {
  const [count, setCount] = useState(0)
  useEffect(() => {
    console.log(count)  
  }, [count])
  console.log('renderelés')
  
  return (
    <>    
      <h2>Renderelések</h2>
      <button onClick={() => setCount(count + 1)}>Mehet</button>
    </>
  )
}

export default Counter
```

Lefut megjelenéskor és amikor változik a count értéke.

## Összegzés

```jsx
//Lefut az újrarenderelés után
useEffect(() => {})
```

```jsx
//Csak az első megjelenéskor fut el, azaz csatoláskor (mount)
useEffect(() => {}, [])
```

```jsx
//Az első megjelenéskor (mount) és érték változásakor fut le
useEffect(() => {}, [value])
```
