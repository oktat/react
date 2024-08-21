# Bootstrap

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Beállítás

Importálni kell a path változót és szükségünk van egy __dirname állandóra:

```javascript
import path from 'path'
const __dirname = path.resolve()
```

A Bootstrap beállítása:

```javascript
  resolve: {
    alias: {
      'bootstrap': path.resolve(__dirname, './node_modules/bootstrap'),
    },
  },
```

vite.config.js:

```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

import path from 'path'
const __dirname = path.resolve()

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      'bootstrap': path.resolve(__dirname, './node_modules/bootstrap'),
    },
  },
})

```

## Használat

src/index.css:

```css
@import 'bootstrap';
```
