# Stílus hozzáadása

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A stílusok hozzáadása

Három módon rendelhetünk CSS-t az alkalmazásunkhoz:

* external - külső
* inline - soron belül
* modulok használata

## Külső stílus hozzáadása

src/Button.jsx:

```javascript
function Button() {
    return (<button 
    className="button" />)
}

export default Button
```

Használjuk a gombot.

src/App.jsx:

```javascript
import Button from "./Button";
function App() {
    return (<Button />);
}

export default App
```

Az index.css fájlban állítsuk be a stílust a gomb számára.

src/index.css:

```css
.button {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 5px;
}
```

## Inline stílus

src/App.js:

```javascript
const heading = {
  fontSize: "64px",
  color: "blue",
  fontFamily: "sans-serif",
}

function App() {
  return (
    <>
      <h1 style={heading}>Turizmus</h1>
    </>
  );
}

export default App
```

A stílus elhelyezhető az osztályon belül is:

```javascript

function App() {
  const heading = {
    fontSize: "64px",
    color: "blue",
    fontFamily: "sans-serif",
  }  
  return (
    <>
      <h1 style={heading}>Turizmus</h1>
    </>
  );
}

export default App
```

## Modul használata

src/components/header.module.css:

```css
.header {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100px;
    background-color: #333;
    color: #fff;
}
```

src/components/header.jsx:

```javascript
import styles from "./header.module.css";

function Header() {
    return (
        <header className={styles.header}>
            <h1>Turizmus</h1>
        </header>
    )
}
export default Header
```

src/App.jsx:

```javascript
import Header from "./components/header";

function App() {
  return (
    <>
      <Header />
    </>
  );
}

export default App
```
