# Ionic Note Component

Source: https://ionicframework.com/docs/api/note

Sections: Basic Usage · Item Notes · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Notes are text elements generally used as subtitles that provide more information. They are styled to appear grey by default. Notes can be used in an item as metadata text.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-note>Default Note</ion-note>
```

```ts
import { Component } from '@angular/core';
import { IonNote } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonNote],
})
export class ExampleComponent {}
```

## Item Notes

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-label>Label</ion-label>
  <ion-note slot="end">Note (End)</ion-note>
</ion-item>

<ion-item>
  <ion-note slot="start">Note (Start)</ion-note>
  <ion-label>Label</ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel, IonNote } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel, IonNote],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-note>Default Note</ion-note>
<ion-note color="primary">Primary Note</ion-note>
<ion-note color="secondary">Secondary Note</ion-note>
<ion-note color="tertiary">Tertiary Note</ion-note>
<ion-note color="success">Success Note</ion-note>
<ion-note color="warning">Warning Note</ion-note>
<ion-note color="danger">Danger Note</ion-note>
<ion-note color="light">Light Note</ion-note>
<ion-note color="medium">Medium Note</ion-note>
<ion-note color="dark">Dark Note</ion-note>
```

```ts
import { Component } from '@angular/core';
import { IonNote } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonNote],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-note>Default Note</ion-note>
```

```css
ion-note {
  --color: #54dc98;
}
```

```ts
import { Component } from '@angular/core';
import { IonNote } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonNote],
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
| `--color` | Color of the note |

| Name | Description |
| --- | --- |
| `--color` | Color of the note |

## Slots

No slots available for this component.
