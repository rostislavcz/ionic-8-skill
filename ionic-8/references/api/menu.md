# Ionic Menu Overview

Source: https://ionicframework.com/docs/api/menu

Sections: Basic Usage · Menu Toggle · Menu Types · Menu Sides · Multiple Menus · Theming · Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The menu component is a navigation drawer that slides in from the side of the current view. By default, it uses the start side, making it slide in from the left for LTR and right for RTL, but the side can be overridden. The menu will be displayed differently based on the mode, however the display type can be changed to any of the available menu types.

The menu element should be a sibling to the root content element. There can be any number of menus attached to the content. These can be controlled from the templates, or programmatically using the `MenuController`.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-menu contentId="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu Content</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">This is the menu content.</ion-content>
</ion-menu>
<div class="ion-page" id="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-menu-button></ion-menu-button>
      </ion-buttons>
      <ion-title>Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding"> Tap the button in the toolbar to open the menu. </ion-content>
</div>
```

```ts
import { Component } from '@angular/core';
import {
  IonButtons,
  IonContent,
  IonHeader,
  IonMenu,
  IonMenuButton,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButtons, IonContent, IonHeader, IonMenu, IonMenuButton, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Menu Toggle

The [menu toggle](https://ionicframework.com/docs/api/menu-toggle) component can be used to create custom button that can open or close the menu.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-menu contentId="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu Content</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-menu-toggle>
      <ion-button>Click to close the menu</ion-button>
    </ion-menu-toggle>
  </ion-content>
</ion-menu>
<div class="ion-page" id="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-menu-toggle>
      <ion-button>Click to open the menu</ion-button>
    </ion-menu-toggle>
  </ion-content>
</div>
```

```ts
import { Component } from '@angular/core';
import {
  IonButton,
  IonContent,
  IonHeader,
  IonMenu,
  IonMenuToggle,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonContent, IonHeader, IonMenu, IonMenuToggle, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Menu Types

The `type` property can be used to customize how menus display in your application.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-menu [type]="menuType" content-id="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu Content</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-menu-toggle>
      <ion-button>Click to close the menu</ion-button>
    </ion-menu-toggle>
  </ion-content>
</ion-menu>

<div class="ion-page" id="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <h2>Select an overlay type:</h2>
    <ion-radio-group [(ngModel)]="menuType">
      <ion-item>
        <ion-radio value="overlay">
          <code>overlay</code>
        </ion-radio>
      </ion-item>
      <ion-item>
        <ion-radio value="reveal">
          <code>reveal</code>
        </ion-radio>
      </ion-item>
      <ion-item>
        <ion-radio value="push">
          <code>push</code>
        </ion-radio>
      </ion-item>
    </ion-radio-group>
    <br />
    <ion-menu-toggle>
      <ion-button>Click to open the menu</ion-button>
    </ion-menu-toggle>
  </ion-content>
</div>
```

```ts
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import {
  IonButton,
  IonContent,
  IonHeader,
  IonItem,
  IonMenu,
  IonMenuToggle,
  IonRadio,
  IonRadioGroup,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [\
    FormsModule,\
    IonButton,\
    IonContent,\
    IonHeader,\
    IonItem,\
    IonMenu,\
    IonMenuToggle,\
    IonRadio,\
    IonRadioGroup,\
    IonTitle,\
    IonToolbar,\
  ],
})
export class ExampleComponent {
  menuType: string = 'overlay';
}
```

## Menu Sides

Menus are displayed on the `"start"` side by default. In apps that use left-to-right direction, this is the left side, and in right-to-left apps, this will be the right side. Menus can also be set to display on the `"end"` side, which is the opposite of `"start"`.

If menus on both sides are needed in an app, the menu can be opened by passing the `side` value to the `open` method on `MenuController`. If a side is not provided, the menu on the `"start"` side will be opened. See the [multiple menus](https://ionicframework.com/docs/api/menu#multiple-menus) section below for an example using `MenuController`.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-menu side="end" contentId="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu Content</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">This is the menu content.</ion-content>
</ion-menu>
<div class="ion-page" id="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu</ion-title>
      <ion-buttons slot="end">
        <ion-menu-button></ion-menu-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding"> Tap the button in the toolbar to open the menu. </ion-content>
</div>
```

```ts
import { Component } from '@angular/core';
import {
  IonButtons,
  IonContent,
  IonHeader,
  IonMenu,
  IonMenuButton,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButtons, IonContent, IonHeader, IonMenu, IonMenuButton, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Multiple Menus

When multiple menus exist on the same side, we need refer to them by ID instead of side. Otherwise, the wrong menu may be activated.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-menu menuId="first-menu" contentId="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>First Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">This is the first menu content.</ion-content>
</ion-menu>

<ion-menu menuId="second-menu" contentId="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Second Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">This is the second menu content.</ion-content>
</ion-menu>

<ion-menu side="end" contentId="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>End Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">This is the end menu content.</ion-content>
</ion-menu>

<div class="ion-page" id="main-content">
  <ion-header>
    <ion-toolbar>
      <ion-title>Menu</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <p>Tap a button below to open a specific menu.</p>

    <ion-button expand="block" (click)="openFirstMenu()">Open First Menu</ion-button>
    <ion-button expand="block" (click)="openSecondMenu()">Open Second Menu</ion-button>
    <ion-button expand="block" (click)="openEndMenu()">Open End Menu</ion-button>
  </ion-content>
</div>
```

```ts
import { Component } from '@angular/core';
import {
  IonButton,
  IonContent,
  IonHeader,
  IonMenu,
  IonTitle,
  IonToolbar,
  MenuController,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonContent, IonHeader, IonMenu, IonTitle, IonToolbar],
})
export class ExampleComponent {
  constructor(private menuCtrl: MenuController) {}

  openFirstMenu() {
    /**
     * Open the menu by menu-id
     * We refer to the menu using an ID
     * because multiple "start" menus exist.
     */
    this.menuCtrl.open('first-menu');
  }

  openSecondMenu() {
    /**
     * Open the menu by menu-id
     * We refer to the menu using an ID
     * because multiple "start" menus exist.
     */
    this.menuCtrl.open('second-menu');
  }

  openEndMenu() {
    /**
     * Open the menu by side
     * We can refer to the menu by side
     * here because only one "end" menu exists
     */
    this.menuCtrl.open('end');
  }
}
```

## Theming

### CSS Shadow Parts

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-app>
  <ion-menu contentId="main-content">
    <ion-header>
      <ion-toolbar color="tertiary">
        <ion-title>Menu Content</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">This is the menu content.</ion-content>
  </ion-menu>
  <div class="ion-page" id="main-content">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button></ion-menu-button>
        </ion-buttons>
        <ion-title>Menu</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding"> Tap the button in the toolbar to open the menu. </ion-content>
  </div>
</ion-app>
```

```css
ion-menu::part(backdrop) {
  background-color: rgba(255, 0, 255, 0.5);
}

ion-menu::part(container) {
  border-radius: 0 20px 20px 0;

  box-shadow: 4px 0px 16px rgba(255, 0, 255, 0.18);
}
```

```ts
import { Component } from '@angular/core';
import {
  IonApp,
  IonButtons,
  IonContent,
  IonHeader,
  IonMenu,
  IonMenuButton,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonApp, IonButtons, IonContent, IonHeader, IonMenu, IonMenuButton, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Interfaces

### MenuCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface MenuCustomEvent<T = any> extends CustomEvent {
  detail: T;
  target: HTMLIonMenuElement;
}
```

## Properties

### contentId

|     |     |
| --- | --- |
| **Description** | The `id` of the main content. When using a router this is typically `ion-router-outlet`. When not using a router, this is typically your main view's `ion-content`. This is not the id of the `ion-content` inside of your `ion-menu`. |
| **Attribute** | `content-id` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the menu is disabled. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### maxEdgeStart

|     |     |
| --- | --- |
| **Description** | The edge threshold for dragging the menu open. If a drag/swipe happens over this value, the menu is not triggered. |
| **Attribute** | `max-edge-start` |
| **Type** | `number` |
| **Default** | `50` |

### menuId

|     |     |
| --- | --- |
| **Description** | An id for the menu. |
| **Attribute** | `menu-id` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### side

|     |     |
| --- | --- |
| **Description** | Which side of the view the menu should be placed. |
| **Attribute** | `side` |
| **Type** | `"end" ｜ "start"` |
| **Default** | `'start'` |

### swipeGesture

|     |     |
| --- | --- |
| **Description** | If `true`, swiping the menu is enabled. |
| **Attribute** | `swipe-gesture` |
| **Type** | `boolean` |
| **Default** | `true` |

### type

|     |     |
| --- | --- |
| **Description** | The display type of the menu. Available options: `"overlay"`, `"reveal"`, `"push"`. |
| **Attribute** | `type` |
| **Type** | `"overlay" ｜ "push" ｜ "reveal" ｜ undefined` |
| **Default** | `undefined` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionDidClose` | Emitted when the menu is closed. | `true` |
| `ionDidOpen` | Emitted when the menu is open. | `true` |
| `ionWillClose` | Emitted when the menu is about to be closed. | `true` |
| `ionWillOpen` | Emitted when the menu is about to be opened. | `true` |

## Methods

### close

|     |     |
| --- | --- |
| **Description** | Closes the menu. If the menu is already closed or it can't be closed, it returns `false`. |
| **Signature** | `close(animated?: boolean, role?: string) => Promise<boolean>` |
| **Parameters** | **animated**: If `true`, the menu will animate when closing. If `false`, the menu will close instantly without animation. Defaults to `true`.<br>**role**: The role of the element that is closing the menu. This can be useful in a button handler for determining which button was clicked to close the menu. Some examples include: `"cancel"`, `"destructive"`, `"selected"`, and `"backdrop"`. |

### isActive

|     |     |
| --- | --- |
| **Description** | Returns `true` if the menu is active.<br>A menu is active when it can be opened or closed, meaning it's enabled and it's not part of a `ion-split-pane`. |
| **Signature** | `isActive() => Promise<boolean>` |

### isOpen

|     |     |
| --- | --- |
| **Description** | Returns `true` is the menu is open. |
| **Signature** | `isOpen() => Promise<boolean>` |

### open

|     |     |
| --- | --- |
| **Description** | Opens the menu. If the menu is already open or it can't be opened, it returns `false`. |
| **Signature** | `open(animated?: boolean) => Promise<boolean>` |
| **Parameters** | **animated**: If `true`, the menu will animate when opening. If `false`, the menu will open instantly without animation. Defaults to `true`. |

### setOpen

|     |     |
| --- | --- |
| **Description** | Opens or closes the menu. If the operation can't be completed successfully, it returns `false`. |
| **Signature** | `setOpen(shouldOpen: boolean, animated?: boolean, role?: string) => Promise<boolean>` |
| **Parameters** | **shouldOpen**: If `true`, the menu will open. If `false`, the menu will close.<br>**animated**: If `true`, the menu will animate when opening/closing. If `false`, the menu will open/close instantly without animation.<br>**role**: The role of the element that is closing the menu. |

### toggle

|     |     |
| --- | --- |
| **Description** | Toggles the menu. If the menu is already open, it will try to close, otherwise it will try to open it. If the operation can't be completed successfully, it returns `false`. |
| **Signature** | `toggle(animated?: boolean) => Promise<boolean>` |
| **Parameters** | **animated**: If `true`, the menu will animate when opening/closing. If `false`, the menu will open/close instantly without animation. Defaults to `true`. |

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `backdrop` | The backdrop that appears over the main content when the menu is open. |
| `container` | The container for the menu content. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the menu |
| `--height` | Height of the menu |
| `--max-height` | Maximum height of the menu |
| `--max-width` | Maximum width of the menu |
| `--min-height` | Minimum height of the menu |
| `--min-width` | Minimum width of the menu |
| `--width` | Width of the menu |

| Name | Description |
| --- | --- |
| `--background` | Background of the menu |
| `--height` | Height of the menu |
| `--max-height` | Maximum height of the menu |
| `--max-width` | Maximum width of the menu |
| `--min-height` | Minimum height of the menu |
| `--min-width` | Minimum width of the menu |
| `--width` | Width of the menu |

## Slots

No slots available for this component.
