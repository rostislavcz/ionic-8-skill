# Ionic Button Guide

Source: https://ionicframework.com/docs/api/button

Sections: Basic Usage · Expand · Shape · Fill · Size · Icons · Theming · Accessibility · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Buttons provide a clickable element, which can be used in forms, or anywhere that needs simple, standard button functionality. They may display text, icons, or both. Buttons can be styled with several attributes to look a specific way.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button>Default</ion-button> <ion-button [disabled]="true">Disabled</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

## Expand

This property lets you specify how wide the button should be. By default, buttons have `display: inline-block`, but setting this property will change the button to a full-width element with `display: block`.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button expand="block">Block</ion-button> <ion-button expand="full">Full</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

## Shape

This property lets you specify the shape of the button. By default, buttons are rectangular with a small border radius, but setting this to `"round"` will change the button to a rounded element.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button>Default</ion-button>
<ion-button shape="round">Round</ion-button>
<ion-button>
  <ion-icon slot="icon-only" name="heart"></ion-icon>
</ion-button>
<ion-button shape="round">
  <ion-icon slot="icon-only" name="heart"></ion-icon>
</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { heart } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ heart });
  }
}
```

## Fill

This property determines the background and border color of the button. By default, buttons have a solid background unless the button is inside of a toolbar, in which case it has a transparent background.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button>Default</ion-button>
<ion-button fill="clear">Clear</ion-button>
<ion-button fill="outline">Outline</ion-button>
<ion-button fill="solid">Solid</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

## Size

This property specifies the size of the button. Setting this property will change the height and padding of a button.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button size="small">Small</ion-button>
<ion-button size="default">Default</ion-button>
<ion-button size="large">Large</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

## Icons

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button size="small">
  <ion-icon slot="icon-only" ios="logo-apple" md="settings-sharp"></ion-icon>
</ion-button>

<ion-button>
  <ion-icon slot="icon-only" ios="logo-apple" md="settings-sharp"></ion-icon>
</ion-button>

<ion-button size="large">
  <ion-icon slot="icon-only" ios="logo-apple" md="settings-sharp"></ion-icon>
</ion-button>

<ion-button size="small">
  <ion-icon slot="start" name="star"></ion-icon>
  Left Icon
</ion-button>

<ion-button>
  <ion-icon slot="start" name="star"></ion-icon>
  Left Icon
</ion-button>

<ion-button size="large">
  <ion-icon slot="start" name="star"></ion-icon>
  Left Icon
</ion-button>

<ion-button size="small">
  Right Icon
  <ion-icon slot="end" name="heart"></ion-icon>
</ion-button>

<ion-button>
  Right Icon
  <ion-icon slot="end" name="heart"></ion-icon>
</ion-button>

<ion-button size="large">
  Right Icon
  <ion-icon slot="end" name="heart"></ion-icon>
</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonIcon } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { heart, logoApple, settingsSharp, star } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonIcon],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ heart, logoApple, settingsSharp, star });
  }
}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button>Default</ion-button>
<ion-button color="primary">Primary</ion-button>
<ion-button color="secondary">Secondary</ion-button>
<ion-button color="tertiary">Tertiary</ion-button>
<ion-button color="success">Success</ion-button>
<ion-button color="warning">Warning</ion-button>
<ion-button color="danger">Danger</ion-button>
<ion-button color="light">Light</ion-button>
<ion-button color="medium">Medium</ion-button>
<ion-button color="dark">Dark</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-button>Custom Button</ion-button>
```

```css
ion-button {
  --background: #93e9be;
  --background-hover: #9ce0be;
  --background-activated: #88f4be;
  --background-focused: #88f4be;

  --color: blue;

  --border-radius: 0;
  --border-color: #000;
  --border-style: solid;
  --border-width: 1px;

  --box-shadow: 0 2px 6px 0 rgb(0, 0, 0, 0.25);

  --ripple-color: deeppink;

  --padding-top: 10px;
  --padding-bottom: 10px;
}
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

## Accessibility

Buttons are built to be accessible, but may need some adjustments depending on their content. The button component renders a native [button element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) which allows it to take advantage of the functionality that a native button provides.

### Overflowing Text Content

There are many cases where a button's text content may overflow the container. It is recommended to wrap the text inside of the button when this happens so that all of the text can still be read. The button component will automatically adjust its height to accommodate the extra lines of text.

The button text does not automatically wrap to the next line when the text is too long to fit. In order to make the text wrap, the `ion-text-wrap` class can be added, which will set the `white-space` property to `"normal"`. This will become the default in a future major release.

info

The `max-width` style is set on the button below for demo purposes only. Text wrapping will work with a dynamic button width.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button>Default</ion-button>
<ion-button class="ion-text-wrap" style="max-width: 400px"
  >This is the button that never ends it just goes on and on and on and on and on and on and on and on my
  friends</ion-button
>
```

```ts
import { Component } from '@angular/core';
import { IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton],
})
export class ExampleComponent {}
```

## Properties

### buttonType

|     |     |
| --- | --- |
| **Description** | The type of button. |
| **Attribute** | `button-type` |
| **Type** | `string` |
| **Default** | `'button'` |

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
| **Description** | If `true`, the user cannot interact with the button. |
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

### expand

|     |     |
| --- | --- |
| **Description** | Set to `"block"` for a full-width button or to `"full"` for a full-width button with square corners and no left or right borders. |
| **Attribute** | `expand` |
| **Type** | `"block" ｜ "full" ｜ undefined` |
| **Default** | `undefined` |

### fill

|     |     |
| --- | --- |
| **Description** | Set to `"clear"` for a transparent button that resembles a flat button, to `"outline"` for a transparent button with a border, or to `"solid"` for a button with a filled background. The default fill is `"solid"` except inside of a toolbar, where the default is `"clear"`. |
| **Attribute** | `fill` |
| **Type** | `"clear" ｜ "default" ｜ "outline" ｜ "solid" ｜ undefined` |
| **Default** | `undefined` |

### form

|     |     |
| --- | --- |
| **Description** | The HTML form element or form element id. Used to submit a form when the button is not a child of the form.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `form` |
| **Type** | `HTMLFormElement ｜ string ｜ undefined` |
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

### shape

|     |     |
| --- | --- |
| **Description** | Set to `"round"` for a button with more rounded corners. |
| **Attribute** | `shape` |
| **Type** | `"round" ｜ undefined` |
| **Default** | `undefined` |

### size

|     |     |
| --- | --- |
| **Description** | Set to `"small"` for a button with less height and padding, to `"default"` for a button with the default height and padding, or to `"large"` for a button with more height and padding. By default the size is unset, unless the button is inside of an item, where the size is `"small"` by default. Set the size to `"default"` inside of an item to make it a standard size button. |
| **Attribute** | `size` |
| **Type** | `"default" ｜ "large" ｜ "small" ｜ undefined` |
| **Default** | `undefined` |

### strong

|     |     |
| --- | --- |
| **Description** | If `true`, activates a button with a heavier font weight. |
| **Attribute** | `strong` |
| **Type** | `boolean` |
| **Default** | `false` |

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
| **Description** | The type of the button. |
| **Attribute** | `type` |
| **Type** | `"button" ｜ "reset" ｜ "submit"` |
| **Default** | `'button'` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionBlur` | Emitted when the button loses focus. | `true` |
| `ionFocus` | Emitted when the button has focus. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `native` | The native HTML button or anchor element that wraps all child elements. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the button |
| `--background-activated` | Background of the button when pressed. Note: setting this will interfere with the Material Design ripple. |
| `--background-activated-opacity` | Opacity of the button when pressed |
| `--background-focused` | Background of the button when focused with the tab key |
| `--background-focused-opacity` | Opacity of the button when focused with the tab key |
| `--background-hover` | Background of the button on hover |
| `--background-hover-opacity` | Opacity of the background on hover |
| `--border-color` | Border color of the button |
| `--border-radius` | Border radius of the button |
| `--border-style` | Border style of the button |
| `--border-width` | Border width of the button |
| `--box-shadow` | Box shadow of the button |
| `--color` | Text color of the button |
| `--color-activated` | Text color of the button when pressed |
| `--color-focused` | Text color of the button when focused with the tab key |
| `--color-hover` | Text color of the button when hover |
| `--opacity` | Opacity of the button |
| `--padding-bottom` | Bottom padding of the button |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the button |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the button |
| `--padding-top` | Top padding of the button |
| `--ripple-color` | Color of the button ripple effect |
| `--transition` | Transition of the button |

| Name | Description |
| --- | --- |
| `--background` | Background of the button |
| `--background-activated` | Background of the button when pressed. Note: setting this will interfere with the Material Design ripple. |
| `--background-activated-opacity` | Opacity of the button when pressed |
| `--background-focused` | Background of the button when focused with the tab key |
| `--background-focused-opacity` | Opacity of the button when focused with the tab key |
| `--background-hover` | Background of the button on hover |
| `--background-hover-opacity` | Opacity of the background on hover |
| `--border-color` | Border color of the button |
| `--border-radius` | Border radius of the button |
| `--border-style` | Border style of the button |
| `--border-width` | Border width of the button |
| `--box-shadow` | Box shadow of the button |
| `--color` | Text color of the button |
| `--color-activated` | Text color of the button when pressed |
| `--color-focused` | Text color of the button when focused with the tab key |
| `--color-hover` | Text color of the button when hover |
| `--opacity` | Opacity of the button |
| `--padding-bottom` | Bottom padding of the button |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the button |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the button |
| `--padding-top` | Top padding of the button |
| `--ripple-color` | Color of the button ripple effect |
| `--transition` | Transition of the button |

## Slots

| Name | Description |
| --- | --- |
| \`\` | Content is placed between the named slots if provided without a slot. |
| `end` | Content is placed to the right of the button text in LTR, and to the left in RTL. |
| `icon-only` | Should be used on an icon in a button that has no text. |
| `start` | Content is placed to the left of the button text in LTR, and to the right in RTL. |
