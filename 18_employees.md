# Dolgozók

## Táblázat egy sora

src/components/EmployeeRow.jsx:

```jsx
/* eslint-disable react/prop-types */

function EmployeeRow(props) {
    return (
        <>
            <tr>
                <td>{props.name}</td>
                <td>{props.city}</td>
                <td>{props.salary}</td>
            </tr>
        </>        
    )
}

export default EmployeeRow
```

## Komponens

src/components/Employee.jsx:

```jsx
import { useState } from 'react';
import EmployeeRow from './EmployeeRow.jsx';

function Employee() {
    const [emps, setEmps] = useState([]);
    const [name, setName] = useState("");
    const [city, setCity] = useState("");
    const [salary, setSalary] = useState(0);
    
    const addEmployee = () => {
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

            <table>
                <thead>
                    <tr>
                        <th>Név</th>
                        <th>Település</th>
                        <th>Fizetés</th>
                    </tr>
                </thead>
                <tbody>
                    {emps.map((emp, index) => 
                    <EmployeeRow 
                        key={index} 
                        name={emp.name} 
                        city={emp.city} 
                        salary={emp.salary} 
                    />)}
                </tbody>
            </table> 
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
