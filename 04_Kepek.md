# Képek

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
