# Ionic Backdrop Guide

Source: https://ionicframework.com/docs/api/backdrop

Sections: Basic Usage · Styling · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Backdrops are full screen components that overlay other components. They are useful behind components that transition in on top of other content and can be used to dismiss that component.

## Basic Usage

The backdrop prevents clicking or tapping on the content behind it. It is transparent by default, so the below demo includes CSS to make it visible.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-backdrop [visible]="true"></ion-backdrop>
<div class="ion-page">
  <ion-header>
    <ion-toolbar>
      <ion-title>Backdrop</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-item>
      <ion-checkbox>Checkbox</ion-checkbox>
    </ion-item>
    <ion-button expand="block">Button</ion-button>
  </ion-content>
</div>
```

```css
ion-backdrop {
  background: var(--ion-color-dark);
  opacity: 0.3;
}
```

```ts
import { Component } from '@angular/core';
import {
  IonBackdrop,
  IonButton,
  IonCheckbox,
  IonContent,
  IonHeader,
  IonItem,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBackdrop, IonButton, IonCheckbox, IonContent, IonHeader, IonItem, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Styling

The backdrop can be customized by assigning CSS properties directly to the backdrop element. Common properties include `background-color`, `background` and `opacity`.

Content can be displayed above the backdrop by setting a `z-index` on the content, higher than the backdrop (defaults to `2`).

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-backdrop [visible]="true"></ion-backdrop>
<div class="ion-page">
  <ion-header>
    <ion-toolbar>
      <ion-title>Backdrop</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Esse, cum aspernatur cupiditate nesciunt totam
      perspiciatis delectus soluta laboriosam, ullam impedit porro eaque laborum optio natus sed nostrum, provident
      expedita vero!
    </p>
  </ion-content>
</div>
<div id="box">
  <ion-checkbox color="light"></ion-checkbox>
  <ion-button class="ion-margin-start" color="light">Clickable</ion-button>
</div>
```

```css
ion-backdrop {
  opacity: 0.9;
  background: var(--ion-color-primary);
}

#box {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateY(-50%) translateX(-50%);
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--ion-background-color, #fff);
  width: 90%;
  height: 100px;
  border-radius: 10px;
}
```

```ts
import { Component } from '@angular/core';
import {
  IonBackdrop,
  IonButton,
  IonCheckbox,
  IonContent,
  IonHeader,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBackdrop, IonButton, IonCheckbox, IonContent, IonHeader, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Properties

### stopPropagation

|     |     |
| --- | --- |
| **Description** | If `true`, the backdrop will stop propagation on tap. |
| **Attribute** | `stop-propagation` |
| **Type** | `boolean` |
| **Default** | `true` |

### tappable

|     |     |
| --- | --- |
| **Description** | If `true`, the backdrop will can be clicked and will emit the `ionBackdropTap` event. |
| **Attribute** | `tappable` |
| **Type** | `boolean` |
| **Default** | `true` |

### visible

|     |     |
| --- | --- |
| **Description** | If `true`, the backdrop will be visible. |
| **Attribute** | `visible` |
| **Type** | `boolean` |
| **Default** | `true` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionBackdropTap` | Emitted when the backdrop is tapped. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
