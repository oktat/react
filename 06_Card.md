# Card komponens

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Kártya készítse

Készítsünk egy új projektet.

Az App.jsx fájlt tisztítsuk meg:

```jsx
function App() {
    
}
export default App
```

Az App.css fájl törölhető.

Az src könyvtárban készítsük el a Card.jsx fájlt:

```jsx
function Card() {
  return (
    <div className="card">
      <img src="" alt="Description" />
      <h2>Title</h2>
      <p>Text</p>
    </div>
  );
}
export default Card
```

Importáljuk az App.jsx fájlban:

```jsx
import Card from './Card.jsx'
function App() {
    return (
        <Card />
    )   
}
export default App
```

Működik így is:

```jsx
<Card></Card>
```

Az img elem számára állítson be egy képet.

```jsx
function Card() {
  return (
    <div className="card">
      <img src="https://via.placeholder.com/150" 
      alt="Description" />
      <h2>Title</h2>
      <p>Text</p>
    </div>
  );
}
export default Card
```

Képet beilleszthetünk a következő helyről is:

* [https://picsum.photos/150](https://picsum.photos/150)

Töltsünk le egy képet az src/assets könyvtárba és illesszük be:

```jsx
import kep from "./assets/kep.jpg"

function Card() {
    return (
        <div className="card">
            <img
                src={kep}
                alt="random"
                className="card-image"
            />
            <h2>Title</h2>
            <p>Text</p>
        </div>
    )
}

export default Card
```

Törüljük ki a index.css tartlmát. Készítsünk a kártya számára egy szelektort és néhány beállítást:

```css
.card {
  border: 1px solid rgba(0, 0, 0, 0.3);
  border-radius: 10px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.3);
  width: 300px;
  padding: 20px;
  margin: 20px;
  text-align: center;
  max-width: 250px;
  display: inline-block;
}
```

A kártya képének is állítsunk CSS-t az index.css fájlban:

```css
.card .card-image {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
}
```

A h2 elem számára is állítsunk be CSS-t:

```html
<h2 className="card-title">Title</h2>
```

```css
.card .card-title {
  font-family: sans-serif;  
}
```

A p elem számára is állítsunk be CSS-t:

```html
<p className="card-text">Text</p>
```

```css
.card .card-text {
  font-family: sans-serif;  
}
```

Nézzük meg, hogyan néz ki, ha az App.jsx fájlban megsokszorozzuk a Card komponenst.
