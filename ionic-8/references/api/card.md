# Ionic Card Component

Source: https://ionicframework.com/docs/api/card

Sections: Basic Usage · Media Cards · Card Buttons · List Card · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Cards are containers that display content such as text, images, buttons, and lists.
A card can be a single component, but is often made up of a header, title, subtitle,
and content. Cards are broken up into several components to accommodate this structure:
[card header](https://ionicframework.com/docs/api/card-header), [card title](https://ionicframework.com/docs/api/card-title), [card subtitle](https://ionicframework.com/docs/api/card-subtitle),
and [card content](https://ionicframework.com/docs/api/card-content).

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-card>
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content>
    Here's a small text description for the card content. Nothing more, nothing less.
  </ion-card-content>
</ion-card>
```

```ts
import { Component } from '@angular/core';
import { IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle],
})
export class ExampleComponent {}
```

## Media Cards

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-card>
  <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/card-media.png" />
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content>
    Here's a small text description for the card content. Nothing more, nothing less.
  </ion-card-content>
</ion-card>
```

```ts
import { Component } from '@angular/core';
import { IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle],
})
export class ExampleComponent {}
```

## Card Buttons

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-card>
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content>
    Here's a small text description for the card content. Nothing more, nothing less.
  </ion-card-content>

  <ion-button fill="clear">Action 1</ion-button>
  <ion-button fill="clear">Action 2</ion-button>
</ion-card>
```

```ts
import { Component } from '@angular/core';
import {
  IonButton,
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardSubtitle,
  IonCardTitle,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle],
})
export class ExampleComponent {}
```

## List Card

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-card>
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>
  <ion-card-content>
    <ion-list>
      <ion-item>
        <ion-thumbnail slot="start">
          <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/thumbnail.svg" />
        </ion-thumbnail>
        <ion-label>Item</ion-label>
      </ion-item>

      <ion-item>
        <ion-thumbnail slot="start">
          <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/thumbnail.svg" />
        </ion-thumbnail>
        <ion-label>Item</ion-label>
      </ion-item>

      <ion-item>
        <ion-thumbnail slot="start">
          <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/thumbnail.svg" />
        </ion-thumbnail>
        <ion-label>Item</ion-label>
      </ion-item>

      <ion-item lines="none">
        <ion-thumbnail slot="start">
          <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/thumbnail.svg" />
        </ion-thumbnail>
        <ion-label>Item</ion-label>
      </ion-item>
    </ion-list>
  </ion-card-content>
</ion-card>
```

```css
ion-item {
  --padding-start: 0;
}
```

```ts
import { Component } from '@angular/core';
import {
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardSubtitle,
  IonCardTitle,
  IonItem,
  IonLabel,
  IonList,
  IonThumbnail,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [\
    IonCard,\
    IonCardContent,\
    IonCardHeader,\
    IonCardSubtitle,\
    IonCardTitle,\
    IonItem,\
    IonLabel,\
    IonList,\
    IonThumbnail,\
  ],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-card color="primary">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="secondary">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="tertiary">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="success">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="warning">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="danger">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="light">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="medium">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>

<ion-card color="dark">
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content> Card Content </ion-card-content>
</ion-card>
```

```ts
import { Component } from '@angular/core';
import { IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-card>
  <ion-card-header>
    <ion-card-title>Card Title</ion-card-title>
    <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
  </ion-card-header>

  <ion-card-content>
    Here's a small text description for the card content. Nothing more, nothing less.
  </ion-card-content>
</ion-card>
```

```css
ion-card {
  --background: #000;
  --color: #9efff0;
}

ion-card-title {
  --color: #52ffe4;
}

ion-card-subtitle {
  --color: #d1fff8;
}
```

```ts
import { Component } from '@angular/core';
import { IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle],
})
export class ExampleComponent {}
```

## Properties

### button

|     |     |
| --- | --- |
| **Description** | If `true`, a button tag will be rendered and the card will be tappable. |
| **Attribute** | `button` |
| **Type** | `boolean` |
| **Default** | `false` |

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
| **Description** | If `true`, the user cannot interact with the card. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### download

|     |     |
| --- | --- |
| **Description** | This attribute instructs browsers to download a URL instead of navigating to it, so the user will be prompted to save it as a local file. If the attribute has a value, it is used as the pre-filled file name in the Save prompt (the user can still change the file name if they want). |
| **Attribute** | `download` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### href

|     |     |
| --- | --- |
| **Description** | Contains a URL or a URL fragment that the hyperlink points to. If this property is set, an anchor tag will be rendered. |
| **Attribute** | `href` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

### rel

|     |     |
| --- | --- |
| **Description** | Specifies the relationship of the target object to the link object. The value is a space-separated list of [link types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types). |
| **Attribute** | `rel` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### routerAnimation

|     |     |
| --- | --- |
| **Description** | When using a router, it specifies the transition animation when navigating to another page using `href`. |
| **Attribute** | `undefined` |
| **Type** | `((baseEl: any, opts?: any) => Animation) ｜ undefined` |
| **Default** | `undefined` |

### routerDirection

|     |     |
| --- | --- |
| **Description** | When using a router, it specifies the transition direction when navigating to another page using `href`. |
| **Attribute** | `router-direction` |
| **Type** | `"back" ｜ "forward" ｜ "root"` |
| **Default** | `'forward'` |

### target

|     |     |
| --- | --- |
| **Description** | Specifies where to display the linked URL. Only applies when an `href` is provided. Special keywords: `"_blank"`, `"_self"`, `"_parent"`, `"_top"`. |
| **Attribute** | `target` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### type

|     |     |
| --- | --- |
| **Description** | The type of the button. Only used when an `onclick` or `button` property is present. |
| **Attribute** | `type` |
| **Type** | `"button" ｜ "reset" ｜ "submit"` |
| **Default** | `'button'` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `native` | The native HTML button, anchor, or div element that wraps all child elements. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the card |
| `--color` | Color of the card |

| Name | Description |
| --- | --- |
| `--background` | Background of the card |
| `--color` | Color of the card |

## Slots

No slots available for this component.
