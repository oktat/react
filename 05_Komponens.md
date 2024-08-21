# Kompnens készítése

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Előkészületek

Tisztítsuk meg az app.jsx fájlt:

```jsx
function App() {
    
}
export default App
```

Az App.css fájl törölhető.

Hozzuk létre a Header komponenst. Hozzunk létre egy Header.jsx fájlt, a következő tartalommal:

```jsx
function Header() {
    return (
        <header>
            <h1>My React App</h1>
        </header>
    );
}
export default Header
```

Az App.jsx fájlban importáljuk:

```jsx
import Header from './Header.jsx'
function App() {
    return(
        <Header />
    );
}
export default App
```

Tegyünk a Header komponesbe navigációt.

```jsx
function Header() {
    return (
        <header>
            <h1>My React App</h1>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">About</a></li>
                    <li><a href="#">Services</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
            <hr /><hr />
        </header>
    );
}
export default Header
```

Az src könyvtárban készítsük el a következő Footer komponenst.

```jsx
function Footer() {
    return (
        <footer>
            <p>&copy; 2024 My React App</p>
        </footer>
    );
}
export default Footer
```

Importáljuk az App.jsx fájlban:

```jsx
import Header from './Header.jsx'
import Footer from './Footer.jsx'

function App() {
    return(
        <Header />
        <Footer />
    );
}
export default App
```

Erre hibát kell kapjunk, mivel egyetlen root elemet lehetséges.

```jsx
import Header from './Header.jsx'
import Footer from './Footer.jsx'

function App() {
    return(
        <>
            <Header />
            <Footer />
        </>
    );
}
export default App
```

Egészítsük ki a lábrészkomponenst:

```jsx
function Footer() {
    return (
        <footer>
            <p>
                &copy; {new Date().getFullYear()} 
                2024 My React App
            </p>
        </footer>
    );
}
export default Footer
```

Készítsük el a Emp komponensünket.

```jsx
function Emp() {
    const emp1 = "Béla";
    const emp2 = "Tibor";
    return (
        <ul>
            <li>Lajos</li>
            <li>{emp1}</li>
            <li>{emp2}</li>
        </ul>
    );
}
export default Emp
```

Importáljuk a App.jsx fájlban:

```jsx
import Header from './Header.jsx'
import Footer from './Footer.jsx'
import Emp from './Emp.jsx'

function App() {
    return(
        <>
            <Header />
            <Emp />
            <Footer />
        </>
    );
}
export default App
```

Tegyük nagybetűssé az emp2-t:

```jsx
function Emp() {
    const emp1 = "Béla";
    const emp2 = "Tibor";
    return (
        <ul>
            <li>Lajos</li>
            <li>{emp1}</li>
            <li>{emp2.toUpperCase()}</li>
        </ul>
    );
}
export default Emp
```
