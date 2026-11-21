# Ionic Item Dividers

Source: https://ionicframework.com/docs/api/item-divider

Sections: Basic Usage · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Item dividers are block elements that can be used to separate [items](https://ionicframework.com/docs/api/item) in a list. They are similar to list headers, but instead of only being placed at the top of a list, they should go in between groups of items.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item-group>
    <ion-item-divider>
      <ion-label> Section A </ion-label>
    </ion-item-divider>

    <ion-item>
      <ion-label>A1</ion-label>
    </ion-item>
    <ion-item>
      <ion-label>A2</ion-label>
    </ion-item>
    <ion-item lines="none">
      <ion-label>A3</ion-label>
    </ion-item>
  </ion-item-group>

  <ion-item-group>
    <ion-item-divider>
      <ion-label> Section B </ion-label>
    </ion-item-divider>

    <ion-item>
      <ion-label>B1</ion-label>
    </ion-item>
    <ion-item>
      <ion-label>B2</ion-label>
    </ion-item>
    <ion-item lines="none">
      <ion-label>B3</ion-label>
    </ion-item>
  </ion-item-group>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonItemDivider, IonItemGroup, IonLabel, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonItemDivider, IonItemGroup, IonLabel, IonList],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item-divider>
  <ion-label>Default</ion-label>
</ion-item-divider>
<ion-item-divider color="primary">
  <ion-label>Primary</ion-label>
</ion-item-divider>
<ion-item-divider color="secondary">
  <ion-label>Secondary</ion-label>
</ion-item-divider>
<ion-item-divider color="tertiary">
  <ion-label>Tertiary</ion-label>
</ion-item-divider>
<ion-item-divider color="success">
  <ion-label>Success</ion-label>
</ion-item-divider>
<ion-item-divider color="warning">
  <ion-label>Warning</ion-label>
</ion-item-divider>
<ion-item-divider color="danger">
  <ion-label>Danger</ion-label>
</ion-item-divider>
<ion-item-divider color="light">
  <ion-label>Light</ion-label>
</ion-item-divider>
<ion-item-divider color="medium">
  <ion-label>Medium</ion-label>
</ion-item-divider>
<ion-item-divider color="dark">
  <ion-label>Dark</ion-label>
</ion-item-divider>
```

```ts
import { Component } from '@angular/core';
import { IonItemDivider, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItemDivider, IonLabel],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-item-divider>
  <ion-label> Item Divider </ion-label>
</ion-item-divider>
```

```css
ion-item-divider {
  --background: #19422d;
  --color: #fff;

  --padding-top: 10px;
  --padding-bottom: 10px;
  --padding-start: 20px;
  --padding-end: 20px;
}
```

```ts
import { Component } from '@angular/core';
import { IonItemDivider, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItemDivider, IonLabel],
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

### sticky

|     |     |
| --- | --- |
| **Description** | When it's set to `true`, the item-divider will stay visible when it reaches the top of the viewport until the next `ion-item-divider` replaces it.<br>This feature relies in `position:sticky`: [https://caniuse.com/#feat=css-sticky](https://caniuse.com/#feat=css-sticky) |
| **Attribute** | `sticky` |
| **Type** | `boolean` |
| **Default** | `false` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `container` | The wrapper element that contains the default slot. |
| `inner` | The inner wrapper element that arranges the divider content. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the item divider |
| `--color` | Color of the item divider |
| `--inner-padding-bottom` | Bottom inner padding of the item divider |
| `--inner-padding-end` | End inner padding of the item divider |
| `--inner-padding-start` | Start inner padding of the item divider |
| `--inner-padding-top` | Top inner padding of the item divider |
| `--padding-bottom` | Bottom padding of the item divider |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the item divider |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the item divider |
| `--padding-top` | Top padding of the item divider |

| Name | Description |
| --- | --- |
| `--background` | Background of the item divider |
| `--color` | Color of the item divider |
| `--inner-padding-bottom` | Bottom inner padding of the item divider |
| `--inner-padding-end` | End inner padding of the item divider |
| `--inner-padding-start` | Start inner padding of the item divider |
| `--inner-padding-top` | Top inner padding of the item divider |
| `--padding-bottom` | Bottom padding of the item divider |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the item divider |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the item divider |
| `--padding-top` | Top padding of the item divider |

## Slots

| Name | Description |
| --- | --- |
| \`\` | Content is placed between the named slots if provided without a slot. |
| `end` | Content is placed to the right of the divider text in LTR, and to the left in RTL. |
| `start` | Content is placed to the left of the divider text in LTR, and to the right in RTL. |
