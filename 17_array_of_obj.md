# Objektumok tömbjének frissítése

## Dolgozók listába

src/components/Employee.jsx:

```jsx
import { useState } from "react";

function Employee() {
    const [emps, setEmps] = useState([]);
    const [name, setName] = useState("");
    const [city, setCity] = useState("");
    const [salary, setSalary] = useState(0);
    
    function addEmployee() {
        setEmps([...emps, {
            name: name,
            city: city,
            salary: salary
        }])
    }
    return (
        <>
            <h1>Dolgozók</h1>
            <input type="text" value={name}
            onChange={e => setName(e.target.value)} />
            <br />
            <input type="text" value={city}
            onChange={e => setCity(e.target.value)} />
            <br />
            <input type="number" value={salary}
            onChange={e => setSalary(e.target.value)} />
            <br />
            <button onClick={addEmployee}>
                Hozzáadás
            </button>

            <ul>
                {emps.map((emp, index) => (
                    <li key={index}>
                        {emp.name} {emp.city} {emp.salary}
                    </li>
                ))}
            </ul>
        </>
    )
    
}

export default Employee
```

## Főkomponens

src/App.jsx:

```jsx

import Employee from './components/Employee';

function App() {
  
  return (
    <>
      <Employee />
    </>
  );
}

export default App
```

## Törléssel

Törlőfüggvény:

```jsx
    function removeEmployee(index) {
        const newEmps = [...emps];
        newEmps.splice(index, 1);
        setEmps(newEmps);
    }
```

src/components/Employee.jsx:

```jsx
import { useState } from "react";

function Employee() {
    const [emps, setEmps] = useState([]);
    const [name, setName] = useState("");
    const [city, setCity] = useState("");
    const [salary, setSalary] = useState(0);
    
    function addEmployee() {
        setEmps([...emps, {
            name: name,
            city: city,
            salary: salary
        }])
    }
    function removeEmployee(index) {
        const newEmps = [...emps];
        newEmps.splice(index, 1);
        setEmps(newEmps);
    }
    return (
        <>
            <h1>Dolgozók</h1>
            <input type="text" value={name}
            onChange={e => setName(e.target.value)} />
            <br />
            <input type="text" value={city}
            onChange={e => setCity(e.target.value)} />
            <br />
            <input type="number" value={salary}
            onChange={e => setSalary(e.target.value)} />
            <br />
            <button onClick={addEmployee}>
                Hozzáadás
            </button>

            <ul>
                {emps.map((emp, index) => (
                    <li key={index}
                    onClick={() => removeEmployee(index)}
                    >
                        {emp.name} {emp.city} {emp.salary}
                    </li>
                ))}
            </ul>
        </>
    )
    
}

export default Employee
```

A törlést megoldhatjuk így is:

```jsx
setEmps(emps.filter((element, index) => i !== index))
```

Rövidítve:

```jsx
setEmps(emps.filter((_, i) => i !== index))
```

Az element lett egy "_" karakter, az index pedig egy "i" betű.
