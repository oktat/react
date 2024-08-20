# A useState

## A useState használata

A React a 16.8 verziótól bevezette a kampók (Hook) használatát.

Ezek segítségével állapotokat tárolhatunk, mellékhatásokat kezelhetünk, állapotok és funkciók könnyű megosztása komponensek között.

A useState() lehetővé teszi állapotartó változó létrehozását. A változóhoz tartozik egy beállítófüggvény.

## Komponens készítése

src/components/City.jsx:

```jsx
import {useState} from 'react'

function City() {
    const [city, setCity] = useState();
    const updateCity = () => {
        setCity('Miskolc');
    }
    return (
        <div>
            <h1>{city}</h1>
            <button onClick={updateCity}>Másik</button>
        </div>
    )
}

export default City
```

src/App.jsx:

```jsx

import City from './components/City';

function App() {
  
  return (
    <>
      <City />
    </>
  );
}

export default App
```

A useState paramétereként megadható kezdőérték is:

```jsx
const [city, setCity] = useState('Szeged');
```

```jsx
const [salary, setSalary] = useState(0);
```

## Fizetés növelése

src/components/City.jsx:

```jsx
import {useState} from 'react'

function City() {
    const [city, setCity] = useState('Szeged');
    const [salary, setSalary] = useState(300);
    const updateCity = () => {
        setCity('Miskolc');
    }
    const incrementSalary = () => {
        setSalary(salary + 5);
    }
    return (
        <div>
            <h1>{city}</h1>
            <button onClick={updateCity}>Másik</button>
            Fizetés:<div>{salary}</div>
            <button onClick={incrementSalary}>Fizetés emelése</button>
        </div>
    )
}

export default City
```

src/App.jsx:

```jsx
import City from './components/City';

function App() {
  
  return (
    <>
      <City />
    </>
  );
}

export default App
```

## Van-e járműve

src/components/City.jsx:

```jsx
import {useState} from 'react'

function City() {
    const [city, setCity] = useState('Szeged');
    const [salary, setSalary] = useState(300);
    const [hasCar, setHasCar] = useState(false);
    const updateCity = () => {
        setCity('Miskolc');
    }
    const incrementSalary = () => {
        setSalary(salary + 5);
    }
    const toggleHasCar = () => {
        setHasCar(!hasCar);
    }
    return (
        <div>
            <h1>{city}</h1>
            <button onClick={updateCity}>Másik</button>

            Fizetés:<div>{salary}</div>
            <button onClick={incrementSalary}>
                Fizetés emelése
            </button>
            Kocsi:<div>{hasCar ? "Van" : "Nincs"}</div>
            <button onClick={toggleHasCar}>
                Kocsi változtat
            </button>
        </div>
    )
}

export default City
```

## Számláló készítése

src/components/Counter.jsx:

```jsx
import { useState } from 'react'

function Counter() {
    const [count, setCount] = useState(0);

    const increment = () => {
        setCount(count + 1);
    }

    const decrement = () => {
        setCount(count - 1);
    }

    const reset = () => {
        setCount(0);
    }

    return (
        <div>
            <h1>{count}</h1>
            <button onClick={increment}>+</button>
            <button onClick={decrement}>-</button>
            <button onClick={reset}>reset</button>
        </div>
    )
}

export default Counter
```

src/App.jsx:

```jsx
import Counter from './components/Counter';

function App() {
  
  return (
    <>
      <Counter />
    </>
  );
}

export default App
```
