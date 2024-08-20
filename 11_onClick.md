# onClick esemény

## Az onClick

Ha felhasználó kattint az egérrel, visszahívással (callback) reagálunk az eseményre.

## Az esemény kezelése

src/components/Button.jsx:

```jsx

function Button() {
    const onClickHandle = () => {
        console.log('Helló');
    }
    return (
        <button 
        onClick={onClickHandle}
        >
            Mehet
        </button>
    );
}

export default Button
```

src/App.jsx:

```jsx
import Button from './components/Button';

function App() {
  
  return (
    <>
      <Button />
    </>
  );
}

export default App
```

## Paraméter átadással

src/components/Button.jsx:

```jsx

Ha paraméter is át kell adni a hívásnál, akkor az onClickHandle helyett onClickHandle()-t írunk és ebbe még a jön a paraméter is:

function Button() {
    const onClickHandle = (name) => {
        console.log('Helló', name);
    }
    return (
        <button onClick={ () => onClickHandle('Imre')}>
            Mehet
        </button>
    );
}

export default Button
```

Ebben az esetben az onClick számára egy névtelen függvényt adunk át, amiben meghívjuk az onClickHandle() függvényünket.

## Számláló

src/components/Button.jsx:

```jsx
function Button() {
    let counter = 0;
    const onClickHandle = (name) => {
        counter++;
        console.log('Helló', name, counter);
    }
    return (
        <button onClick={ () => onClickHandle('Imre')}>
            Mehet
        </button>
    );
}

export default Button
```

## Információ az esményről

src/components/Button.jsx:

```jsx
function Button() {
    const onClickHandle = (e) => {
        console.log(e);
    }
    return (
        <button onClick={(e) => onClickHandle(e)}>
            Mehet
        </button>
    );
}

export default Button

```

Nézzük meg a böngészőben, milyen információkat ír egy bekövetkezett eseményről.

src/commponents/Button.jsx:

```jsx
function Button() {
    const onClickHandle = (e) => {
        //Az esemény kiváltó elem szövegének módosítása
        e.target.textContent = 'Kattintottam'
        
    }
    return (
        <button onClick={(e) => onClickHandle(e)}>
            Mehet
        </button>
    );
}

export default Button
```

## onDoubleClick

src/components/Button.tsx:

```tsx
function Button() {
    const onDoubleClickHandle = () => {
        console.log('Helló');
    }
    return (
        <button onDoubleClick={() => onDoubleClickHandle()}>
            Mehet
        </button>
    );
}

export default Button
```

## Más HTML elem kattintása

src/components/Box.jsx:

```jsx
function Box() {
    const style = {
        backgroundColor: 'red',
        width: '100px',
        height: '100px',
    }

    const onClickHandle = () => {
        console.log('doboz')
    }
    return (
        <div className="box" style={style}
        onClick={onClickHandle}>
            doboz
        </div>
    )
}

export default Box
```

A kattintás forrásának kezelése:

src/components/Box.jsx:

```jsx
function Box() {
    const style = {
        backgroundColor: 'red',
        width: '100px',
        height: '100px',
    }

    const onClickHandle = (e) => {
        e.target.style.backgroundColor = 'blue';
        console.log('doboz')
    }
    return (
        <div className="box" style={style}
        onClick={(e) => onClickHandle(e)}>
            doboz
        </div>
    )
}

export default Box
```
