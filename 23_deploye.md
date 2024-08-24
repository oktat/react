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

## Útválasztás és a deployee

Ha alkönyvtárba telepítsünk ezt meg kell adni az útválasztási beállításoknál.

```javascript
const router = createBrowserRouter([

    { path: '/', element: <Home /> },
    { path: 'login', element: <Login /> },
    {
      element: <Layout />,
      children: [                
        { path: '/logout', element: <Logout /> },
        { path: '/profile', element: <Profile />  },        
      ]
     },
     { path: '*', element: <Nopage /> }

  ], {basename: '/m/assur'})
```
