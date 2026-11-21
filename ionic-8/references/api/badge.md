# Ionic Badges Guide

Source: https://ionicframework.com/docs/api/badge

Sections: Basic Usage · Badges in Tab Buttons · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Badges are inline block elements that usually appear near another element. Typically they contain a number or other characters. They can be used as a notification that there are additional items associated with an element and indicate how many items there are. Badges are hidden if no content is passed in.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-badge slot="start">11</ion-badge>
    <ion-label>Badge in start slot</ion-label>
  </ion-item>
  <ion-item>
    <ion-badge slot="end">22</ion-badge>
    <ion-label>Badge in end slot</ion-label>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonBadge, IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBadge, IonItem, IonLabel, IonList],
})
export class ExampleComponent {}
```

## Badges in Tab Buttons

Badges can be added inside a tab button, often used to indicate notifications or highlight additional items associated with the element.

info

Empty badges are only available for `md` mode.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-tab-bar color="light">
  <ion-tab-button tab="1">
    <ion-icon name="heart"></ion-icon>
    <ion-label>Favorites</ion-label>
    <ion-badge color="danger"></ion-badge>
  </ion-tab-button>

  <ion-tab-button tab="2">
    <ion-icon name="musical-note"></ion-icon>
    <ion-label>Music</ion-label>
  </ion-tab-button>

  <ion-tab-button tab="3">
    <ion-icon name="calendar"></ion-icon>
    <ion-label>Calendar</ion-label>
    <ion-badge color="danger">47</ion-badge>
  </ion-tab-button>
</ion-tab-bar>
```

```ts
import { Component } from '@angular/core';
import { IonBadge, IonTabBar, IonTabButton, IonIcon, IonLabel } from '@ionic/angular/standalone';
import { addIcons } from 'ionicons';
import { heart, calendar, musicalNote } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['./example.component.css'],
  imports: [IonBadge, IonTabBar, IonTabButton, IonIcon, IonLabel],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ heart, calendar, musicalNote });
  }
}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-label>Followers</ion-label>
    <ion-badge color="primary">22k</ion-badge>
  </ion-item>
  <ion-item>
    <ion-label>Likes</ion-label>
    <ion-badge color="secondary">118k</ion-badge>
  </ion-item>
  <ion-item>
    <ion-label>Stars</ion-label>
    <ion-badge color="tertiary">34k</ion-badge>
  </ion-item>
  <ion-item>
    <ion-label>Completed</ion-label>
    <ion-badge color="success">80</ion-badge>
  </ion-item>
  <ion-item>
    <ion-label>Warnings</ion-label>
    <ion-badge color="warning">70</ion-badge>
  </ion-item>
  <ion-item>
    <ion-label>Notifications</ion-label>
    <ion-badge color="danger">1000</ion-badge>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonBadge, IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBadge, IonItem, IonLabel, IonList],
})
export class ExampleComponent {}
```

### CSS Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-label>Badges styled</ion-label>
    <ion-badge>1</ion-badge>
  </ion-item>
</ion-list>
```

```css
ion-badge {
  --background: purple;
  --color: white;
  --padding-end: 20px;
  --padding-start: 20px;
}
```

```ts
import { Component } from '@angular/core';
import { IonBadge, IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonBadge, IonItem, IonLabel, IonList],
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

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the badge |
| `--color` | Text color of the badge |
| `--padding-bottom` | Bottom padding of the badge |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the badge |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the badge |
| `--padding-top` | Top padding of the badge |

| Name | Description |
| --- | --- |
| `--background` | Background of the badge |
| `--color` | Text color of the badge |
| `--padding-bottom` | Bottom padding of the badge |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the badge |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the badge |
| `--padding-top` | Top padding of the badge |

## Slots

No slots available for this component.
