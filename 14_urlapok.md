# Űrlapok használata

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Az onChange eseményről

Az onChange esemény, elsősorban űrlapoknál használjuk. Olyan elemeknél mint input, textarea, select stb.

Az esemény akkor következzik be, amikor megváltozik az elem értéke.

## Név bekérése

src/components/Name.jsx:

```jsx
import React from 'react'

function Name() {
    const [name, setName] = React.useState("Senki");
    function onChangeName(e) {
        setName(e.target.value)
    }
    return (
        <div>
            <h1>Üdv {name}</h1>
            <input 
                type="text" 
                
                onChange={onChangeName} 
                />
            
        </div>
    )
}

export default Name
```

Hogy legyen az input mező értéke a kezdeti name érték, szúrjuk be:

```jsx
value={name} 
```

src/component/Name.jsx:

```jsx
import React from 'react'

function Name() {
    const [name, setName] = React.useState("Senki");
    function onChangeName(e) {
        setName(e.target.value)
    }
    return (
        <div>
            <h1>Üdv {name}</h1>
            <input 
                type="text" 
                value={name} 
                onChange={onChangeName} 
                />
            
        </div>
    )
}

export default Name
```

## Háromszög területe

src/components/Triangle.jsx:

```jsx
import { useState } from 'react';

function Triangle() {
    const [base, setBase] = useState(0);
    const [height, setHeight] = useState(0);
    const [area, setArea] = useState(0);
    
    const calculateArea = () => {
        setArea(base * height / 2);
    }

    return (
        <div>
            <div className="input">
                <label>Alap</label>
                <input type="number" value={base} onChange={(e) => setBase(e.target.value)} />
            </div>

            <div className="input">
                <label>Magasság</label>
                <input type="number" value={height} onChange={(e) => setHeight(e.target.value)} />
            </div>
            <div>
    
                <button onClick={calculateArea}>Szerkesztés</button>
            </div>

            {area}
        </div>
    )
}

export default Triangle
```

src/App.jsx:

```jsx

import Triangle from './components/Triangle';

function App() {
  
  return (
    <>
      <Triangle />
    </>
  );
}

export default App
```

## A select használata

src/components/Vehicle.jsx:

```jsx
import { useState } from 'react';

function Vehicle() {   
    const [brand, setBrand] = useState('');
    function onChangeBrand(e) {
        setBrand(e.target.value)
    }
    return (
        <div>
            <h1>Márka {brand}</h1>
            <select value={brand} onChange={(e) => onChangeBrand(e)}>
                <option value="">---</option>
                <option value="Mercedes">Mercedes</option>
                <option value="Opel">Opel</option>
                <option value="BMW">BMW</option>
                <option value="Audi">Audi</option>
            </select>
        </div>
    )    
}

export default Vehicle
```

src/App.jsx:

```jsx

import Vehicle from './components/Vehicle';

function App() {
  
  return (
    <>
      <Vehicle />
    </>
  );
}

export default App
```

## Rádiógombok használata

```jsx
<div>
    <input type="radio" 
    name="used" 
    id="used" 
    value="használt" 
    checked={used === 'használt'} 
    onChange={onChangeUsed}/>
    <label htmlFor="used">használt</label>
</div>    
<div>    
    <input type="radio" 
    name="used" 
    id="new" 
    value="új" 
    checked={used === 'új'} 
    onChange={onChangeUsed}/>
    <label htmlFor="new">új</label>    
</div>
```

A teljes kód:

src/components/Vehicle.jsx:

```jsx
import { useState } from 'react';

function Vehicle() {   
    const [brand, setBrand] = useState('');
    const [used, setUsed] = useState('');

    function onChangeBrand(e) {
        setBrand(e.target.value)
    }

    function onChangeUsed(e) {
        setUsed(e.target.value)
    }
    return (
        <div>
            <h1>Kocsi {used} {brand}</h1>
            <select value={brand} onChange={(e) => onChangeBrand(e)}>
                <option value="">---</option>
                <option value="Mercedes">Mercedes</option>
                <option value="Opel">Opel</option>
                <option value="BMW">BMW</option>
                <option value="Audi">Audi</option>
            </select>

            
            <div>
                <input type="radio" 
                name="used" 
                id="used" 
                value="használt" 
                checked={used === 'használt'} 
                onChange={onChangeUsed}/>
                <label htmlFor="used">használt</label>
            </div>    
            <div>    
                <input type="radio" 
                name="used" 
                id="new" 
                value="új" 
                checked={used === 'új'} 
                onChange={onChangeUsed}/>
                <label htmlFor="new">új</label>    
            </div>
        </div>
    )    
}

export default Vehicle
```

## Gyakorlat 1

* Gyakorlásként kérjünk be mennyiséget
* Gyakorlásként kérjünk be megjegyzést, textarea használatával.
* Gyakorlásként kérjünk be fizetési módot select használatával.
* Készítsünk egy színválasztó komponenst.
