# Képek

* **Szerző:** Sallai András
* Copyright (c) 2024, Sallai András
* Licenc: [CC Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)
* Web: [https://szit.hu](https://szit.hu)

## A képek helye

Képeket két helyre tehejtük:

* `./src/assets` - Dinamikusan importált képek
* `./public` - Statikusan használt képek

A `./src/assets` könyvtárban elhelyett képek a build folyamat során feldolgozásra kerülnek.

## Statikus képek

```html
<img src="/image.png" alt="Description" />
```

## Dinamikus képek

```javascript
import image from './assets/image.png';

function MyComponent() {
  return <img src={image} alt="Description" />;
}
```
