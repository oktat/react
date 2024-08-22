# Frissítések

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Kiindulóhelyzet

A következő kód 4-gyel kellene növelje a count értékét:

```jsx
const increment = () => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);        
}
```

De csak eggyel növeli, mivel mind a négy esetben a függvény hívás elején volt count értéke fog szerepelni.

A megoldás, függvények használata:

src/component/Counter.jsx:

```jsx
import { useState } from 'react'

function Counter() {
    const [count, setCount] = useState(0);

    const increment = () => {
        setCount(count => count + 1);
        setCount(count => count + 1);
        setCount(count => count + 1);
        setCount(count => count + 1);        
    }

    return (
        <div>
            <h1>{count}</h1>
            <button onClick={increment}>+</button>
        </div>
    )
}

export default Counter
```

## Objektum frissítése

### Elsőre

Objektumok frissíétse esetén ha külön szeretnénk frissíteni, az egyes tagokat:

src/components/Student.jsx:

```jsx
import { useState } from 'react';

function Student() {
    const [student, setStu] = useState({
        name: "Veronika",
        city: "Pécs",
        hasCar: false
    })
    const updateName = (event) => {        
        setStu({...student, name: event.target.value})
    }

    const updateCity = (event) => {
        setStu({...student, city: event.target.value})
    }

    const toggleHasCar = () => {
        setStu({...student, hasCar: !student.hasCar})
    }
    return (
        <div>
            <p>
                {student.name} 
                {student.city} 
                {student.hasCar ? "Van" : "Nincs"}
            </p>
            <p>
                <input type="text" value={student.name} 
                onChange={updateName}/>
                <input type="text" value={student.city} 
                onChange={updateCity}/>
                <input type="checkbox" checked={student.hasCar} 
                onChange={toggleHasCar}/>
            </p>            
        </div>

    )
}

export default Student
```

### Függvénnyel

```jsx
setStu(s => ({...s, name: event.target.value}))
```

A zárójeleket ne hagyuk ki!

src/components/Student.jsx:

```jsx
import { useState } from 'react';

function Student() {
    const [student, setStu] = useState({
        name: "Veronika",
        city: "Pécs",
        hasCar: false
    })
    const updateName = (event) => {        
        setStu(s => ({...s, name: event.target.value}))
    }

    const updateCity = (event) => {
        setStu(s =>({...s, city: event.target.value}))
    }

    const toggleHasCar = () => {
        setStu(s =>({...s, hasCar: !student.hasCar}))
    }
    return (
        <div>
            <p>
                {student.name} 
                {student.city} 
                {student.hasCar ? "Van" : "Nincs"}
            </p>
            <p>
                <input type="text" value={student.name} 
                onChange={updateName}/>
                <input type="text" value={student.city} 
                onChange={updateCity}/>
                <input type="checkbox" checked={student.hasCar} 
                onChange={toggleHasCar}/>
            </p>            
        </div>

    )
}

export default Student
```

## Tömb frissítése

### Tantárgyak

src/components/Subject.jsx:

```jsx
import { useState } from 'react';

function Subject() {
    const [subjects, setSubjects] = useState(
        ["Matematika", "Fizika", "Angol"]);

    function onClickAdd() {
        const subject = document.querySelector("#subject").value;
        setSubjects(s => [...s, subject]);
        document.querySelector("#subject").value = "";
    }
        

    return (
        <div>
            <h1>Tantárgyak</h1>
            <ul>
                {subjects.map((subject, index) => (
                    <li key={index}>{subject}</li>
                ))}
            </ul>
            <input type="text" id="subject" />
            <button onClick={onClickAdd}>Add</button>
        </div>
    )
}

export default Subject
```

### Tantárgy törlése

src/components/Subject.jsx:

```jsx
import { useState } from 'react';

function Subject() {
    const [subjects, setSubjects] = useState(
        ["Matematika", "Fizika", "Angol"]);

    function onClickAdd() {
        const subject = document.querySelector("#subject").value;
        setSubjects(s => [...s, subject]);
        document.querySelector("#subject").value = "";
    }

    function onClickRemove(index) {
        setSubjects(s => s.filter((_, i) => i !== index));
    }
        

    return (
        <div>
            <h1>Tantárgyak</h1>
            <ul>
                {subjects.map((subject, index) => (
                    <li key={index}
                    onClick={ () => onClickRemove(index)}
                    >{subject}</li>
                ))}
            </ul>
            <input type="text" id="subject" />
            <button onClick={onClickAdd}>Add</button>
        </div>
    )
}

export default Subject
```

## Objektumok tömbjének frissítése

### Dolgozók listába

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

### Főkomponens

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

### Törléssel

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
