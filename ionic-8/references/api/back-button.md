# Ionic Back Button

Source: https://ionicframework.com/docs/api/back-button

Sections: Basic Usage · Custom Back Button · Default Back History · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The back button navigates back in the app's history when clicked. It is only displayed when there is history in the navigation stack, unless [`defaultHref`](https://ionicframework.com/docs/api/back-button#default-back-history) is set. The back button displays different text and icon based on the mode, but this can be customized.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts
- src/app/page-one.component.ts
- src/app/page-two.component.ts

```html
<ion-nav [root]="component"></ion-nav>
```

```ts
import { Component } from '@angular/core';
import { IonNav } from '@ionic/angular/standalone';

import { PageOneComponent } from './page-one.component';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonNav],
})
export class ExampleComponent {
  component = PageOneComponent;
}
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonContent, IonHeader, IonNavLink, IonTitle, IonToolbar } from '@ionic/angular/standalone';

import { PageTwoComponent } from './page-two.component';

@Component({
  selector: 'app-page-one',
  template: `
    <ion-header>
      <ion-toolbar>
        <ion-title>Back Button</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page One</h1>
      <p>Navigate to the next page to see the back button.</p>
      <ion-nav-link router-direction="forward" [component]="component">
        <ion-button>Navigate</ion-button>
      </ion-nav-link>
    </ion-content>
  `,
  imports: [IonButton, IonContent, IonHeader, IonNavLink, IonTitle, IonToolbar],
})
export class PageOneComponent {
  component = PageTwoComponent;
}
```

```ts
import { Component } from '@angular/core';
import { IonBackButton, IonButtons, IonContent, IonHeader, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-page-two',
  template: `
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button></ion-back-button>
        </ion-buttons>
        <ion-title>Back Button</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page Two</h1>
      <p>Use the back button to navigate to the previous page.</p>
    </ion-content>
  `,
  imports: [IonBackButton, IonButtons, IonContent, IonHeader, IonTitle, IonToolbar],
})
export class PageTwoComponent {}
```

## Custom Back Button

By default, the back button will display the text `"Back"` with a `"chevron-back"` icon on `ios`, and an `"arrow-back-sharp"` icon on `md`. This can be customized per back button component by setting the `icon` or `text` properties. Alternatively, it can be set globally using the `backButtonIcon` or `backButtonText` properties in the global config. See the [Config docs](https://ionicframework.com/docs/developing/config) for more information.

- src/app/example.component.html
- src/app/example.component.ts
- src/app/page-one.component.ts
- src/app/page-two.component.ts

```html
<ion-nav [root]="component"></ion-nav>
```

```ts
import { Component } from '@angular/core';
import { IonNav } from '@ionic/angular/standalone';

import { PageOneComponent } from './page-one.component';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonNav],
})
export class ExampleComponent {
  component = PageOneComponent;
}
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonContent, IonHeader, IonNavLink, IonTitle, IonToolbar } from '@ionic/angular/standalone';

import { PageTwoComponent } from './page-two.component';

@Component({
  selector: 'app-page-one',
  template: `
    <ion-header>
      <ion-toolbar>
        <ion-title>Back Button</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page One</h1>
      <p>Navigate to the next page to see the back button.</p>
      <ion-nav-link router-direction="forward" [component]="component">
        <ion-button>Navigate</ion-button>
      </ion-nav-link>
    </ion-content>
  `,
  imports: [IonButton, IonContent, IonHeader, IonNavLink, IonTitle, IonToolbar],
})
export class PageOneComponent {
  component = PageTwoComponent;
}
```

```ts
import { Component } from '@angular/core';
import { IonBackButton, IonButtons, IonContent, IonHeader, IonTitle, IonToolbar } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { caretBack } from 'ionicons/icons';

@Component({
  selector: 'app-page-two',
  template: `
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button text="Previous" icon="caret-back"></ion-back-button>
        </ion-buttons>
        <ion-title>Back Button</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page Two</h1>
      <p>Use the back button to navigate to the previous page.</p>
    </ion-content>
  `,
  imports: [IonBackButton, IonButtons, IonContent, IonHeader, IonTitle, IonToolbar],
})
export class PageTwoComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ caretBack });
  }
}
```

## Default Back History

Occasionally an app may need to show the back button and navigate back when there is no history. This can be done by setting the `defaultHref` on the back button to a path. In order to use `defaultHref`, the app must contain a router with paths set.

## Properties

### color

|     |     |
| --- | --- |
| **Description** | The color to use from your application's color palette. Default options are: `"primary"`, `"secondary"`, `"tertiary"`, `"success"`, `"warning"`, `"danger"`, `"light"`, `"medium"`, and `"dark"`. For more information on colors, see [theming](https://ionicframework.com/docs/theming/basics). |
| **Attribute** | `color` |
| **Type** | `"danger" ｜ "dark" ｜ "light" ｜ "medium" ｜ "primary" ｜ "secondary" ｜ "success" ｜ "tertiary" ｜ "warning" ｜ string ｜ undefined` |
| **Default** | `undefined` |

### defaultHref

|     |     |
| --- | --- |
| **Description** | The url to navigate back to by default when there is no history. |
| **Attribute** | `default-href` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the user cannot interact with the button. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### icon

|     |     |
| --- | --- |
| **Description** | The built-in named SVG icon name or the exact `src` of an SVG file to use for the back button. |
| **Attribute** | `icon` |
| **Type** | `null ｜ string ｜ undefined` |
| **Default** | `undefined` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

### routerAnimation

|     |     |
| --- | --- |
| **Description** | When using a router, it specifies the transition animation when navigating to another page. |
| **Attribute** | `undefined` |
| **Type** | `((baseEl: any, opts?: any) => Animation) ｜ undefined` |
| **Default** | `undefined` |

### text

|     |     |
| --- | --- |
| **Description** | The text to display in the back button. |
| **Attribute** | `text` |
| **Type** | `null ｜ string ｜ undefined` |
| **Default** | `undefined` |

### type

|     |     |
| --- | --- |
| **Description** | The type of the button. |
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
| `icon` | The back button icon (uses ion-icon). |
| `native` | The native HTML button element that wraps all child elements. |
| `text` | The back button text. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the button |
| `--background-focused` | Background of the button when focused with the tab key |
| `--background-focused-opacity` | Opacity of the button background when focused with the tab key |
| `--background-hover` | Background of the button on hover |
| `--background-hover-opacity` | Opacity of the background on hover |
| `--border-radius` | Border radius of the button |
| `--color` | Text color of the button |
| `--color-focused` | Text color of the button when focused with the tab key |
| `--color-hover` | Text color of the button on hover |
| `--icon-font-size` | Font size of the button icon |
| `--icon-font-weight` | Font weight of the button icon |
| `--icon-margin-bottom` | Bottom margin of the button icon |
| `--icon-margin-end` | Right margin if direction is left-to-right, and left margin if direction is right-to-left of the button icon |
| `--icon-margin-start` | Left margin if direction is left-to-right, and right margin if direction is right-to-left of the button icon |
| `--icon-margin-top` | Top margin of the button icon |
| `--icon-padding-bottom` | Bottom padding of the button icon |
| `--icon-padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the button icon |
| `--icon-padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the button icon |
| `--icon-padding-top` | Top padding of the button icon |
| `--margin-bottom` | Bottom margin of the button |
| `--margin-end` | Right margin if direction is left-to-right, and left margin if direction is right-to-left of the button |
| `--margin-start` | Left margin if direction is left-to-right, and right margin if direction is right-to-left of the button |
| `--margin-top` | Top margin of the button |
| `--min-height` | Minimum height of the button |
| `--min-width` | Minimum width of the button |
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
| `--background-focused` | Background of the button when focused with the tab key |
| `--background-focused-opacity` | Opacity of the button background when focused with the tab key |
| `--background-hover` | Background of the button on hover |
| `--background-hover-opacity` | Opacity of the background on hover |
| `--border-radius` | Border radius of the button |
| `--color` | Text color of the button |
| `--color-focused` | Text color of the button when focused with the tab key |
| `--color-hover` | Text color of the button on hover |
| `--icon-font-size` | Font size of the button icon |
| `--icon-font-weight` | Font weight of the button icon |
| `--icon-margin-bottom` | Bottom margin of the button icon |
| `--icon-margin-end` | Right margin if direction is left-to-right, and left margin if direction is right-to-left of the button icon |
| `--icon-margin-start` | Left margin if direction is left-to-right, and right margin if direction is right-to-left of the button icon |
| `--icon-margin-top` | Top margin of the button icon |
| `--icon-padding-bottom` | Bottom padding of the button icon |
| `--icon-padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the button icon |
| `--icon-padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the button icon |
| `--icon-padding-top` | Top padding of the button icon |
| `--margin-bottom` | Bottom margin of the button |
| `--margin-end` | Right margin if direction is left-to-right, and left margin if direction is right-to-left of the button |
| `--margin-start` | Left margin if direction is left-to-right, and right margin if direction is right-to-left of the button |
| `--margin-top` | Top margin of the button |
| `--min-height` | Minimum height of the button |
| `--min-width` | Minimum width of the button |
| `--opacity` | Opacity of the button |
| `--padding-bottom` | Bottom padding of the button |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the button |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the button |
| `--padding-top` | Top padding of the button |
| `--ripple-color` | Color of the button ripple effect |
| `--transition` | Transition of the button |

## Slots

No slots available for this component.
