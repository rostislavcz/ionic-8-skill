# Sliding Item Options

Source: https://ionicframework.com/docs/api/item-sliding

Sections: Basic Usage · Icon Options · Expandable Options · Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

A sliding item contains an item that can be dragged to reveal option buttons. It requires an [item](https://ionicframework.com/docs/api/item) component as a child. All options to reveal should be placed in the [item options](https://ionicframework.com/docs/api/item-options) element.

## Basic Usage

Sliding item options are placed on the `"end"` side of the item by default. This means that options are revealed when the item is swiped from end to start, i.e. from right to left in LTR, but from left to right in RTL. To place them on the opposite side, so that they are revealed when swiping in the opposite direction, set the side attribute to `"start"` on the [item options](https://ionicframework.com/docs/api/item-options) element. Up to two item options can be used at the same time in order to reveal two different sets of options depending on the swiping direction.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item-sliding>
    <ion-item>
      <ion-label>Sliding Item with End Options</ion-label>
    </ion-item>

    <ion-item-options>
      <ion-item-option>Favorite</ion-item-option>
      <ion-item-option color="danger">Delete</ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">Archive</ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label>Sliding Item with Start Options</ion-label>
    </ion-item>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">Archive</ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label>Sliding Item with Options on Both Sides</ion-label>
    </ion-item>

    <ion-item-options side="end">
      <ion-item-option>Favorite</ion-item-option>
      <ion-item-option color="danger">Delete</ion-item-option>
    </ion-item-options>
  </ion-item-sliding>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonItemOption, IonItemOptions, IonItemSliding, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonItemOption, IonItemOptions, IonItemSliding, IonLabel, IonList],
})
export class ExampleComponent {}
```

## Icon Options

When an icon is placed alongside text in the [item option](https://ionicframework.com/docs/api/item-option), it will display the icon on top of the text by default. The slot on the icon can be changed to any of the available [item option slots](https://ionicframework.com/docs/api/item-option#slots) to change its position.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">
        <ion-icon slot="icon-only" name="archive"></ion-icon>
      </ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label>Sliding Item with Icons Only</ion-label>
    </ion-item>

    <ion-item-options side="end">
      <ion-item-option>
        <ion-icon slot="icon-only" name="heart"></ion-icon>
      </ion-item-option>
      <ion-item-option color="danger">
        <ion-icon slot="icon-only" name="trash"></ion-icon>
      </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">
        <ion-icon slot="start" name="archive"></ion-icon>
        Archive
      </ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label> Sliding Item with Start Icons </ion-label>
    </ion-item>

    <ion-item-options side="end">
      <ion-item-option>
        <ion-icon slot="start" name="heart"></ion-icon>
        Favorite
      </ion-item-option>
      <ion-item-option color="danger">
        <ion-icon slot="start" name="trash"></ion-icon>
        Delete
      </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">
        <ion-icon slot="end" name="archive"></ion-icon>
        Archive
      </ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label> Sliding Item with End Icons </ion-label>
    </ion-item>

    <ion-item-options>
      <ion-item-option>
        <ion-icon slot="end" name="heart"></ion-icon>
        Favorite
      </ion-item-option>
      <ion-item-option color="danger">
        <ion-icon slot="end" name="trash"></ion-icon>
        Delete
      </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">
        <ion-icon slot="top" name="archive"></ion-icon>
        Archive
      </ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label> Sliding Item with Top Icons </ion-label>
    </ion-item>

    <ion-item-options>
      <ion-item-option>
        <ion-icon slot="top" name="heart"></ion-icon>
        Favorite
      </ion-item-option>
      <ion-item-option color="danger">
        <ion-icon slot="top" name="trash"></ion-icon>
        Delete
      </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success">
        <ion-icon slot="bottom" name="archive"></ion-icon>
        Archive
      </ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label> Sliding Item with Bottom Icons </ion-label>
    </ion-item>

    <ion-item-options>
      <ion-item-option>
        <ion-icon slot="bottom" name="heart"></ion-icon>
        Favorite
      </ion-item-option>
      <ion-item-option color="danger">
        <ion-icon slot="bottom" name="trash"></ion-icon>
        Delete
      </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import {
  IonIcon,
  IonItem,
  IonItemOption,
  IonItemOptions,
  IonItemSliding,
  IonLabel,
  IonList,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { archive, heart, trash } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonIcon, IonItem, IonItemOption, IonItemOptions, IonItemSliding, IonLabel, IonList],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ archive, heart, trash });
  }
}
```

## Expandable Options

Options can be expanded to take up the full width of the parent `ion-item` if you swipe past a certain point. This can be combined with the `ionSwipe` event on the [item options](https://ionicframework.com/docs/api/item-options) to call a method when the item is fully swiped.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item-sliding>
    <ion-item-options side="start">
      <ion-item-option color="success" expandable>Archive</ion-item-option>
    </ion-item-options>

    <ion-item>
      <ion-label>Sliding Item with Expandable Options</ion-label>
    </ion-item>

    <ion-item-options side="end">
      <ion-item-option>Favorite</ion-item-option>
      <ion-item-option color="danger" expandable>Delete</ion-item-option>
    </ion-item-options>
  </ion-item-sliding>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonItemOption, IonItemOptions, IonItemSliding, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonItemOption, IonItemOptions, IonItemSliding, IonLabel, IonList],
})
export class ExampleComponent {}
```

## Interfaces

### ItemSlidingCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface ItemSlidingCustomEvent extends CustomEvent {
  target: HTMLIonItemSlidingElement;
}
```

## Properties

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the user cannot interact with the sliding item. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionDrag` | Emitted when the sliding position changes. | `true` |

## Methods

### close

|     |     |
| --- | --- |
| **Description** | Close the sliding item. Items can also be closed from the [List](https://ionicframework.com/docs/api/list). |
| **Signature** | `close() => Promise<void>` |

### closeOpened

|     |     |
| --- | --- |
| **Description** | Close all of the sliding items in the list. Items can also be closed from the [List](https://ionicframework.com/docs/api/list). |
| **Signature** | `closeOpened() => Promise<boolean>` |

### getOpenAmount

|     |     |
| --- | --- |
| **Description** | Get the amount the item is open in pixels. |
| **Signature** | `getOpenAmount() => Promise<number>` |

### getSlidingRatio

|     |     |
| --- | --- |
| **Description** | Get the ratio of the open amount of the item compared to the width of the options. If the number returned is positive, then the options on the right side are open. If the number returned is negative, then the options on the left side are open. If the absolute value of the number is greater than 1, the item is open more than the width of the options. |
| **Signature** | `getSlidingRatio() => Promise<number>` |

### open

|     |     |
| --- | --- |
| **Description** | Open the sliding item. |
| **Signature** | `open(side: Side ｜ undefined) => Promise<void>` |
| **Parameters** | **side**: The side of the options to open. If a side is not provided, it will open the first set of options it finds within the item. |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
