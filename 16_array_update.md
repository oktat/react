# Tömb frissítése

## Tantárgyak

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

## Tantárgy törlése

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
