# Card komponens

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
                className="card__image"
            />
            <h2>Title</h2>
            <p>Text</p>
        </div>
    )
}

export default Card
```
