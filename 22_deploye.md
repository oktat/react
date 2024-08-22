# Deploye

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## Build

```cmd
npm run build
```

## Telepítés alkönyvtárba

vite.config.js:

```js
export default defineConfig({
  plugins: [react()],
  base: '/valami/',
})
```

```cmd
npm run build
```

A build után az index.html fájlban a megadott útvonalon szerepelnek a CSS és JavaScript fájlok.
