# Ionic Button Guide

Source: https://ionicframework.com/docs/api/buttons

Sections: Basic Usage · Buttons Placement · Types of Buttons · Collapsible Buttons · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[scoped](https://ionicframework.com/docs/reference/glossary#scoped)

The Buttons component is a container element. It should be used inside of a [toolbar](https://ionicframework.com/docs/api/toolbar) and can contain several types of buttons, including standard [buttons](https://ionicframework.com/docs/api/button), [menu buttons](https://ionicframework.com/docs/api/menu-button), and [back buttons](https://ionicframework.com/docs/api/back-button).

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-toolbar>
  <ion-buttons slot="start">
    <ion-button>Button</ion-button>
  </ion-buttons>
  <ion-title>Default Buttons</ion-title>
</ion-toolbar>
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonButtons, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonButtons, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Buttons Placement

Buttons can be positioned inside of the toolbar using a named slot. The below chart has a description of each slot.

| Slot | Description |
| --- | --- |
| `start` | Positions to the `left` of the content in LTR, and to the `right` in RTL. |
| `end` | Positions to the `right` of the content in LTR, and to the `left` in RTL. |
| `secondary` | Positions element to the `left` of the content in `ios` mode, and directly to the `right` in `md` mode. |
| `primary` | Positions element to the `right` of the content in `ios` mode, and to the far `right` in `md` mode. |

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-toolbar>
  <ion-buttons slot="start">
    <ion-button>Start</ion-button>
  </ion-buttons>
  <ion-title>Buttons</ion-title>
  <ion-buttons slot="end">
    <ion-button>End</ion-button>
  </ion-buttons>
</ion-toolbar>

<ion-toolbar>
  <ion-buttons slot="secondary">
    <ion-button>Secondary</ion-button>
  </ion-buttons>
  <ion-title>Buttons</ion-title>
  <ion-buttons slot="primary">
    <ion-button>Primary</ion-button>
  </ion-buttons>
</ion-toolbar>
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonButtons, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonButtons, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Types of Buttons

A button in a toolbar is styled to be clear by default, but this can be changed using the [`fill`](https://ionicframework.com/docs/api/button#fill) property on the button. The properties included on [back button](https://ionicframework.com/docs/api/back-button) and [menu button](https://ionicframework.com/docs/api/menu-button) in this example are for display purposes; see their respective documentation for proper usage.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-toolbar>
  <ion-buttons slot="secondary">
    <ion-button size="large"> Favorite </ion-button>
  </ion-buttons>
  <ion-title>Default Buttons</ion-title>
  <ion-buttons slot="primary">
    <ion-button> Delete </ion-button>
  </ion-buttons>
</ion-toolbar>

<ion-toolbar>
  <ion-buttons slot="secondary">
    <ion-button>
      <ion-icon slot="icon-only" name="person-circle"></ion-icon>
    </ion-button>
    <ion-button>
      <ion-icon slot="icon-only" name="search"></ion-icon>
    </ion-button>
  </ion-buttons>
  <ion-buttons slot="primary">
    <ion-button>
      <ion-icon slot="icon-only" ios="ellipsis-horizontal" md="ellipsis-vertical"></ion-icon>
    </ion-button>
  </ion-buttons>
  <ion-title>Icon Buttons</ion-title>
</ion-toolbar>

<ion-toolbar>
  <ion-buttons slot="secondary">
    <ion-button fill="solid">
      <ion-icon slot="start" name="person-circle"></ion-icon>
      Contact
    </ion-button>
  </ion-buttons>
  <ion-buttons slot="primary">
    <ion-button fill="solid">
      Help
      <ion-icon slot="end" name="help-circle"></ion-icon>
    </ion-button>
  </ion-buttons>
  <ion-title>Solid Buttons</ion-title>
</ion-toolbar>

<ion-toolbar>
  <ion-buttons slot="secondary">
    <ion-button fill="outline">
      <ion-icon slot="start" name="star"></ion-icon>
      Star
    </ion-button>
  </ion-buttons>
  <ion-buttons slot="primary">
    <ion-button fill="outline">
      Edit
      <ion-icon slot="end" name="create"></ion-icon>
    </ion-button>
  </ion-buttons>
  <ion-title>Outline Buttons</ion-title>
</ion-toolbar>

<ion-toolbar>
  <ion-buttons slot="start">
    <ion-back-button default-href="#"></ion-back-button>
  </ion-buttons>
  <ion-title>Back Button</ion-title>
</ion-toolbar>

<ion-toolbar>
  <ion-buttons slot="start">
    <ion-menu-button auto-hide="false"></ion-menu-button>
  </ion-buttons>
  <ion-title>Menu Button</ion-title>
</ion-toolbar>
```

```ts
import { Component } from '@angular/core';
import {
  IonBackButton,
  IonButton,
  IonButtons,
  IonIcon,
  IonMenuButton,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { create, ellipsisHorizontal, ellipsisVertical, helpCircle, personCircle, search, star } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBackButton, IonButton, IonButtons, IonIcon, IonMenuButton, IonTitle, IonToolbar],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ create, ellipsisHorizontal, ellipsisVertical, helpCircle, personCircle, search, star });
  }
}
```

## Collapsible Buttons

The `collapse` property can be set on the buttons to collapse them when the header collapses. This is typically used with [collapsible large titles](https://ionicframework.com/docs/api/title#collapsible-large-titles).

info

This feature is only available for iOS.

iOS

MD

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-header [translucent]="true">
  <ion-toolbar>
    <ion-title>Title</ion-title>
    <ion-buttons [collapse]="true" slot="end">
      <ion-button>Button</ion-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>
<ion-content [fullscreen]="true">
  <ion-header collapse="condense">
    <ion-toolbar>
      <ion-title size="large">Title</ion-title>
      <ion-buttons [collapse]="true" slot="end">
        <ion-button>Button</ion-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>

  <div class="ion-padding">Scroll the list to see the title & buttons collapse.</div>

  <ion-list>
    <ion-item>Item 1</ion-item>
    <ion-item>Item 2</ion-item>
    <ion-item>Item 3</ion-item>
    <ion-item>Item 4</ion-item>
    <ion-item>Item 5</ion-item>
    <ion-item>Item 6</ion-item>
    <ion-item>Item 7</ion-item>
    <ion-item>Item 8</ion-item>
    <ion-item>Item 9</ion-item>
    <ion-item>Item 10</ion-item>
    <ion-item>Item 11</ion-item>
    <ion-item>Item 12</ion-item>
    <ion-item>Item 13</ion-item>
    <ion-item>Item 14</ion-item>
    <ion-item>Item 15</ion-item>
    <ion-item>Item 16</ion-item>
    <ion-item>Item 17</ion-item>
    <ion-item>Item 18</ion-item>
    <ion-item>Item 19</ion-item>
    <ion-item>Item 20</ion-item>
  </ion-list>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import {
  IonButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonItem,
  IonList,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonButtons, IonContent, IonHeader, IonItem, IonList, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Properties

### collapse

|     |     |
| --- | --- |
| **Description** | If true, buttons will disappear when its parent toolbar has fully collapsed if the toolbar is not the first toolbar. If the toolbar is the first toolbar, the buttons will be hidden and will only be shown once all toolbars have fully collapsed.<br>Only applies in `ios` mode with `collapse` set to `true` on `ion-header`.<br>Typically used for [Collapsible Large Titles](https://ionicframework.com/docs/api/title#collapsible-large-titles) |
| **Attribute** | `collapse` |
| **Type** | `boolean` |
| **Default** | `false` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
