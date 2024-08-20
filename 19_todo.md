# Todo megvalósítása

## A Todo komponens

src/components/Todo.jsx:

```jsx
import { useState } from "react";
import './Todo.css';

function Todo() {
    const [tasks, setTasks] = useState([]);
    const [newTask, setNewTask] = useState("");

    function addTask() {
        if(newTask.trim() !== "") {
            setTasks([...tasks, newTask]);
            setNewTask("");
        }
    }
    function deleteTask(index) {
        const updatedTasks =tasks.filter((task, i) => i !== index);
        setTasks(updatedTasks);
    }
    function moveTaskUp(index) {
        if(index > 0) {
            const updatedTasks = [...tasks];
            const [removedTask] = updatedTasks.splice(index, 1);
            updatedTasks.splice(index - 1, 0, removedTask);
            setTasks(updatedTasks);
        }
    }
    function moveTaskDown(index) {
        if(index < tasks.length - 1) {
            const updatedTasks = [...tasks];
            const [removedTask] = updatedTasks.splice(index, 1);
            updatedTasks.splice(index + 1, 0, removedTask);
            setTasks(updatedTasks);
        }
    }

    return (
        <div>
            <h1>Tennivaló</h1>
            <input
                className="todo-input"
                type="text"
                value={newTask}
                placeholder="tennivaló"
                onChange={(e) => setNewTask(e.target.value)}
            />
            <button onClick={addTask}
            className="add-button">Hozzáadása</button>
            <ul>
                {tasks.map((task, index) => (
                    <li key={index}>
                        
                        <span className="task-text">{task}</span>

                        <button onClick={() => deleteTask(index)}
                        className="delete-button"                    
                        >🗑</button>
                        <button onClick={() => moveTaskUp(index)}
                        className="move-button">↑</button>
                        <button onClick={() => moveTaskDown(index)}
                        className="move-button">↓</button>
                    </li>
                ))}
            </ul>
        </div>
    )
}

export default Todo
```

## Főkomponens

src/App.jsx:

```jsx
import Todo from "./Todo";

function App() {

  return (
    <>
      <div className="container">
        <Todo />
      </div>
      
    </>
  )
}

export default App
```

src/index.css:

```css
body {
  margin: 0;
}

.container {
  background-color: burlywood;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: top;
  font-size: calc(10px + 2vmin);
  color: black;
  
}
```

src/Todo.css:

```css
h1 {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 3rem;
    margin: 3rem 0;
    text-align: center;
    color: #333;
}

button {
    font-size: 1rem;
    padding: 0.1rem;
    border-radius: 3px;
}

.add-button {
    background-color: green;
    color: white;
    padding: 0.5rem;
    border-color: green;
}

.todo-input {
    font-size: 1.1rem;
    padding: 0.5rem;
    border-radius: 3px;
    border: 1px solid #ccc;
    margin: 1.2rem 1rem;
    min-width: 15rem;
    

}

.task-text {
    font-size: 1.1rem;
    min-width: 15rem;
    display: inline-block;
}

.delete-button {
    background-color:orange;
    color: black;
    margin: 0.1rem;
    padding: 0.2rem;
    border-color: rgb(218, 142, 2);
}

ul {
    list-style: none;
    padding: 0;
    margin: 0;
    
}

li {
    background-color: white;
    border: 0;
    border-radius: 3px;
    margin: 0.5rem;
    padding: 0.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.move-button {
    background-color:burlywood;
    border-color: rgb(176, 145, 105);
    font-size: 1.5rem;
}
```

## Élő minta

* [https://szit.hu/m/react_todo/](https://szit.hu/m/react_todo/)
