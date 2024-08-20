# A useEffect kampó

## A useEffect-ről

A useEffect() egy React kampó, ami azt mondja csinálj valamit, amikor:

* A komponens újra renderelődik.
* A komponens csatolva lesz.
* Egy state értéket kap.

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

Mikor használjuk a useEffect() kampót?

* API hívások
* Időzített műveleteknél
* Eseményfigyelés
* DOM manipuláció
* Külső könyvtárak használata

## Írás a böngésző címsorába

src/App.jsx:

```jsx
import { useEffect } from 'react';
import { useState } from 'react'

function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count ${count}`;
  }, [count]);

  function addCount() {
    setCount(c => c + 1);
  }
  return (
    <>
      <p>count: {count}</p>

      <button onClick={addCount}>Növel</button>
    </>
  )
}

export default App
```

## Két változóval

src/App.jsx:

```jsx
import { useEffect } from 'react';
import { useState } from 'react'

function App() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('Irén');

  useEffect(() => {
    document.title = `Count ${count} - ${name}`;
  }, [count]);

  function addCount() {
    setCount(c => c + 1);
  }
  function substractCount() {
    setCount(c => c - 1);
  }
  function changeName() {
    setName(n => n === "Irén" ? "Pisti" : "Irén");
  }
  return (
    <>
      <p>count: {count}</p>
      <p>name: {name}</p>

      <button onClick={addCount}>Növel</button>
      <button onClick={substractCount}>Csökkent</button>
      <button onClick={changeName}>Vált</button>
    </>
  )
}

export default App

```

Nézzük meg a kód ezen részét:

```jsx
useEffect(() => {
document.title = `Count ${count} - ${name}`;
}, [count]);
```

Mivel a name nincs a függőségek között, az nem látszik változás esetén sem.
