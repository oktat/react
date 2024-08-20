# Ismétlés

## Beosztások megjelenítése

src/components/Positions.jsx:

```jsx
function Positions () {
    const positions = [
        "front-end fejlesztő",
        "back-end fejlesztő",
        "full-stack fejlesztő",
        "tesztelő"
    ]

    return (positions)
}

export default Positions
```

src/App.jsx:

```jsx
import Positions from './components/Positions';

function App() {
  
  return (
    <>
      <Positions />
    </>
  );
}

export default App
```

## Listába renderelés

src/components/Positions.jsx:

```jsx
function Positions () {
    const positions = [
        "front-end fejlesztő",
        "back-end fejlesztő",
        "full-stack fejlesztő",
        "tesztelő"
    ]
    // eslint-disable-next-line react/jsx-key
    const listItems = positions.map((position) => <li>{position}</li>)
    return (listItems)
}

export default Positions
```

src/components/Positions.jsx:

```jsx
/* eslint-disable react/jsx-key */
function Positions () {
    const positions = [
        "front-end fejlesztő",
        "back-end fejlesztő",
        "full-stack fejlesztő",
        "tesztelő"
    ]
    const listItems = positions.map((position) => <li>{position}</li>)
    return (listItems)
}

export default Positions
```

## Rendezve

src/components/Positions.jsx:

```jsx
/* eslint-disable react/jsx-key */
function Positions () {
    const positions = [
        "front-end fejlesztő",
        "back-end fejlesztő",
        "full-stack fejlesztő",
        "tesztelő"
    ]
    positions.sort()
    const listItems = positions.map((position) => <li>{position}</li>)
    return (listItems)
}

export default Positions
```

## Kulcs beállítása

src/compoents/Postions.jsx:

```jsx
function Positions () {
    const positions = [
        "front-end fejlesztő",
        "back-end fejlesztő",
        "full-stack fejlesztő",
        "tesztelő"
    ]

    const listItems = positions.map((position) => 
        <li key={position}>{position}</li>
    )
    return (listItems)
}

export default Positions
```

Az index használataával:

src/components/Positions.jsx:

```jsx
function Positions () {
    const positions = [
        "front-end fejlesztő",
        "back-end fejlesztő",
        "full-stack fejlesztő",
        "tesztelő"
    ]

    const listItems = positions.map((position, index) => 
        <li key={index}>{position}</li>
    )
    return (listItems)
}

export default Positions
```

## Objektumként tárolva

src/components/Positions.jsx:

```jsx
function Positions () {
    const positions = [
        {id: 1, name: "front-end fejlesztő"},
        {id: 2, name: "back-end fejlesztő"},
        {id: 3, name: "full-stack fejlesztő"},
        {id: 4, name: "tesztelő"}
    ]

    const listItems = positions.map((pos) => 
        <li key={pos.id}>{pos.name}</li>
    )
    return (<ul>{listItems}</ul>)
}

export default Positions
```

Ha listát nem gyermekelemként adjuk át, vagyis kihagyjuk az ul elemet, akkor a következő hibát kaphatjuk:

```txt
 Objects are not valid as a React child (found: object with keys {listItems}). If you meant to render a collection of children, use an array instead.
```

## Rendezés

src/components/Employees.jsx:

```jsx

function Employees() {
    const employees = [
        {id: 1, name: "Szendrei Albert", city: "Budapest", salary: 392, hasCar: false},
        {id: 2, name: "Bástya Irén", city: "Debrecen", salary: 380, hasCar: true},
        {id: 3, name: "Masa Béla", city: "Budapest", salary: 400, hasCar: false},
        {id: 4, name: "Lórinc Zsolt", city: "Debrecen", salary: 397, hasCar: true},
    ]

    //Rendezés név alapján
    employees.sort((a, b) => a.name.localeCompare(b.name))
    //Fordított rendezése
    employees.sort((a, b) => b.name.localeCompare(a.name))
    //Fizetés szerint rendezve
    employees.sort((a, b) => b.salary - a.salary)
    //Fizetés szerint rendezve fordítva
    employees.sort((a, b) => b.salary - a.salary)

    const listItems = employees.map((emp) => 
        <li key={emp.id}>{emp.name} {emp.city} {emp.salary}</li>
    )
    return (<ul>{listItems}</ul>)
}

export default Employees
```

A rendezések közül, természetesen egyet kell meghagyni.

## Szűrés

src/commponents/Employees.jsx:

```jsx

function Employees() {
    const employees = [
        {id: 1, name: "Szendrei Albert", city: "Budapest", salary: 392, hasCar: false},
        {id: 2, name: "Bástya Irén", city: "Debrecen", salary: 380, hasCar: true},
        {id: 3, name: "Masa Béla", city: "Budapest", salary: 400, hasCar: false},
        {id: 4, name: "Lórinc Zsolt", city: "Debrecen", salary: 397, hasCar: true},
    ]

    const hasCarEmployees = employees.filter((emp) => emp.hasCar)

    const listItems = hasCarEmployees.map((emp) => 
        <li key={emp.id}>{emp.name} {emp.city} {emp.salary}</li>
    )
    return (<ul>{listItems}</ul>)
}

export default Employees
```

Összehasonlító operátrokat is használhatunk:

```jsx
const hasCarEmployees = employees.filter((emp) => emp.salary > 390)
```

## A dolgozók az App oldalról

src/App.jsx:

```jsx
import Employees from './components/Employees';

function App() {
  const employees = [
    {id: 1, name: "Szendrei Albert", city: "Budapest", salary: 392, hasCar: false},
    {id: 2, name: "Bástya Irén", city: "Debrecen", salary: 380, hasCar: true},
    {id: 3, name: "Masa Béla", city: "Budapest", salary: 400, hasCar: false},
    {id: 4, name: "Lórinc Zsolt", city: "Debrecen", salary: 397, hasCar: true},
]
  
  return (
    <>
    
      <Employees items={employees}/>
    </>
  );
}

export default App
```

src/components/Employees.jsx:

```jsx
/* eslint-disable react/prop-types */

function Employees(props) {
    const employees = props.items;

    const listItems = employees.map((emp) => 
        <li key={emp.id}>{emp.name} {emp.city} {emp.salary}</li>
    )
    return (<ul>{listItems}</ul>)
}

export default Employees
```
