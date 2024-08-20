# Objektumok frissítése

## Elsőre

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

## Függvénnyel

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
