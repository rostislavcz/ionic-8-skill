# Ionic List Headers

Source: https://ionicframework.com/docs/api/list-header

Sections: Basic Usage · Buttons in List Headers · List Header Lines · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

List headers are block elements that are used to describe the contents of a [list](https://ionicframework.com/docs/api/list). Unlike [item dividers](https://ionicframework.com/docs/api/item-divider), list headers should only be used once at the top of a list of [items](https://ionicframework.com/docs/api/item).

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-list-header>
    <ion-label>Video Games</ion-label>
  </ion-list-header>
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
import { IonItem, IonLabel, IonList, IonListHeader } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonListHeader],
})
export class ExampleComponent {}
```

## Buttons in List Headers

A [button](https://ionicframework.com/docs/api/button) placed in a list header can be useful for showing part of a list and redirecting to the full list with the button.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-list-header>
    <ion-label>Video Games</ion-label>
    <ion-button>See All</ion-button>
  </ion-list-header>
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
import { IonButton, IonItem, IonLabel, IonList, IonListHeader } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonItem, IonLabel, IonList, IonListHeader],
})
export class ExampleComponent {}
```

## List Header Lines

List headers do not show a bottom border by default. The `lines` property can be modified to `"full"` or `"inset"` which will show a full width border or an inset border with left padding, respectively.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-list-header>
    <ion-label>Default</ion-label>
  </ion-list-header>
  <ion-item>
    <ion-label>Item</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Item</ion-label>
  </ion-item>
</ion-list>

<ion-list>
  <ion-list-header lines="inset">
    <ion-label>Inset</ion-label>
  </ion-list-header>
  <ion-item>
    <ion-label>Item</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Item</ion-label>
  </ion-item>
</ion-list>

<ion-list>
  <ion-list-header lines="full">
    <ion-label>Full</ion-label>
  </ion-list-header>
  <ion-item>
    <ion-label>Item</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Item</ion-label>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel, IonList, IonListHeader } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonList, IonListHeader],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list-header>
  <ion-label>Default</ion-label>
</ion-list-header>
<ion-list-header color="primary">
  <ion-label>Primary</ion-label>
</ion-list-header>
<ion-list-header color="secondary">
  <ion-label>Secondary</ion-label>
</ion-list-header>
<ion-list-header color="tertiary">
  <ion-label>Tertiary</ion-label>
</ion-list-header>
<ion-list-header color="success">
  <ion-label>Success</ion-label>
</ion-list-header>
<ion-list-header color="warning">
  <ion-label>Warning</ion-label>
</ion-list-header>
<ion-list-header color="danger">
  <ion-label>Danger</ion-label>
</ion-list-header>
<ion-list-header color="light">
  <ion-label>Light</ion-label>
</ion-list-header>
<ion-list-header color="medium">
  <ion-label>Medium</ion-label>
</ion-list-header>
<ion-list-header color="dark">
  <ion-label>Dark</ion-label>
</ion-list-header>
```

```ts
import { Component } from '@angular/core';
import { IonLabel, IonListHeader } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonLabel, IonListHeader],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-list-header>
  <ion-label>Custom List Header</ion-label>
</ion-list-header>
```

```css
ion-list-header {
  --background: #19422d;
  --color: #fff;

  --border-width: 0 0 4px 0;
  --border-color: #f24aec;
  --border-style: double;
}
```

```ts
import { Component } from '@angular/core';
import { IonLabel, IonListHeader } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonLabel, IonListHeader],
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

### lines

|     |     |
| --- | --- |
| **Description** | How the bottom border should be displayed on the list header. |
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

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `inner` | The inner wrapper element that arranges the list header content. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the list header |
| `--border-color` | Color of the list header border |
| `--border-style` | Style of the list header border |
| `--border-width` | Width of the list header border |
| `--color` | Color of the list header text |
| `--inner-border-width` | Width of the inner list header border |

| Name | Description |
| --- | --- |
| `--background` | Background of the list header |
| `--border-color` | Color of the list header border |
| `--border-style` | Style of the list header border |
| `--border-width` | Width of the list header border |
| `--color` | Color of the list header text |
| `--inner-border-width` | Width of the inner list header border |

## Slots

No slots available for this component.
