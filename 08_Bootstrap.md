# Bootstrap

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Telepítés

```bash
pnpm install bootstrap
```

## Használatbavétel

src/index.css:

```css
@import 'bootstrap';
```

## Példa

```javascript
<button className="btn btn-primary">Mehet</button>
```

src/App.js

```javascript
import './App.css'

function App() {
  return (
    <>
      <div className="container">
        <h1>Helló</h1>
        <button className="btn btn-primary">Mehet</button>
      </div>
    </>
  )
}

export default App
```
