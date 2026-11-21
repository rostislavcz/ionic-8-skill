# Ionic Icon Component

Source: https://ionicframework.com/docs/api/icon

Icon is a simple component made available through the [Ionicons](https://ionic.io/ionicons) library, which comes pre-packaged by default with all Ionic Framework applications. It can be used to display any icon from the Ionicons set, or a custom SVG. It also has support for styling such as size and color.

For a list of all available icons, see [ionic.io/ionicons](https://ionic.io/ionicons). For more information including styling and custom SVG usage, see [the Usage page](https://ionic.io/ionicons/usage).

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-icon name="logo-ionic"></ion-icon>
<ion-icon name="logo-ionic" size="large"></ion-icon>
<ion-icon name="logo-ionic" color="primary"></ion-icon>
<ion-icon name="logo-ionic" size="large" color="primary"></ion-icon>
```

```ts
import { Component } from '@angular/core';
import { IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { logoIonic } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ logoIonic });
  }
}
```

## Accessibility

Icons that are purely decorative content should have `aria-hidden="true"`. This will not visually hide the icon, but it will hide the element from assistive technology.

```html
<ion-icon name="heart" aria-hidden="true"></ion-icon>
```

If the icon is interactive, it should have alternate text defined by adding an `aria-label`.

```html
<ion-icon name="heart" aria-label="Favorite"></ion-icon>
```

Alternatively, if the icon is inside of another element that it is describing, that element should have the `aria-label` added to it, and the icon should be hidden using `aria-hidden`.

```html
<ion-button aria-label="Favorite">
  <ion-icon name="heart" aria-hidden="true"></ion-icon>
</ion-button>
```
