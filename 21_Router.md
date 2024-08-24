# Útválasztás

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Tartalomjegyzék

* [Tartalomjegyzék](#tartalomjegyzék)
* [Szükséges csomagok](#szükséges-csomagok)
* [Útválasztás megvalósítása](#útválasztás-megvalósítása)
* [Lapok](#lapok)
* [A Layout komponens](#a-layout-komponens)
* [Hibaoldal](#hibaoldal)
* [Lásd](#lásd)

## Szükséges csomagok

* react-router-dom
  
```bash
pnpm install react-router-dom
```

## Útválasztás megvalósítása

src/App.jsx:

```jsx
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

## Lapok

src/pages/Home.jsx:

```jsx

function Home() {
  return (
    <div>Home</div>
  )
}

export default Home
```

src/pages/Solution.jsx:

```jsx
function Solution() {
  return (
    <div>Solution</div>
  )
}

export default Solution
```

src/pages/About.jsx:

```jsx

function About() {
  return (
    <div>About</div>
  )
}

export default About
```

## A Layout komponens

src/components/Layout.jsx:

```javascript
import { Outlet } from 'react-router-dom'

function Layout() {
  return (
    <>
      <nav>
        <ul>
          <li>
            <a href="/">Főoldal</a>
          </li>
          <li>
            <a href="/about">Névjegy</a>
          </li>
          <li>
            <a href="/solution">Megoldás</a>
          </li>
        </ul>
      </nav>

      <main>
        <Outlet />
      </main>
    </>
  )
}

export default Layout
```

## Hibaoldal

```jsx
{
  path: '*',
  element: <Nopage />,
},
```

Teljeskód:

src/App.jsx:

```jsx
import { createBrowserRouter } from 'react-router-dom'
import About from './pages/About'
import Home from './pages/Home'
import Layout from './pages/Layout'
import { RouterProvider } from 'react-router-dom'
import Solution from './pages/Solution'
import Nopage from './pages/Nopage'

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
        {
          path: '*',
          element: <Nopage />,
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

## Lásd

* [https://reactrouter.com/en/main/routers/create-browser-router](https://reactrouter.com/en/main/routers/create-browser-router) (2024)
