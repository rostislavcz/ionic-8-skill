# Ionic List Component

Source: https://ionicframework.com/docs/api/list

Sections: Basic Usage · Inset List · List Lines · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

Lists are made up of multiple rows of [items](https://ionicframework.com/docs/api/item) which can contain text, buttons, toggles,
icons, thumbnails, and much more. Lists generally contain items with similar data content, such as images and text.

Lists support several interactions including swiping items to reveal options, dragging to [reorder](https://ionicframework.com/docs/api/reorder) items within the list, and deleting items.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-label>Pokémon Yellow</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Mega Man X</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>The Legend of Zelda</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Pac-Man</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Super Mario World</ion-label>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList],
})
export class ExampleComponent {}
```

## Inset List

Adding the `inset` property to a list will apply margin around the list. In `ios` mode it will also add rounded corners to the list.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content color="light">
  <ion-list [inset]="true">
    <ion-item>
      <ion-label>Pokémon Yellow</ion-label>
    </ion-item>
    <ion-item>
      <ion-label>Mega Man X</ion-label>
    </ion-item>
    <ion-item>
      <ion-label>The Legend of Zelda</ion-label>
    </ion-item>
    <ion-item>
      <ion-label>Pac-Man</ion-label>
    </ion-item>
    <ion-item>
      <ion-label>Super Mario World</ion-label>
    </ion-item>
  </ion-list>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import { IonContent, IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent, IonItem, IonLabel, IonList],
})
export class ExampleComponent {}
```

## List Lines

Adding the `lines` property to a list will adjust the bottom borders of all of the items in the list. Setting it to `"full"` will display full width borders, `"inset"` will display borders adjusted with left padding, and `"none"` will show no borders. If the `lines` property is set on an item in a list, that will take priority over the property on the list.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list lines="full">
  <ion-item>
    <ion-label>Full Lines</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Full Lines</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Full Lines</ion-label>
  </ion-item>
</ion-list>

<ion-list lines="inset">
  <ion-item>
    <ion-label>Inset Lines</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Inset Lines</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Inset Lines</ion-label>
  </ion-item>
</ion-list>

<ion-list lines="none">
  <ion-item>
    <ion-label>No Lines</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>No Lines</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>No Lines</ion-label>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList],
})
export class ExampleComponent {}
```

## Properties

### inset

|     |     |
| --- | --- |
| **Description** | If `true`, the list will have margin around it and rounded corners. |
| **Attribute** | `inset` |
| **Type** | `boolean` |
| **Default** | `false` |

### lines

|     |     |
| --- | --- |
| **Description** | How the bottom border should be displayed on all items. |
| **Attribute** | `lines` |
| **Type** | `"full" ｜ "inset" ｜ "none" ｜ undefined` |
| **Default** | `undefined` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

## Events

No events available for this component.

## Methods

### closeSlidingItems

|     |     |
| --- | --- |
| **Description** | If `ion-item-sliding` are used inside the list, this method closes any open sliding item.<br>Returns `true` if an actual `ion-item-sliding` is closed. |
| **Signature** | `closeSlidingItems() => Promise<boolean>` |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
