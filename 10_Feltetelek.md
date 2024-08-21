# Feltételek

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A feltételek használatáról

A feltételek segítségével megszabhatjuk mit rendereljen az alkalmazás. Megjeleníthetünk valamit, eltüntethetünk vagy cserélhetünk valamit.

## Navigációs sáv megjelenítése

src/components/Navbar.jsx:

```jsx
/* eslint-disable react/prop-types */

function Navbar(props) {
  
  if(props.isLoggedIn) {
    return (
      <div>
        <div>Bejelentkezve: {props.username}</div>
      </div>
    )
  }
}

export default Navbar
```

src/App.jsx:

```jsx
import Nav from './components/Navbar';

function App() {
  
  return (
    <>
      <Nav 
        isLoggedIn={true}
        username="imre"
      />
    </>
  );
}

export default App
```

## Ellenben ág

src/components/Navbar.jsx:

```jsx
/* eslint-disable react/prop-types */

function Navbar(props) {
  
  if(props.isLoggedIn) {
    return (
      <div>
        <div>Bejelentkezve: {props.username}</div>
      </div>
    )
  }else {
    return (
      <div>
        <div>Jelentkezz be</div>
      </div>
    )
  }
}

export default Navbar
```

src/App.jsx:

```jsx

import Nav from './components/Navbar';

function App() {
  
  return (
    <>
      <Nav 
        isLoggedIn={false}
        username="imre"
      />
    </>
  );
}

export default App
```

## Kérdőjel operátorral

src/components/Navbar.jsx:

```jsx
/* eslint-disable react/prop-types */

function Navbar(props) {
  
  return(props.isLoggedIn ? 
    <div>Bejelentkezve: {props.username}</div> :
    <div>Jelentkezz be</div>
  )
}

export default Navbar
```

Egyszerűsítve:

src/components/Navbar.jsx:

```jsx
/* eslint-disable react/prop-types */

function Navbar(props) {
  const loggedInDiv = <div>
    Bejelentkezve: {props.username}
    </div>

  const loggedOutDiv = <div>
    Jelentkezz be
    </div>
  
  return(props.isLoggedIn ? 
    loggedInDiv : loggedOutDiv
    
  )
}

export default Navbar
```
