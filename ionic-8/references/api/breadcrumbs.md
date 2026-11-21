# Ionic Breadcrumbs Guide

Source: https://ionicframework.com/docs/api/breadcrumbs

Sections: Basic Usage · Using Icons · Collapsing Items · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Breadcrumbs are navigation items that are used to indicate where a user is on an app or site. They should be used for large sites and apps with hierarchically arranged pages. Breadcrumbs can be collapsed based on the maximum number that can show, and the collapsed indicator can be clicked on to present a popover with more information or expand the collapsed breadcrumbs.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-breadcrumbs>
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs],
})
export class ExampleComponent {}
```

## Using Icons

### Icons on Items

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-label>Icons at Start</ion-label>
<ion-breadcrumbs>
  <ion-breadcrumb href="#home">
    <ion-icon slot="start" name="home"></ion-icon>
    Home
  </ion-breadcrumb>
  <ion-breadcrumb href="#electronics">
    <ion-icon slot="start" name="flash"></ion-icon>
    Electronics
  </ion-breadcrumb>
  <ion-breadcrumb href="#cameras">
    <ion-icon slot="start" name="camera"></ion-icon>
    Cameras
  </ion-breadcrumb>
  <ion-breadcrumb href="#film">
    <ion-icon slot="start" name="film"></ion-icon>
    Film
  </ion-breadcrumb>
</ion-breadcrumbs>

<ion-label class="ion-margin-top">Icons at End</ion-label>
<ion-breadcrumbs>
  <ion-breadcrumb href="#home">
    Home
    <ion-icon slot="end" name="home"></ion-icon>
  </ion-breadcrumb>
  <ion-breadcrumb href="#electronics">
    Electronics
    <ion-icon slot="end" name="flash"></ion-icon>
  </ion-breadcrumb>
  <ion-breadcrumb href="#cameras">
    Cameras
    <ion-icon slot="end" name="camera"></ion-icon>
  </ion-breadcrumb>
  <ion-breadcrumb href="#film">
    Film
    <ion-icon slot="end" name="film"></ion-icon>
  </ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs, IonIcon, IonLabel } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { camera, film, flash, home } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs, IonIcon, IonLabel],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ camera, film, flash, home });
  }
}
```

### Custom Separators

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-breadcrumbs>
  <ion-breadcrumb href="#home">
    Home
    <ion-icon slot="separator" name="arrow-forward-circle"></ion-icon>
  </ion-breadcrumb>
  <ion-breadcrumb href="#electronics">
    Electronics
    <ion-icon slot="separator" name="arrow-forward-circle"></ion-icon>
  </ion-breadcrumb>
  <ion-breadcrumb href="#cameras">
    Cameras
    <ion-icon slot="separator" name="arrow-forward-circle"></ion-icon>
  </ion-breadcrumb>
  <ion-breadcrumb href="#film">
    Film
    <ion-icon slot="separator" name="arrow-forward-circle"></ion-icon>
  </ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { arrowForwardCircle } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ arrowForwardCircle });
  }
}
```

## Collapsing Items

### Max Items

If there are more items than the value of `maxItems`, the breadcrumbs will be collapsed. By default, only the first and last items will be shown.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-breadcrumbs [maxItems]="4">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs],
})
export class ExampleComponent {}
```

### Items Before or After Collapse

Once the items are collapsed, the number of items to show can be controlled by the `itemsBeforeCollapse` and `itemsAfterCollapse` properties.

- src/app/example.component.html
- src/app/example.component.ts

```html
<div>Before Collapse = 2</div>
<ion-breadcrumbs [maxItems]="4" [itemsBeforeCollapse]="2">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>

<div class="ion-margin-top">Before Collapse = 0</div>
<ion-breadcrumbs [maxItems]="4" [itemsBeforeCollapse]="0">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>

<div class="ion-margin-top">After Collapse = 2</div>
<ion-breadcrumbs [maxItems]="4" [itemsAfterCollapse]="2">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>

<div class="ion-margin-top">Before Collapse = 2, After Collapse = 2</div>
<ion-breadcrumbs [maxItems]="4" [itemsBeforeCollapse]="2" [itemsAfterCollapse]="2">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs],
})
export class ExampleComponent {}
```

### Collapsed Indicator Click -- Expand Breadcrumbs

Clicking the collapsed indicator will fire the `ionCollapsedClick` event. This can be used to, for example, expand the breadcrumbs.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-breadcrumbs [maxItems]="maxBreadcrumbs" (ionCollapsedClick)="expandBreadcrumbs()">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs],
})
export class ExampleComponent {
  maxBreadcrumbs? = 4;

  expandBreadcrumbs() {
    this.maxBreadcrumbs = undefined;
  }
}
```

### Collapsed Indicator Click -- Present Popover

The `ionCollapsedClick` event can also be used to present an overlay (in this case, an `ion-popover`) showing the hidden breadcrumbs.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-breadcrumbs [maxItems]="4" (ionCollapsedClick)="presentPopover($event)">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#photography">Photography</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
  <ion-breadcrumb href="#35mm">35 mm</ion-breadcrumb>
</ion-breadcrumbs>
<ion-popover #popover [isOpen]="isOpen" (didDismiss)="isOpen = false">
  <ng-template>
    <ion-content>
      <ion-list>
        @for (breadcrumb of collapsedBreadcrumbs; track breadcrumb; let last = $last) {
        <ion-item [href]="breadcrumb.href" [lines]="last ? 'none' : null">
          <ion-label>{{ breadcrumb.textContent }}</ion-label>
        </ion-item>
        }
      </ion-list>
    </ion-content>
  </ng-template>
</ion-popover>
```

```ts
import { Component, ViewChild } from '@angular/core';
import {
  IonBreadcrumb,
  IonBreadcrumbs,
  IonContent,
  IonItem,
  IonLabel,
  IonList,
  IonPopover,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs, IonContent, IonItem, IonLabel, IonList, IonPopover],
})
export class ExampleComponent {
  @ViewChild('popover') popover!: HTMLIonPopoverElement;

  isOpen = false;
  collapsedBreadcrumbs: HTMLIonBreadcrumbElement[] = [];

  async presentPopover(e: Event) {
    this.collapsedBreadcrumbs = (e as CustomEvent).detail.collapsedBreadcrumbs;
    this.popover.event = e;
    this.isOpen = true;
  }
}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-breadcrumbs color="primary">
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
</ion-breadcrumbs>
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-breadcrumbs>
  <ion-breadcrumb href="#home">Home</ion-breadcrumb>
  <ion-breadcrumb href="#electronics">Electronics</ion-breadcrumb>
  <ion-breadcrumb href="#cameras">Cameras</ion-breadcrumb>
  <ion-breadcrumb href="#film">Film</ion-breadcrumb>
</ion-breadcrumbs>
```

```css
ion-breadcrumb {
  --color: rgb(81, 155, 198);
  --color-active: rgb(150, 112, 220);
  --color-hover: rgb(103, 61, 180);
}
```

```ts
import { Component } from '@angular/core';
import { IonBreadcrumb, IonBreadcrumbs } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBreadcrumb, IonBreadcrumbs],
})
export class ExampleComponent {}
```

## Properties

### color

|     |     |
| --- | --- |
| **Description** | The color to use from your application's color palette. Default options are: `"primary"`, `"secondary"`, `"tertiary"`, `"success"`, `"warning"`, `"danger"`, `"light"`, `"medium"`, and `"dark"`. For more information on colors, see [theming](https://ionicframework.com/docs/theming/basics). |
| **Attribute** | `color` |
| **Type** | `"danger" ｜ "dark" ｜ "light" ｜ "medium" ｜ "primary" ｜ "secondary" ｜ "success" ｜ "tertiary" ｜ "warning" ｜ string ｜ undefined` |
| **Default** | `undefined` |

### itemsAfterCollapse

|     |     |
| --- | --- |
| **Description** | The number of breadcrumbs to show after the collapsed indicator. If `itemsBeforeCollapse` \+ `itemsAfterCollapse` is greater than `maxItems`, the breadcrumbs will not be collapsed. |
| **Attribute** | `items-after-collapse` |
| **Type** | `number` |
| **Default** | `1` |

### itemsBeforeCollapse

|     |     |
| --- | --- |
| **Description** | The number of breadcrumbs to show before the collapsed indicator. If `itemsBeforeCollapse` \+ `itemsAfterCollapse` is greater than `maxItems`, the breadcrumbs will not be collapsed. |
| **Attribute** | `items-before-collapse` |
| **Type** | `number` |
| **Default** | `1` |

### maxItems

|     |     |
| --- | --- |
| **Description** | The maximum number of breadcrumbs to show before collapsing. |
| **Attribute** | `max-items` |
| **Type** | `number ｜ undefined` |
| **Default** | `undefined` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionCollapsedClick` | Emitted when the collapsed indicator is clicked on. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
