# Ionic Chip Component

Source: https://ionicframework.com/docs/api/chip

Sections: Basic Usage · Slotting Components and Icons · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Chips represent complex entities in small blocks, such as a contact. A chip can contain several different elements such as avatars, text, and icons.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-chip>Default</ion-chip>
<ion-chip [disabled]="true">Disabled</ion-chip>
<ion-chip [outline]="true">Outline</ion-chip>
```

```ts
import { Component } from '@angular/core';
import { IonChip } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonChip],
})
export class ExampleComponent {}
```

## Slotting Components and Icons

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-chip>
  <ion-avatar>
    <img alt="Silhouette of a person's head" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
  </ion-avatar>
  <ion-label>Avatar Chip</ion-label>
  <ion-icon name="close-circle"></ion-icon>
</ion-chip>

<ion-chip>
  <ion-icon name="pin" color="primary"></ion-icon>
  <ion-label>Icon Chip</ion-label>
  <ion-icon name="close"></ion-icon>
</ion-chip>
```

```ts
import { Component } from '@angular/core';
import { IonAvatar, IonChip, IonIcon, IonLabel } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { close, closeCircle, pin } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonChip, IonIcon, IonLabel],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ close, closeCircle, pin });
  }
}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-chip>Default</ion-chip>
<ion-chip color="primary">Primary</ion-chip>
<ion-chip color="secondary">Secondary</ion-chip>
<ion-chip color="tertiary">Tertiary</ion-chip>
<ion-chip color="success">Success</ion-chip>
<ion-chip color="warning">Warning</ion-chip>
<ion-chip color="danger">Danger</ion-chip>
<ion-chip color="light">Light</ion-chip>
<ion-chip color="medium">Medium</ion-chip>
<ion-chip color="dark">Dark</ion-chip>
```

```ts
import { Component } from '@angular/core';
import { IonChip } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonChip],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-chip>Default</ion-chip>
```

```css
ion-chip {
  --background: #00213f;
  --color: #adefd1;
}
```

```ts
import { Component } from '@angular/core';
import { IonChip } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonChip],
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

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the user cannot interact with the chip. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

### outline

|     |     |
| --- | --- |
| **Description** | Display an outline style button. |
| **Attribute** | `outline` |
| **Type** | `boolean` |
| **Default** | `false` |

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
| `--background` | Background of the chip |
| `--color` | Color of the chip |

| Name | Description |
| --- | --- |
| `--background` | Background of the chip |
| `--color` | Color of the chip |

## Slots

No slots available for this component.
