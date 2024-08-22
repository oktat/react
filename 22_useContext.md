# useContext

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A useContext

A useContext segítségével adatokat adhatunk át a többszinten lévő komponensek számára.

A useContext nélkül, a komponensek láncolásán keresztül valósítjuk meg az ilyen feladatokat. Az egyik komponens átadja a következőnek, az megint a következőnek, és így tovább. Így hosszú láncok jönnek létre, am megnehezíti a kodbázis karbantartását. Az ilyen láncolást a komponensek fúrásának szokás nevezni. A kontextus használatával ez elkerülehtő.

## Név terjesztése

Készítsünk három komponenst:

* src/components/CompA.jsx
* src/components/CompB.jsx
* src/components/CompC.jsx

Tegyük az CompA komponenst az App kompnensbe.

src/App.jsx:

```javascript
import CompA from './components/CompA'

function App() {
  return (
    <>    
      <CompA />
    </>
  )
}

export default App
```

src/components/CompA.jsx:

```javascript
import { useState, createContext } from 'react'
import CompB from './CompB'

export const CompAContext = createContext()

function CompA() {
    const [name] = useState("Béla")
  return (
    <div className="comp">
        <h2>A</h2>
        <p>{name}</p>
        <CompAContext.Provider value={name}>
            <CompB />
        </CompAContext.Provider>
        
    </div>
  )
}

export default CompA
```

src/components/CompB.jsx:

```javascript

import CompC from './CompC'

function CompB() {
  return (
    <div className="comp">
        <h2>B</h2>        
        <CompC />
    </div>
  )
}

export default CompB
```

src/components/CompC.jsx:

```javascript
import { useContext } from 'react'

import { CompAContext } from './CompA'

function CompC() {
  const name = useContext(CompAContext)
  return (
    <div className="comp">
        <h2>C</h2>
        <p>{name}</p>
    </div>
  )
}

export default CompC
```

## Navigációs sáv

Készítsünk egy projektet. Készítsünk egy components nevű könyvtárat, benne három komponenst:

* src/components/Main.jsx
* src/components/Nav.jsx
* src/components/Login.jsx

src/components/Main.jsx:

```javascript
import { Context } from "../App"
import { useContext } from "react"

function Main() {
    const [signedIn] = useContext(Context)
  return (
    <div>
        <h1>Főoldal</h1>
        <p>{signedIn ? "Bejelentkezve" : "Kijelentkezve"}</p>
    </div>
  )
}

export default Main
```

src/components/Nav.jsx:

```javascript
import Login from "./Login";

export default function Nav() {
  return (
    <div className="nav">
        <Login />   
    </div>
  )
}
```

src/components/Login.jsx:

```javascript
import { Context } from "../App"
import { useContext } from "react"

function Login() {
    const [signedIn, setSignedIn] = useContext(Context)
    function auth() {
        setSignedIn(!signedIn)
    }
  return (
    <button onClick={auth}>
        {signedIn ? "Kijelentkezés" : "Bejelentkezés"}
    </button>
  )
}

export default Login
```

src/App.jsx:

```javascript

import './App.css'
import Main from './components/Main'
import Nav from './components/Nav'

import React, { useState } from 'react'

export const Context = React.createContext()

function App() {
  const [signedIn, setSignedIn] = useState(false)
  return (
    <Context.Provider value={[signedIn, setSignedIn]}>
      <Nav />
      <Main />
    </Context.Provider>
  )
}

export default App
```
