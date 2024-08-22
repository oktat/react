# Útválasztás

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Szükséges csomagok

* react-router-dom
  
```bash
pnpm install react-router-dom
```

## Lapok

Készítsünk egy pages nevű könyvtárat az src könyvtáron belül.

* src/pages/Home.jsx
* src/pages/Solution.jsx
* src/pages/About.jsx

## Útválasztás beállítása

```javascript
import { Route } from "react-router-dom"
import { Routes } from "react-router-dom"
import { BrowserRouter } from "react-router-dom"
import Home from "./pages/Home"
import Solutions from "./pages/Solutions"
import About from "./pages/About"
import { Link } from "react-router-dom"

function App() {

  return (

    <BrowserRouter>
      <nav>
          <ul>
              <li>
                  <Link to='/'>Home</Link>
              </li>
              <li>
                  <Link to='/solution'>Solutions</Link>
              </li>
              <li>
                  <Link to='/about'>About</Link>
              </li>
          </ul>
      </nav>
      <Routes>        
        <Route path='/' element={<Home />} />
        <Route path='/solution' element={<Solutions />} />
        <Route path='/about' element={<About />} />
      </Routes>
    </BrowserRouter>

  )
}

export default App
```

## Másik megoldás

src/App.js:

```javascript
import { 
  createBrowserRouter, 
  createRoutesFromElements, 
  Route 
} from 'react-router-dom'
import About from './pages/About'
import Home from './pages/Home'
import Layout from './pages/Layout'
import { RouterProvider } from 'react-router-dom'
import Solution from './pages/Solution'

function App() {

  const router = createBrowserRouter(
    createRoutesFromElements(
      <Route path="/" element={<Layout />}>
        <Route index element={<Home />} />
        <Route path="about" element={<About />} />
        <Route path="solution" element={<Solution />} />
      </Route>
    )
  )

  return (
    <>
      <RouterProvider router={router} />
    </>
  )
}

export default App
```

src/pages/Layout.jsx:

```javascript
import { Outlet } from "react-router-dom"
import { Link } from "react-router-dom"

function Layout() {
  return (
    <>
      <nav>
        <ul>
          <li>
            <Link to="/">Főoldal</Link>
          </li>
          <li>
            <Link to="/solution">Megoldás</Link>
          </li>
          <li>
            <Link to="/about">Névjegy</Link>
          </li>
        </ul>
      </nav>
      <Outlet />
    </>
  )
}

export default Layout
```

### Kreállók lapjai

src/pages/Home.jsx:

```javascript

function Home() {
  return (
    <div>Home</div>
  )
}

export default Home
```

src/pages/Solution.jsx:

```javascript
function Solution() {
  return (
    <div>Solution</div>
  )
}

export default Solution
```

src/pages/About.jsx:

```javascript

function About() {
  return (
    <div>About</div>
  )
}

export default About
```

## Legújabb React Router

src/App.jsx:

```javascript
import { createBrowserRouter } from 'react-router-dom'
import About from './pages/About'
import Home from './pages/Home'
import Layout from './pages/Layout'
import { RouterProvider } from 'react-router-dom'
import Solution from './pages/Solution'

function App() {

  const router = createBrowserRouter([
    {
      path: '/',
      element: <Layout />,
      children: [
        {
          index: true,
          element: <Home />,
        },
        {
          path: 'about',
          element: <About />,
        },
        {
          path: 'solution',
          element: <Solution />,
        },
      ],
    },
  ])

  return (
    <>
      <RouterProvider router={router} />
    </>
  )
}

export default App
```

A weblapok megegyeznek az előző fejezetben megadotakkal.

Lásd:

* [https://reactrouter.com/en/main/routers/create-browser-router](https://reactrouter.com/en/main/routers/create-browser-router) (2024)
