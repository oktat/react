# Frissítő függvények

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
