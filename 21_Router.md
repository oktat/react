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
* [Útvonalak védelme](#útvonalak-védelme)
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

## Útvonalak védelme

src/App.jsx:

```javascript
import { createBrowserRouter } from 'react-router-dom'
import './App.css'
import Home from './components/Home'
import Login from './components/Login'
import Layout from './components/Layout'
import { RouterProvider } from 'react-router-dom'
import Nopage from './components/Nopage'
import Profile from './components/Profile'
import Logout from './components/Logout'

function App() {

  const router = createBrowserRouter([

    { path: '/', element: <Home /> },
    { path: 'login', element: <Login /> },
    {
      element: <Layout />,
      children: [                
        { path: '/logout', element: <Logout /> },
        { path: '/profile', element: <Profile />  },        
      ]
     },
     { path: '*', element: <Nopage /> }

  ], {basename: '/m/assur'})

  return (
    <>
      <div className="container">
        <RouterProvider router={router} />
      </div>
    </>
  )
}

export default App
```

A routing végén találunk egy ilyen sort:

```javascript
{basename: '/m/assur'}
```

Itt kell megadnunk, ha valamilyen alkönyvtárban lesz elérhető a webhely.

### A védelem és a navigáció

src/components/Layout.jsx:

```javascript
import { Link } from 'react-router-dom'
import { Outlet } from 'react-router-dom'
import { Navigate } from 'react-router-dom';

function Layout() {
  const signedIn = localStorage.getItem('signedIn')
  const username = localStorage.getItem('username')

  return (
    <>
      <nav className="navbar navbar-expand-lg navbar-light bg-light p-1">
        <div className="d-flex justify-content-end">
          Bejelentkezett: {username}
        </div>
        <ul className="nav justify-content-center">
          <li className="nav-item">
            <Link to="/logout" className="nav-link">              
              Kilépés
            </Link>
          </li>
        </ul>
      </nav>

      <main>
      {signedIn ? <Outlet /> : <Navigate to="/login" /> }
      </main>
    </>
  )
}

export default Layout
```

### Főoldal

src/components/Home.jsx:

```javascript
import { Link } from "react-router-dom"

function Home() {
  return (
    <>
      <div className="d-flex justify-content-end">
        <Link to="/login"
        className="btn btn-primary mt-2">Bejelentkezés</Link>
      </div>
      <h1>Informáló</h1>

      <p>
        Dolgozói informáló
      </p>
      <p>
        Egy hozzáférés: eros:titok
      </p>
      <p>
        Egy admin hozzáférés: admin:admin
      </p>
    </>
  )
}

export default Home
```

### Beléptető felület

Egy helyettesítő azonosítást használunk.

src/components/Login.jsx:

```javascript
import { useState } from "react";
import { useNavigate } from "react-router-dom";


function Login() {
  const navigate = useNavigate();
  const [user, setUser] = useState({
    username: '',
    password: ''
  });

  const handleChange = (e) => {
    setUser({ ...user, [e.target.name]: e.target.value });
  }
  
  const handleSubmit = (e) => {
    e.preventDefault();
    if (
      user.username === 'admin' && user.password === 'admin' ||
      user.username === 'eros' && user.password === 'titok'
    ) {      
      localStorage.setItem('signedIn', 'true');
      localStorage.setItem('username', user.username);
      navigate('/profile');  
    }
  }

  return (
    <div>
      <h1>Bejelentkezés</h1>
      
      <form className="loginForm">
        <fieldset className="bg-light p-3 rounded">          
          <div className="input">
            <label htmlFor="username"
            className='form-label'>Felhasználónév</label>
            <input type="text" name="username" id="username"
            className='form-control' 
            onChange={handleChange}
            value={user.username}
            />
          </div>
          <div className="input">
            <label htmlFor="password"
            className='form-label'>Jelszó</label>
            <input type="password" name="password" id="password"
            className='form-control' 
            onChange={handleChange} 
            value={user.password}
            />
          </div>
          
          <button type="submit"
          className='btn btn-primary mt-3'
          onClick={handleSubmit}>Belépés</button>
        </fieldset>
      </form>
      
    </div>
  )
}

export default Login
```

### Profil oldal

src/components/Profile.jsx:

```javascript

function Profile() {
  return (
    <>
    <h1>Profil</h1>
    <p>Név: Erős István</p>
    <p>Település: Szeged</p>
    </>
  )
}

export default Profile
```

### Kijelentkezés

src/components/Logout.jsx:

```javascript
import { Navigate } from "react-router-dom";

function Logout() {
  localStorage.removeItem('signedIn')
  
  return (
    <Navigate to="/login" />
  )
}

export default Logout
```

### A Nopage komponens

src/components/Nopage.jsx:

```javascript

function Nopage() {
  return (
    <>
      <p>
        Nemlétező oldalra tévedtél.
      </p>
    </>
  )
}

export default Nopage
```

### Mintakód és webhelye elérhetősége

GitHub:

* [https://github.com/oktat/assur](https://github.com/oktat/assur)

Élő, működő változat:

* [https://szit.hu/m/assur/](https://szit.hu/m/assur/)

## Lásd

* [https://reactrouter.com/en/main/routers/create-browser-router](https://reactrouter.com/en/main/routers/create-browser-router) (2024)
