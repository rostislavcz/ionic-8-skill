# Ionic Label Component

Source: https://ionicframework.com/docs/api/label

Sections: Basic Usage · Item Labels · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[scoped](https://ionicframework.com/docs/reference/glossary#scoped)

Label is an element used primarily to add text content to [Item](https://ionicframework.com/docs/api/item) components. Label can also be used inside of form control components such as [Input](https://ionicframework.com/docs/api/input) or [Radio](https://ionicframework.com/docs/api/radio) when specifying the visible label, but it is not required.

The position of the label inside of an item can be inline, fixed, stacked, or floating.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-label>Label</ion-label>
```

```ts
import { Component } from '@angular/core';
import { IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonLabel],
})
export class ExampleComponent {}
```

## Item Labels

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-label>Default Label</ion-label>
</ion-item>

<ion-item>
  <ion-label>
    Multi-line text that should ellipsis when it is too long to fit on one line. Lorem ipsum dolor sit amet, consectetur
    adipiscing elit.
  </ion-label>
</ion-item>

<ion-item>
  <ion-label class="ion-text-wrap">
    Multi-line text that should wrap when it is too long to fit on one line. Lorem ipsum dolor sit amet, consectetur
    adipiscing elit.
  </ion-label>
</ion-item>

<ion-item>
  <ion-label>
    <h1>Heading</h1>
    <p>Paragraph</p>
  </ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-label>Default</ion-label>
<ion-label color="primary">Primary</ion-label>
<ion-label color="secondary">Secondary</ion-label>
<ion-label color="tertiary">Tertiary</ion-label>
<ion-label color="success">Success</ion-label>
<ion-label color="warning">Warning</ion-label>
<ion-label color="danger">Danger</ion-label>
<ion-label color="light">Light</ion-label>
<ion-label color="medium">Medium</ion-label>
<ion-label color="dark">Dark</ion-label>
```

```ts
import { Component } from '@angular/core';
import { IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonLabel],
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

### position

|     |     |
| --- | --- |
| **Description** | The position determines where and how the label behaves inside an item. |
| **Attribute** | `position` |
| **Type** | `"fixed" ｜ "floating" ｜ "stacked" ｜ undefined` |
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
| `--color` | Color of the label. This property is only available when using `ion-label` inside of an `ion-item`. |

| Name | Description |
| --- | --- |
| `--color` | Color of the label. This property is only available when using `ion-label` inside of an `ion-item`. |

## Slots

No slots available for this component.
