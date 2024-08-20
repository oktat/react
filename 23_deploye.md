# Deploye

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
