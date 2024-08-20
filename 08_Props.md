# A props

## A props-ról

A props egy csak olvasható tulajdonság, amivel adatokat tudunk megosztani a komponensek számára. A szülő komponens adatokat küldhet a gyermekkomponensnek.

Szintaxis:

```jsx
<Component key=value />
```

## Props példa

### Props típusellenőrzés nélkül

Ha ESlint-t használunk, az megköveteli a típusellenőrzést a props objektumon keresztülérkező adatok esetén. A következő példában egy megjegyéssel lebeszéljük róla.

src/components/Employee.jsx:

```jsx
/* eslint-disable react/prop-types */

function Employee(props) {
    return (
        <>
            <div>
                
                <h3>{props.name}</h3>
                <p>{props.city}</p>
            </div>
        </>
    )
}

export default Employee
```

src/App.jsx:

```jsx
import Employee from './components/Employee';

function App() {
  
  return (
    <>
      <Employee 
        name="Erős István" 
        city="Szeged"
        />

    </>
  );
}

export default App
```

### Props típusellenőrzéssel

Készítsünk egy Employee komponenst.

src/components/Employee.jsx:

```jsx
import PropTypes from 'prop-types';

function Employee(props) {
    return (
        <>
            <div>
                <h3>{props.name}</h3>
                <p>{props.city}</p>
            </div>
        </>
    )
}

Employee.propTypes = {
    name: PropTypes.string,
    city: PropTypes.string
}

export default Employee
```

src/App.jsx

```jsx
import Employee from './components/Employee';

function App() {
  
  return (
    <>
      <Employee 
        name="Erős István" 
        city="Szeged"
        />

    </>
  );
}

export default App
```

### Megoldás interface-szel

Ez a megoldás csak TypeScript-tel használható:

src/components/Employee.jsx:

```tsx
interface EmployeeProps {
    name: string;
    city: string;
}

function Employee(props: EmployeeProps) {
    return (
        <>
            <div>
                <h3>{props.name}</h3>
                <p>{props.city}</p>
            </div>
        </>
    )
}

export default Employee
```

### A props logikai típussal

src/components/Employee.jsx:

```jsx
/* eslint-disable react/prop-types */

function Employee(props) {
    return (
        <>
            <div>                
                <h3>{props.name}</h3>
                <p>{props.city}</p>
                <p>{props.salary}</p>
                <p>{props.hasCar ? "Igen" : "Nem"}</p>
            </div>
        </>
    )
}

export default Employee
```

src/App.jsx

```jsx
import Employee from './components/Employee';

function App() {
  
  return (
    <>
      <Employee 
        name="Erős István" 
        city="Szeged"
        salary={345}
        hasCar={true}
        />

    </>
  );
}

export default App
```

### Típusellenőrzéssel

Telepítsük a prop-types csomagot:

```cmd
pnpm i prop-types
```

src/components/Employee.jsx:

```jsx
import PropTypes from 'prop-types';

function Employee(props) {
    return (
        <>
            <div>                
                <h3>{props.name}</h3>
                <p>{props.city}</p>
                <p>{props.salary}</p>
                <p>{props.hasCar ? "Igen" : "Nem"}</p>
            </div>
        </>
    )
}

Employee.propTypes = {
    name: PropTypes.string,
    city: PropTypes.string,
    salary: PropTypes.number,
    hasCar: PropTypes.bool
}

export default Employee
```

### Alapértelmezett érték

```jsx
Employee.defaultProps = {
    name: "Nincs nev",
    city: "Nincs varos",
    salary: 0,
    hasCar: false
}
```

A teljes kód:

src/components/Employee.jsx:

```jsx
import PropTypes from 'prop-types';

function Employee(props) {
    return (
        <>
            <div>                
                <h3>{props.name}</h3>
                <p>{props.city}</p>
                <p>{props.salary}</p>
                <p>{props.hasCar ? "Igen" : "Nem"}</p>
            </div>
        </>
    )
}

Employee.propTypes = {
    name: PropTypes.string,
    city: PropTypes.string,
    salary: PropTypes.number,
    hasCar: PropTypes.bool
}

Employee.defaultProps = {
    name: "Nincs nev",
    city: "Nincs varos",
    salary: 0,
    hasCar: false
}

export default Employee

```
