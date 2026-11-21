# Ionic Reorder Guide

Source: https://ionicframework.com/docs/api/reorder

Sections: Basic Usage · Toggling Reorder · Custom Reorder Icon · Reorder Wrapper · Updating Data · Event Handling · Usage with Virtual Scroll · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Reorder is a component that allows an item to be dragged to change its order within a group of items. It must be used within a [reorder group](https://ionicframework.com/docs/api/reorder-group) to provide a visual drag and drop interface.

The reorder is the anchor used to drag and drop the items. Once the reorder is complete, the `ionReorderEnd` event will be dispatched from the reorder group and the `complete` method needs to be called.

## Basic Usage

The most basic example of a reorder is slotting it inside of an item. By default, the reorder functionality is disabled for a reorder group. It can be enabled by setting the `disabled` property on the reorder group to `false`. The reorder icon can then be used to drag and drop the items and reorder them.

Reorder

Item 1

Item 2

Item 3

Item 4

Item 5

Reorder

Item 1

Item 2

Item 3

Item 4

Item 5

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.ts
- src/app/example.component.html

```ts
import { Component } from '@angular/core';
import {
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  ReorderEndCustomEvent,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  handleReorderEnd(event: ReorderEndCustomEvent) {
    // The `from` and `to` properties contain the index of the item
    // when the drag started and ended, respectively
    console.log('Dragged from index', event.detail.from, 'to', event.detail.to);

    // Finish the reorder and position the item in the DOM based on
    // where the gesture ended. This method can also be called directly
    // by the reorder group.
    event.detail.complete();
  }
}
```

```html
<ion-list>
  <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group [disabled]="false" (ionReorderEnd)="handleReorderEnd($any($event))">
    <ion-item>
      <ion-label> Item 1 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 2 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 3 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 4 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 5 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>
  </ion-reorder-group>
</ion-list>
```

## Toggling Reorder

In some cases, it may be desired to have the option to toggle the reorder functionality. This can be done by making the `disabled` property reactive, based on a function or variable.

Reorder

Item 1

Item 2

Item 3

Item 4

Item 5

Toggle Reorder

Reorder

Item 1

Item 2

Item 3

Item 4

Item 5

Toggle Reorder

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.ts
- src/app/example.component.html

```ts
import { Component } from '@angular/core';
import {
  IonButton,
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  ReorderEndCustomEvent,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  public isDisabled = true;

  handleReorderEnd(event: ReorderEndCustomEvent) {
    // The `from` and `to` properties contain the index of the item
    // when the drag started and ended, respectively
    console.log('Dragged from index', event.detail.from, 'to', event.detail.to);

    // Finish the reorder and position the item in the DOM based on
    // where the gesture ended. This method can also be called directly
    // by the reorder group.
    event.detail.complete();
  }

  toggleReorder() {
    this.isDisabled = !this.isDisabled;
  }
}
```

```html
<ion-list>
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group [disabled]="isDisabled" (ionReorderEnd)="handleReorderEnd($any($event))">
    <ion-item>
      <ion-label> Item 1 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 2 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 3 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 4 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 5 </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>
  </ion-reorder-group>
</ion-list>

<!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
<ion-button (click)="toggleReorder()"> Toggle Reorder </ion-button>
```

## Custom Reorder Icon

The reorder component uses a reorder icon with three lines on iOS and two lines on Material Design. This can be customized by adding an [Icon](https://ionic.io/ionicons) component inside of the reorder with any of the available Ionicons.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group [disabled]="false" (ionReorderEnd)="handleReorderEnd($any($event))">
    <ion-item>
      <ion-label> Item 1 </ion-label>
      <ion-reorder slot="end">
        <ion-icon name="pizza"></ion-icon>
      </ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 2 </ion-label>
      <ion-reorder slot="end">
        <ion-icon name="pizza"></ion-icon>
      </ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 3 </ion-label>
      <ion-reorder slot="end">
        <ion-icon name="pizza"></ion-icon>
      </ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 4 </ion-label>
      <ion-reorder slot="end">
        <ion-icon name="pizza"></ion-icon>
      </ion-reorder>
    </ion-item>

    <ion-item>
      <ion-label> Item 5 </ion-label>
      <ion-reorder slot="end">
        <ion-icon name="pizza"></ion-icon>
      </ion-reorder>
    </ion-item>
  </ion-reorder-group>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import {
  IonIcon,
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  ReorderEndCustomEvent,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { pizza } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonIcon, IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ pizza });
  }

  handleReorderEnd(event: ReorderEndCustomEvent) {
    // The `from` and `to` properties contain the index of the item
    // when the drag started and ended, respectively
    console.log('Dragged from index', event.detail.from, 'to', event.detail.to);

    // Finish the reorder and position the item in the DOM based on
    // where the gesture ended. This method can also be called directly
    // by the reorder group.
    event.detail.complete();
  }
}
```

## Reorder Wrapper

Reorder can also be used as a wrapper around an item, making the item itself the anchor. Click anywhere on an item below and drag it to reorder the list.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.ts
- src/app/example.component.html

```ts
import { Component } from '@angular/core';
import {
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  ReorderEndCustomEvent,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  handleReorderEnd(event: ReorderEndCustomEvent) {
    // The `from` and `to` properties contain the index of the item
    // when the drag started and ended, respectively
    console.log('Dragged from index', event.detail.from, 'to', event.detail.to);

    // Finish the reorder and position the item in the DOM based on
    // where the gesture ended. This method can also be called directly
    // by the reorder group.
    event.detail.complete();
  }
}
```

```html
<ion-list>
  <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group [disabled]="false" (ionReorderEnd)="handleReorderEnd($any($event))">
    <ion-reorder>
      <ion-item>
        <ion-label> Item 1 </ion-label>
      </ion-item>
    </ion-reorder>

    <ion-reorder>
      <ion-item>
        <ion-label> Item 2 </ion-label>
      </ion-item>
    </ion-reorder>

    <ion-reorder>
      <ion-item>
        <ion-label> Item 3 </ion-label>
      </ion-item>
    </ion-reorder>

    <ion-reorder>
      <ion-item>
        <ion-label> Item 4 </ion-label>
      </ion-item>
    </ion-reorder>

    <ion-reorder>
      <ion-item>
        <ion-label> Item 5 </ion-label>
      </ion-item>
    </ion-reorder>
  </ion-reorder-group>
</ion-list>
```

## Updating Data

When the `complete` method is called on the reorder group with no parameters, the DOM nodes will be reordered. If the items are rendered from an array of data that needs to be sorted, this can result in the data and DOM being out of sync.

In order to sort the array upon completion of the reorder, the array should be passed as a parameter to the `complete` method. The `complete` method will sort the array and return it so it can be reassigned. Note that passing the array will prevent Ionic from reordering the DOM nodes.

In some cases, it may be necessary for an app to reorder both the array and the DOM nodes on its own. If this is required, `false` should be passed as a parameter to the `complete` method. This will prevent Ionic from reordering any DOM nodes inside of the reorder group.

Regardless of the approach taken, a stable identity should be provided to reorder items if provided in a loop. This means using `track` for Angular, and `key` for React and Vue.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.ts
- src/app/example.component.html

```ts
import { Component } from '@angular/core';
import {
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  ReorderEndCustomEvent,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  items = [1, 2, 3, 4, 5];

  handleReorderEnd(event: ReorderEndCustomEvent) {
    // Before complete is called with the items they will remain in the
    // order before the drag
    console.log('Before complete', this.items);

    // Finish the reorder and position the item in the DOM based on
    // where the gesture ended. Update the items variable to the
    // new order of items
    this.items = event.detail.complete(this.items);

    // After complete is called the items will be in the new order
    console.log('After complete', this.items);
  }
}
```

```html
<ion-list>
  <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group [disabled]="false" (ionReorderEnd)="handleReorderEnd($any($event))">
    @for (item of items; track item) {
    <ion-item>
      <ion-label> Item {{ item }} </ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>
    }
  </ion-reorder-group>
</ion-list>
```

## Event Handling

### Using `ionReorderStart` and `ionReorderEnd`

The `ionReorderStart` event is emitted when the user begins a reorder gesture. This event fires when the user taps and holds an item, before any movement occurs. This is useful for preparing the UI for the reorder operation, such as hiding certain elements or updating the visual state of items. For example, icons in list items can be hidden while they are being dragged and shown again when the reorder is complete.

The `ionReorderEnd` event is emitted when the user completes the reorder gesture. This occurs when the user releases the item they are dragging, for example by lifting their finger on a touch screen or releasing the mouse button. The event includes the `from` and `to` indices of the item, as well as the `complete` method that should be called to finalize the reorder operation. The `from` index will always be the position of the item when the gesture started, while the `to` index will be its final position. This event will fire even if no items have changed position, in which case the `from` and `to` indices will be the same.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group
    [disabled]="false"
    (ionReorderStart)="handleReorderStart()"
    (ionReorderEnd)="handleReorderEnd($any($event))"
  >
    @for (item of items; track item; let i = $index) {
    <ion-item>
      <ion-label>{{ item.label }}</ion-label>
      <ion-icon #icon [name]="item.icon" [color]="item.color" slot="end"></ion-icon>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>
    }
  </ion-reorder-group>
</ion-list>
```

```ts
import { Component, ViewChildren, QueryList, ElementRef } from '@angular/core';
import {
  ReorderEndCustomEvent,
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  IonIcon,
} from '@ionic/angular/standalone';
import { addIcons } from 'ionicons';
import { caretDown, ellipse, warning } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonReorder, IonReorderGroup, IonIcon],
})
export class ExampleComponent {
  items = [\
    { label: 'Buy groceries', icon: 'warning', color: 'warning' },\
    { label: 'Call the bank', icon: 'warning', color: 'warning' },\
    { label: 'Finish project report', icon: 'ellipse', color: 'light' },\
    { label: 'Book flight tickets', icon: 'ellipse', color: 'light' },\
    { label: 'Read a book', icon: 'caret-down', color: 'secondary' },\
  ];

  @ViewChildren('icon', { read: ElementRef }) icons!: QueryList<ElementRef<HTMLIonIconElement>>;

  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ caretDown, ellipse, warning });
  }

  handleReorderStart() {
    console.log('Reorder started');

    // Hide the icons when the reorder starts
    this.icons.forEach((icon) => {
      icon.nativeElement.style.opacity = '0';
    });
  }

  handleReorderEnd(event: ReorderEndCustomEvent) {
    console.log('Dragged from index', event.detail.from, 'to', event.detail.to);

    // Show the icons again
    this.icons.forEach((icon) => {
      icon.nativeElement.style.opacity = '1';
    });

    // Finish the reorder and update the items data
    this.items = event.detail.complete(this.items);
  }
}
```

### Using `ionReorderMove`

The `ionReorderMove` event is emitted continuously during the reorder gesture as the user drags an item. The event includes the `from` and `to` indices of the item. Unlike `ionReorderEnd`, the `from` index in this event represents the last known position of the item (which updates as the item moves), while the `to` index represents its current position. If the item has not changed position since the last event, the `from` and `to` indices will be the same. This event is useful for tracking position changes during the drag operation. For example, the ranking or numbering of items can be updated in real-time as they are being dragged to maintain a logical ascending order.

warning

Do not call the `complete` method during the `ionReorderMove` event as it can break the gesture.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.ts
- src/app/example.component.html

```ts
import { Component } from '@angular/core';
import {
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
  ReorderEndCustomEvent,
  ReorderMoveCustomEvent,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  items = ['Buy groceries', 'Call the bank', 'Finish project report', 'Book flight tickets', 'Read a book'];

  handleReorderMove(event: ReorderMoveCustomEvent) {
    const from = event.detail.from;
    const to = event.detail.to;

    if (from !== to) {
      console.log('Dragged from index', from, 'to', to);
    }

    // Get all items and sort by their current id (item-1, item-2, ...)
    const itemElements = Array.from(document.querySelectorAll('ion-item')).sort((a, b) => {
      const aNum = parseInt(a.id.replace('item-', ''), 10);
      const bNum = parseInt(b.id.replace('item-', ''), 10);
      return aNum - bNum;
    });

    // Dragging down: shift up items between from+1 and to, set dragged to to+1
    if (from < to) {
      for (let i = from; i <= to; i++) {
        const item = itemElements[i];
        const itemNum = item.querySelector('b');
        if (itemNum) {
          if (i === from) {
            // Dragged item
            itemNum.textContent = String(to + 1);
            item.id = `item-${to + 1}`;
          } else {
            // Items shift up
            itemNum.textContent = String(i);
            item.id = `item-${i}`;
          }
        }
      }
      // Dragging up: shift down items between to and from-1, set dragged to to+1
    } else if (from > to) {
      for (let i = to; i <= from; i++) {
        const item = itemElements[i];
        const itemNum = item.querySelector('b');
        if (itemNum) {
          if (i === from) {
            // Dragged item
            itemNum.textContent = String(to + 1);
            item.id = `item-${to + 1}`;
          } else {
            // Items shift down
            itemNum.textContent = String(i + 2);
            item.id = `item-${i + 2}`;
          }
        }
      }
    }
  }

  handleReorderEnd(event: ReorderEndCustomEvent) {
    // Finish the reorder and update the items data
    this.items = event.detail.complete(this.items);
  }
}
```

```html
<ion-list lines="full">
  <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
  <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
  <ion-reorder-group
    [disabled]="false"
    (ionReorderMove)="handleReorderMove($any($event))"
    (ionReorderEnd)="handleReorderEnd($any($event))"
  >
    @for (item of items; track item; let i = $index) {
    <ion-item [id]="'item-' + (i + 1)">
      <b slot="start">{{ i + 1 }}</b>
      <ion-label>{{ item }}</ion-label>
      <ion-reorder slot="end"></ion-reorder>
    </ion-item>
    }
  </ion-reorder-group>
</ion-list>
```

## Usage with Virtual Scroll

Reorder requires a scroll container to work properly. When using a virtual scrolling solution, a custom scroll target needs to be provided. Scrolling on the content needs to be disabled and the `.ion-content-scroll-host` class needs to be added to the element responsible for scrolling.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-content [scrollY]="false">
  <div class="ion-content-scroll-host">
    <ion-list>
      <!-- The reorder gesture is disabled by default, enable it to drag and drop items -->
      <!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
      <ion-reorder-group [disabled]="false" (ionReorderEnd)="handleReorderEnd($any($event))">
        <ion-item>
          <ion-label> Item 1 </ion-label>
          <ion-reorder slot="end"></ion-reorder>
        </ion-item>

        <ion-item>
          <ion-label> Item 2 </ion-label>
          <ion-reorder slot="end"></ion-reorder>
        </ion-item>

        <ion-item>
          <ion-label> Item 3 </ion-label>
          <ion-reorder slot="end"></ion-reorder>
        </ion-item>

        <ion-item>
          <ion-label> Item 4 </ion-label>
          <ion-reorder slot="end"></ion-reorder>
        </ion-item>

        <ion-item>
          <ion-label> Item 5 </ion-label>
          <ion-reorder slot="end"></ion-reorder>
        </ion-item>
      </ion-reorder-group>
    </ion-list>
  </div>
</ion-content>
```

```css
.ion-content-scroll-host {
  position: absolute;
  top: 0;
  left: 0;

  height: 100%;
  width: 100%;
  overflow-y: auto;
}
```

```ts
import { Component } from '@angular/core';
import {
  ReorderEndCustomEvent,
  IonContent,
  IonItem,
  IonLabel,
  IonList,
  IonReorder,
  IonReorderGroup,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['./example.component.css'],
  imports: [IonContent, IonItem, IonLabel, IonList, IonReorder, IonReorderGroup],
})
export class ExampleComponent {
  handleReorderEnd(event: ReorderEndCustomEvent) {
    // The `from` and `to` properties contain the index of the item
    // when the drag started and ended, respectively
    console.log('Dragged from index', event.detail.from, 'to', event.detail.to);

    // Finish the reorder and position the item in the DOM based on
    // where the gesture ended. This method can also be called directly
    // by the reorder group.
    event.detail.complete();
  }
}
```

## Properties

No properties available for this component.

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `icon` | The icon of the reorder handle (uses ion-icon). |

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
