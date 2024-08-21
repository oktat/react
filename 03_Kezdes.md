# A Vite és a React

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Projekt létrehozása

```bash
npm create vite@latest
```

A futtatás lehetséges eredménye:

```bash
$ npm create vite@latest
✔ Project name: … app01
✔ Select a framework: › React
✔ Select a variant: › JavaScript

Scaffolding project in /home/andras/app01...

Done. Now run:

  cd app01
  npm install
  npm run dev
```

Telepítenünk kell a függőségeket:

```bash
npm install
```

Ha van pnpm parancsunk, használjuk azt:

```bash
pnpm install
```

Fejlesztői szerver futtatása:

```bash
npm run dev
```

Alapértelmezetten az 5173-s porton indul el a fejlesztői szerver.

Az alkalmazás belépésiponja main.jsx, ami egyetlen komponenst tartalmaz, amelynek neve: App, amit az App.jsx fájlban találunk.

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

Az App.jsx fájl már egyszerűbb:

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <div>
        <a href="https://vitejs.dev" target="_blank">
          <img src={viteLogo} className="logo" alt="Vite logo" />
        </a>
        <a href="https://react.dev" target="_blank">
          <img src={reactLogo} className="logo react" alt="React logo" />
        </a>
      </div>
      <h1>Vite + React</h1>
      <div className="card">
        <button onClick={() => setCount((count) => count + 1)}>
          count is {count}
        </button>
        <p>
          Edit <code>src/App.jsx</code> and save to test HMR
        </p>
      </div>
      <p className="read-the-docs">
        Click on the Vite and React logos to learn more
      </p>
    </>
  )
}

export default App
```

## Képek helye

Képeket két helyre szokás elhelyezni:

* `./src/assets` - Dinamikusan importált képek
* `./public` - Statikusan használt képek
