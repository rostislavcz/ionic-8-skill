# Floating Action Button

Source: https://ionicframework.com/docs/api/fab

Sections: Basic Usage · List Side · Positioning · Button Sizing · Theming · Accessibility · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Fabs are container elements that contain one or more [fab buttons](https://ionicframework.com/docs/api/fab-button). They should be placed in a fixed position that does not scroll with the content. Fabs should have one main fab button. Fabs can also contain one or more [fab lists](https://ionicframework.com/docs/api/fab-list) which contain related buttons that show when the main fab button is clicked.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-fab>
  <ion-fab-button>
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
</ion-fab>
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add });
  }
}
```

## List Side

The `side` property of the [fab list](https://ionicframework.com/docs/api/fab-list) component controls where it appears relative to the main fab button. A single fab can have multiple fab lists as long as they all have different values for `side`.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-fab slot="fixed" horizontal="center" vertical="center">
  <ion-fab-button>
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
  <ion-fab-list side="top">
    <ion-fab-button>
      <ion-icon name="chevron-up"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
  <ion-fab-list side="end">
    <ion-fab-button>
      <ion-icon name="chevron-forward"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="chevron-forward"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
  <ion-fab-list side="bottom">
    <ion-fab-button>
      <ion-icon name="chevron-down"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
  <ion-fab-list side="start">
    <ion-fab-button>
      <ion-icon name="chevron-back"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="chevron-back"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
</ion-fab>
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonFabList, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add, chevronBack, chevronDown, chevronForward, chevronUp } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonFabList, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add, chevronBack, chevronDown, chevronForward, chevronUp });
  }
}
```

## Positioning

In order to place the fab in a fixed position, it should be assigned to the `fixed` slot of the outer [content](https://ionicframework.com/docs/api/content) component. Use the `vertical` and `horizontal` props to control the alignment of the fab in the viewport. The `edge` prop will cause the fab button to overlap with the app's header or footer.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Fab Buttons</ion-title>
  </ion-toolbar>
</ion-header>
<ion-content class="ion-padding">
  <ion-fab slot="fixed" vertical="top" horizontal="start">
    <ion-fab-button>
      <ion-icon name="chevron-forward-circle"></ion-icon>
    </ion-fab-button>
    <ion-fab-list side="end">
      <ion-fab-button>
        <ion-icon name="document"></ion-icon>
      </ion-fab-button>
      <ion-fab-button>
        <ion-icon name="color-palette"></ion-icon>
      </ion-fab-button>
      <ion-fab-button>
        <ion-icon name="globe"></ion-icon>
      </ion-fab-button>
    </ion-fab-list>
  </ion-fab>

  <ion-fab slot="fixed" vertical="top" horizontal="end" [edge]="true">
    <ion-fab-button>
      <ion-icon name="chevron-down-circle"></ion-icon>
    </ion-fab-button>
    <ion-fab-list side="bottom">
      <ion-fab-button>
        <ion-icon name="document"></ion-icon>
      </ion-fab-button>
      <ion-fab-button>
        <ion-icon name="color-palette"></ion-icon>
      </ion-fab-button>
      <ion-fab-button>
        <ion-icon name="globe"></ion-icon>
      </ion-fab-button>
    </ion-fab-list>
  </ion-fab>

  <ion-fab slot="fixed" vertical="bottom" horizontal="end">
    <ion-fab-button>
      <ion-icon name="chevron-up-circle"></ion-icon>
    </ion-fab-button>
    <ion-fab-list side="top">
      <ion-fab-button>
        <ion-icon name="document"></ion-icon>
      </ion-fab-button>
      <ion-fab-button>
        <ion-icon name="color-palette"></ion-icon>
      </ion-fab-button>
      <ion-fab-button>
        <ion-icon name="globe"></ion-icon>
      </ion-fab-button>
    </ion-fab-list>
  </ion-fab>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import {
  IonContent,
  IonFab,
  IonFabButton,
  IonFabList,
  IonHeader,
  IonIcon,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import {
  chevronDownCircle,
  chevronForwardCircle,
  chevronUpCircle,
  colorPalette,
  document,
  globe,
} from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent, IonFab, IonFabButton, IonFabList, IonHeader, IonIcon, IonTitle, IonToolbar],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ chevronDownCircle, chevronForwardCircle, chevronUpCircle, colorPalette, document, globe });
  }
}
```

### Safe Area

If there is no `ion-header` or `ion-footer` component, the fab may be covered by a device's notch, status bar, or other device UI. In these cases, the [safe area](https://ionicframework.com/docs/theming/advanced#safe-area-padding) on the top and bottom is not taken into account. This can be adjusted by using the [`--ion-safe-area-(dir)` variables](https://ionicframework.com/docs/theming/advanced#application-variables).

When using a fab with `vertical` set to `"top"` without an `ion-header`, the top margin needs to be set:

```css
ion-fab {
  margin-top: var(--ion-safe-area-top, 0);
}
```

And when using a fab with `vertical` set to `"bottom"` without an `ion-footer`, the bottom margin needs to be set:

```css
ion-fab {
  margin-bottom: var(--ion-safe-area-bottom, 0);
}
```

If there is an `ion-header` (for a fab with `vertical` set to `"top"`) or `ion-footer` (for a fab with `vertical` set to `"bottom"`), no CSS adjustment is needed because the fab gets positioned relative to the header or footer.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts
- src/global.css

```html
<ion-fab slot="fixed" vertical="top" horizontal="center">
  <ion-fab-button>
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
</ion-fab>
```

```css
ion-fab {
  margin-top: var(--ion-safe-area-top, 0);
  margin-bottom: var(--ion-safe-area-bottom, 0);
}
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add });
  }
}
```

```css
:root {
  /**
   * Setting the variables for DEMO purposes only.
   * Values will be set automatically when building an iOS or Android app.
   */
  --ion-safe-area-top: 20px;
  --ion-safe-area-bottom: 20px;
}
```

### Relative to Infinite List

In scenarios where a view contains many interactive elements, such as an infinitely-scrolling list, it may be challenging for users to navigate to the Floating Action Button (FAB) if it is placed below all the items in the DOM.

By setting the `fixedSlotPlacement` property on [Content](https://ionicframework.com/docs/api/content) to `before`, the FAB will be placed before the main content in the DOM. This ensures that the FAB receives keyboard focus before other interactive elements receive focus, making it easier for users to access the FAB.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content fixed-slot-placement="before">
  <ion-fab horizontal="end" vertical="bottom" slot="fixed">
    <ion-fab-button>
      <ion-icon name="add"></ion-icon>
    </ion-fab-button>
  </ion-fab>
  <ion-list>
    @for (item of items; track item; let index = $index) {
    <ion-item button>
      <ion-avatar slot="start">
        <img [src]="'https://picsum.photos/80/80?random=' + index" alt="avatar" />
      </ion-avatar>
      <ion-label>{{ item }}</ion-label>
    </ion-item>
    }
  </ion-list>
  <ion-infinite-scroll (ionInfinite)="onIonInfinite($event)">
    <ion-infinite-scroll-content></ion-infinite-scroll-content>
  </ion-infinite-scroll>
</ion-content>
```

```tsx
import { Component, OnInit } from '@angular/core';
import {
  InfiniteScrollCustomEvent,
  IonAvatar,
  IonContent,
  IonFab,
  IonFabButton,
  IonIcon,
  IonInfiniteScroll,
  IonInfiniteScrollContent,
  IonItem,
  IonLabel,
  IonList,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [\
    IonAvatar,\
    IonContent,\
    IonFab,\
    IonFabButton,\
    IonIcon,\
    IonInfiniteScroll,\
    IonInfiniteScrollContent,\
    IonItem,\
    IonLabel,\
    IonList,\
  ],
})
export class ExampleComponent implements OnInit {
  items: string[] = [];

  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add });
  }

  ngOnInit() {
    this.generateItems();
  }

  private generateItems() {
    const count = this.items.length + 1;
    for (let i = 0; i < 50; i++) {
      this.items.push(`Item ${count + i}`);
    }
  }

  onIonInfinite(event: InfiniteScrollCustomEvent) {
    this.generateItems();
    setTimeout(() => {
      event.target.complete();
    }, 500);
  }
}
```

## Button Sizing

Setting the `size` property of the main fab button to `"small"` will render it at a mini size. Note that this property will not have an effect when used with the inner fab buttons.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-fab>
  <ion-fab-button size="small">
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
  <ion-fab-list side="end">
    <ion-fab-button>
      <ion-icon name="document"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="color-palette"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="globe"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
</ion-fab>
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonFabList, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add, colorPalette, document, globe } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonFabList, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add, colorPalette, document, globe });
  }
}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-fab slot="fixed" horizontal="center" vertical="center">
  <ion-fab-button color="secondary">
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
  <ion-fab-list side="top">
    <ion-fab-button color="primary">
      <ion-icon name="chevron-up"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
  <ion-fab-list side="end">
    <ion-fab-button color="tertiary">
      <ion-icon name="chevron-forward"></ion-icon>
    </ion-fab-button>
    <ion-fab-button color="success">
      <ion-icon name="chevron-forward"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
  <ion-fab-list side="bottom">
    <ion-fab-button color="warning">
      <ion-icon name="chevron-down"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
  <ion-fab-list side="start">
    <ion-fab-button color="danger">
      <ion-icon name="chevron-back"></ion-icon>
    </ion-fab-button>
    <ion-fab-button color="dark">
      <ion-icon name="chevron-back"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
</ion-fab>
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonFabList, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add, chevronBack, chevronDown, chevronForward, chevronUp } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonFabList, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add, chevronBack, chevronDown, chevronForward, chevronUp });
  }
}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-fab>
  <ion-fab-button>
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
  <ion-fab-list side="end">
    <ion-fab-button>
      <ion-icon name="document"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="color-palette"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="globe"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
</ion-fab>
```

```css
ion-fab-button {
  --background: #b7f399;
  --background-activated: #87d361;
  --background-hover: #a3e681;
  --border-radius: 15px;
  --box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.3), 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
  --color: black;
}
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonFabList, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add, colorPalette, document, globe } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonFabList, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add, colorPalette, document, globe });
  }
}
```

### CSS Shadow Parts

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-fab>
  <ion-fab-button>
    <ion-icon name="add"></ion-icon>
  </ion-fab-button>
  <ion-fab-list side="end">
    <ion-fab-button>
      <ion-icon name="document"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="color-palette"></ion-icon>
    </ion-fab-button>
    <ion-fab-button>
      <ion-icon name="globe"></ion-icon>
    </ion-fab-button>
  </ion-fab-list>
</ion-fab>
```

```css
ion-fab-button::part(native) {
  background-color: #b7f399;
  border-radius: 15px;
  box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.3), 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
  color: black;
}

ion-fab-button::part(native):hover::after {
  background-color: #a3e681;
}

ion-fab-button::part(native):active::after {
  background-color: #87d361;
}
```

```ts
import { Component } from '@angular/core';
import { IonFab, IonFabButton, IonFabList, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { add, colorPalette, document, globe } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonFab, IonFabButton, IonFabList, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ add, colorPalette, document, globe });
  }
}
```

## Accessibility

### Labels

Since FABs are allowed to contain only icons, developers must provide an `aria-label` on each `ion-fab-button` instance. Without this label, assistive technologies will not be able to announce the purpose of each button.

## Properties

### activated

|     |     |
| --- | --- |
| **Description** | If `true`, both the `ion-fab-button` and all `ion-fab-list` inside `ion-fab` will become active. That means `ion-fab-button` will become a `close` icon and `ion-fab-list` will become visible. |
| **Attribute** | `activated` |
| **Type** | `boolean` |
| **Default** | `false` |

### edge

|     |     |
| --- | --- |
| **Description** | If `true`, the fab will display on the edge of the header if `vertical` is `"top"`, and on the edge of the footer if it is `"bottom"`. Should be used with a `fixed` slot. |
| **Attribute** | `edge` |
| **Type** | `boolean` |
| **Default** | `false` |

### horizontal

|     |     |
| --- | --- |
| **Description** | Where to align the fab horizontally in the viewport. |
| **Attribute** | `horizontal` |
| **Type** | `"center" ｜ "end" ｜ "start" ｜ undefined` |
| **Default** | `undefined` |

### vertical

|     |     |
| --- | --- |
| **Description** | Where to align the fab vertically in the viewport. |
| **Attribute** | `vertical` |
| **Type** | `"bottom" ｜ "center" ｜ "top" ｜ undefined` |
| **Default** | `undefined` |

## Events

No events available for this component.

## Methods

### close

|     |     |
| --- | --- |
| **Description** | Close an active FAB list container. |
| **Signature** | `close() => Promise<void>` |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
