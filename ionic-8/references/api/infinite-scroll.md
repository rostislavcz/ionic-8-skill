# Infinite Scroll Guide

Source: https://ionicframework.com/docs/api/infinite-scroll

Sections: Basic Usage · Loading Text and Spinner · Custom Content · Usage with Virtual Scroll · Accessibility · Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

The Infinite Scroll component calls an action to be performed when the user scrolls a specified distance from the bottom or top of the page.

The expression assigned to the `ionInfinite` event is called when the user reaches that defined distance. When this expression has finished any and all tasks, it should call the `complete()` method on the infinite scroll instance.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content>
  <ion-list>
    @for (item of items; track item; let index = $index) {
    <ion-item>
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
  IonInfiniteScroll,
  IonInfiniteScrollContent,
  IonItem,
  IonLabel,
  IonList,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonContent, IonInfiniteScroll, IonInfiniteScrollContent, IonItem, IonLabel, IonList],
})
export class ExampleComponent implements OnInit {
  items: string[] = [];

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

## Loading Text and Spinner

The `ion-infinite-scroll-content` is responsible for the visual display of the infinite scroll interaction. By default this component changes its look depending on the infinite scroll's state. It displays a spinner that looks best based on the platform the user is on. Both the spinner and loading text can be customized by setting properties on the `ion-infinite-scroll-content` component.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content>
  <ion-list>
    @for (item of items; track item; let index = $index) {
    <ion-item>
      <ion-avatar slot="start">
        <img [src]="'https://picsum.photos/80/80?random=' + index" alt="avatar" />
      </ion-avatar>
      <ion-label>{{ item }}</ion-label>
    </ion-item>
    }
  </ion-list>
  <ion-infinite-scroll>
    <ion-infinite-scroll-content loadingText="Please wait..." loadingSpinner="bubbles"></ion-infinite-scroll-content>
  </ion-infinite-scroll>
</ion-content>
```

```tsx
import { Component, OnInit } from '@angular/core';
import {
  IonAvatar,
  IonContent,
  IonInfiniteScroll,
  IonInfiniteScrollContent,
  IonItem,
  IonLabel,
  IonList,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonContent, IonInfiniteScroll, IonInfiniteScrollContent, IonItem, IonLabel, IonList],
})
export class ExampleComponent implements OnInit {
  items: string[] = [];

  ngOnInit() {
    for (let i = 1; i < 51; i++) {
      this.items.push(`Item ${i}`);
    }
  }
}
```

## Custom Content

Separating the `ion-infinite-scroll` and `ion-infinite-scroll-content` components allows developers to create their own content components, if desired. This content can contain anything, from an SVG element to elements with unique CSS animations.

- src/app/example.component.html
- src/app/example.component.ts
- src/app/example.component.css

```html
<ion-content>
  <ion-list>
    @for (item of items; track item; let index = $index) {
    <ion-item>
      <ion-avatar slot="start">
        <img [src]="'https://picsum.photos/80/80?random=' + index" alt="avatar" />
      </ion-avatar>
      <ion-label>{{ item }}</ion-label>
    </ion-item>
    }
  </ion-list>
  <ion-infinite-scroll>
    <div class="infinite-scroll-content">
      <svg
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        x="0px"
        y="0px"
        viewBox="0 0 100 100"
        enable-background="new 0 0 100 100"
        xml:space="preserve"
      >
        <circle fill="none" stroke="#1b6dff" stroke-width="4" stroke-miterlimit="10" cx="50" cy="50" r="48" />
        <line
          fill="none"
          stroke-linecap="round"
          stroke="#1b6dff"
          stroke-width="4"
          stroke-miterlimit="10"
          x1="50"
          y1="50"
          x2="85"
          y2="50.5"
        >
          <animateTransform
            attributeName="transform"
            dur="2s"
            type="rotate"
            from="0 50 50"
            to="360 50 50"
            repeatCount="indefinite"
          />
        </line>
        <line
          fill="none"
          stroke-linecap="round"
          stroke="#1b6dff"
          stroke-width="4"
          stroke-miterlimit="10"
          x1="50"
          y1="50"
          x2="49.5"
          y2="74"
        >
          <animateTransform
            attributeName="transform"
            dur="15s"
            type="rotate"
            from="0 50 50"
            to="360 50 50"
            repeatCount="indefinite"
          />
        </line>
      </svg>
    </div>
  </ion-infinite-scroll>
</ion-content>
```

```tsx
import { Component, OnInit } from '@angular/core';
import { IonAvatar, IonContent, IonInfiniteScroll, IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonContent, IonInfiniteScroll, IonItem, IonLabel, IonList],
})
export class ExampleComponent implements OnInit {
  items: string[] = [];

  ngOnInit() {
    for (let i = 1; i < 51; i++) {
      this.items.push(`Item ${i}`);
    }
  }
}
```

```css
svg {
  width: 20px;
  height: 20px;
  display: inline-block;
}

.infinite-scroll-content {
  text-align: center;
  padding: 20px 0;
}
```

## Usage with Virtual Scroll

Infinite scroll requires a scroll container. When using a virtual scrolling solution, you will need to disable scrolling on the `ion-content` and indicate which element container is responsible for the scroll container with the `.ion-content-scroll-host` class target.

```html
<ion-content scroll-y="false">
  <virtual-scroll-element class="ion-content-scroll-host">
    <!-- Your virtual scroll content -->
  </virtual-scroll-element>
  <ion-infinite-scroll>
    <ion-infinite-scroll-content></ion-infinite-scroll-content>
  </ion-infinite-scroll>
</ion-content>
```

note

`virtual-scroll-element` refers to the scroll container responsible for scrolling the content. This may be a component provided directly by the virtual scroll solution you are using.

## Accessibility

Developers should assign the `role="feed"` attribute to the scrollable list of items that are added to or removed from as the user scrolls.

Individual list items should either have `role="article"` or use the `<article>` element directly.

For example, when rendering a collection of items in an `ion-list`:

```html
<ion-content role="feed">
  <ion-list>
    <ion-item role="article">
      First item
    </ion-item>
    <ion-item role="article">
      Second item
    </ion-item>
    ...
  </ion-list>

  <ion-infinite-scroll>
    <ion-infinite-scroll-content></ion-infinite-scroll-content>
  </ion-infinite-scroll>
</ion-content>
```

Please refer to the [ARIA: feed role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/feed_role) documentation for additional information.

## Interfaces

### InfiniteScrollCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface InfiniteScrollCustomEvent extends CustomEvent {
  target: HTMLIonInfiniteScrollElement;
}
```

## Properties

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the infinite scroll will be hidden and scroll event listeners will be removed.<br>Set this to true to disable the infinite scroll from actively trying to receive new data while scrolling. This is useful when it is known that there is no more data that can be added, and the infinite scroll is no longer needed. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### position

|     |     |
| --- | --- |
| **Description** | The position of the infinite scroll element. The value can be either `top` or `bottom`. |
| **Attribute** | `position` |
| **Type** | `"bottom" ｜ "top"` |
| **Default** | `'bottom'` |

### threshold

|     |     |
| --- | --- |
| **Description** | The threshold distance from the bottom of the content to call the `infinite` output event when scrolled. The threshold value can be either a percent, or in pixels. For example, use the value of `10%` for the `infinite` output event to get called when the user has scrolled 10% from the bottom of the page. Use the value `100px` when the scroll is within 100 pixels from the bottom of the page. |
| **Attribute** | `threshold` |
| **Type** | `string` |
| **Default** | `'15%'` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionInfinite` | Emitted when the scroll reaches the threshold distance. From within your infinite handler, you must call the infinite scroll's `complete()` method when your async operation has completed. | `true` |

## Methods

### complete

|     |     |
| --- | --- |
| **Description** | Call `complete()` within the `ionInfinite` output event handler when your async operation has completed. For example, the `loading` state is while the app is performing an asynchronous operation, such as receiving more data from an AJAX request to add more items to a data list. Once the data has been received and UI updated, you then call this method to signify that the loading has completed. This method will change the infinite scroll's state from `loading` to `enabled`. |
| **Signature** | `complete() => Promise<void>` |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
