# A useEffect kampó

## A useEffect-ről

A useEffect() egy React kampó, ami azt mondja csinálj valamit, amikor:

* A komponens újra renderelődik.
* A komponens csatolva lesz.
* Egy state értéket kap.

```jsx
//Lefut az újrarenderelés után
useEffect(() => {})
```

```jsx
//Csak az első megjelenéskor fut el, azaz csatoláskor (mount)
useEffect(() => {}, [])
```

```jsx
//Csatoláskor és érték változásakor fut le
useEffect(() => {}, [value])
```

Mikor használjuk a useEffect() kampót?

* API hívások
* Időzített műveleteknél
* Eseményfigyelés
* DOM manipuláció
* Külső könyvtárak használata
