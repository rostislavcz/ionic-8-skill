# Ionic Nav Component

Source: https://ionicframework.com/docs/api/nav

Sections: Using NavLink · Navigation within a Modal · Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Nav is a standalone component for loading arbitrary components and pushing new components on to the stack.

Unlike Router Outlet, Nav is not tied to a particular router. This means that if we load a Nav component, and push other components to the stack, they will not affect the app's overall router. For example, you should not push a new component to `ion-nav` and expect the URL to update. This fits use cases where you could have a modal, which needs its own sub-navigation, without making it tied to the apps URL.

note

`ion-nav` is not meant to be used for routing. Instead, see the routing guides for [Angular](https://ionicframework.com/docs/angular/navigation), [React](https://ionicframework.com/docs/react/navigation), and [Vue](https://ionicframework.com/docs/vue/navigation), or [`ion-router`](https://ionicframework.com/docs/api/router) for vanilla JavaScript projects.

## Using NavLink

NavLink is a simplified API when interacting with Nav. Developers can customize the component, pass along component properties, modify the direction of the route animation or define a custom animation when navigating.

- src/app/example.component.html
- src/app/example.component.ts
- src/app/page-one.component.ts
- src/app/page-two.component.ts
- src/app/page-three.component.ts

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
        <ion-title>Page One</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page One</h1>
      <ion-nav-link router-direction="forward" [component]="component">
        <ion-button>Go to Page Two</ion-button>
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
import {
  IonBackButton,
  IonButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonNavLink,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

import { PageThreeComponent } from './page-three.component';

@Component({
  selector: 'app-page-two',
  template: `
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button></ion-back-button>
        </ion-buttons>
        <ion-title>Page Two</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page Two</h1>
      <div>
        <ion-nav-link router-direction="forward" [component]="component">
          <ion-button>Go to Page Three</ion-button>
        </ion-nav-link>
      </div>
    </ion-content>
  `,
  imports: [IonBackButton, IonButton, IonButtons, IonContent, IonHeader, IonNavLink, IonTitle, IonToolbar],
})
export class PageTwoComponent {
  component = PageThreeComponent;
}
```

```ts
import { Component } from '@angular/core';
import { IonBackButton, IonButtons, IonContent, IonHeader, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-page-one',
  template: `
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button></ion-back-button>
        </ion-buttons>
        <ion-title>Page Three</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Page Three</h1>
    </ion-content>
  `,
  imports: [IonBackButton, IonButtons, IonContent, IonHeader, IonTitle, IonToolbar],
})
export class PageThreeComponent {}
```

## Navigation within a Modal

Modal can use Nav to offer a linear navigation that is independent of the URL.

note

The example below uses a reference to Nav and the public method APIs to push and pop views. It is recommended to use NavLink in implementations that do not require this level of granular access and control.

- src/app/example.component.html
- src/app/example.component.ts
- src/app/page-one.component.ts
- src/app/page-two.component.ts
- src/app/page-three.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Modal Navigation</ion-title>
  </ion-toolbar>
</ion-header>
<ion-content class="ion-padding">
  <ion-button id="openModal">Open Modal</ion-button>
  <ion-modal #modal trigger="openModal" (willPresent)="onWillPresent()">
    <ng-template>
      <ion-header>
        <ion-toolbar>
          <ion-title>Modal</ion-title>
          <ion-buttons slot="end">
            <ion-button (click)="modal.dismiss()"> Close </ion-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>
      <ion-content>
        <ion-nav #nav></ion-nav>
      </ion-content>
    </ng-template>
  </ion-modal>
</ion-content>
```

```ts
import { Component, ViewChild } from '@angular/core';
import {
  IonButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonModal,
  IonNav,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

import { PageOneComponent } from './page-one.component';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonButtons, IonContent, IonHeader, IonModal, IonNav, IonTitle, IonToolbar],
})
export class ExampleComponent {
  @ViewChild('nav') private nav!: IonNav;

  onWillPresent() {
    this.nav.setRoot(PageOneComponent);
  }
}
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonContent, IonNav } from '@ionic/angular/standalone';

import { PageTwoComponent } from './page-two.component';

@Component({
  selector: 'app-page-one',
  template: `
    <ion-content class="ion-padding">
      <h1>Page One</h1>
      <ion-button (click)="navigateToPageTwo()">Go to Page Two</ion-button>
    </ion-content>
  `,
  imports: [IonButton, IonContent],
})
export class PageOneComponent {
  constructor(private nav: IonNav) {}

  navigateToPageTwo() {
    this.nav.push(PageTwoComponent);
  }
}
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonContent, IonNav } from '@ionic/angular/standalone';

import { PageThreeComponent } from './page-three.component';

@Component({
  selector: 'app-page-two',
  template: `
    <ion-content class="ion-padding">
      <h1>Page Two</h1>
      <ion-button (click)="navigateToPageThree()">Go to Page Three</ion-button>
    </ion-content>
  `,
  imports: [IonButton, IonContent],
})
export class PageTwoComponent {
  component = PageThreeComponent;

  constructor(private nav: IonNav) {}

  navigateToPageThree() {
    this.nav.push(PageThreeComponent);
  }
}
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonContent, IonNav } from '@ionic/angular/standalone';

@Component({
  selector: 'app-page-one',
  template: `
    <ion-content class="ion-padding">
      <h1>Page Three</h1>
      <ion-button (click)="navigateBack()">Go Back</ion-button>
      <ion-button (click)="navigateToRoot()">Go to Root</ion-button>
    </ion-content>
  `,
  imports: [IonButton, IonContent],
})
export class PageThreeComponent {
  constructor(private nav: IonNav) {}

  navigateBack() {
    this.nav.pop();
  }

  navigateToRoot() {
    this.nav.popToRoot();
  }
}
```

## Interfaces

### NavCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface NavCustomEvent extends CustomEvent {
  target: HTMLIonNavElement;
}
```

## Properties

### animated

|     |     |
| --- | --- |
| **Description** | If `true`, the nav should animate the transition of components. |
| **Attribute** | `animated` |
| **Type** | `boolean` |
| **Default** | `true` |

### animation

|     |     |
| --- | --- |
| **Description** | By default `ion-nav` animates transition between pages based in the mode (ios or material design). However, this property allows to create custom transition using `AnimationBuilder` functions. |
| **Attribute** | `undefined` |
| **Type** | `((baseEl: any, opts?: any) => Animation) ｜ undefined` |
| **Default** | `undefined` |

### root

|     |     |
| --- | --- |
| **Description** | Root NavComponent to load |
| **Attribute** | `root` |
| **Type** | `Function ｜ HTMLElement ｜ ViewController ｜ null ｜ string ｜ undefined` |
| **Default** | `undefined` |

### rootParams

|     |     |
| --- | --- |
| **Description** | Any parameters for the root component |
| **Attribute** | `undefined` |
| **Type** | `T ｜ undefined` |
| **Default** | `undefined` |

### swipeGesture

|     |     |
| --- | --- |
| **Description** | If the nav component should allow for swipe-to-go-back. |
| **Attribute** | `swipe-gesture` |
| **Type** | `boolean ｜ undefined` |
| **Default** | `undefined` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionNavDidChange` | Event fired when the nav has changed components | `false` |
| `ionNavWillChange` | Event fired when the nav will change components | `false` |

## Methods

### canGoBack

|     |     |
| --- | --- |
| **Description** | Returns `true` if the current view can go back. |
| **Signature** | `canGoBack(view?: ViewController) => Promise<boolean>` |
| **Parameters** | **view**: The view to check. |

### getActive

|     |     |
| --- | --- |
| **Description** | Get the active view. |
| **Signature** | `getActive() => Promise<ViewController ｜ undefined>` |

### getByIndex

|     |     |
| --- | --- |
| **Description** | Get the view at the specified index. |
| **Signature** | `getByIndex(index: number) => Promise<ViewController ｜ undefined>` |
| **Parameters** | **index**: The index of the view. |

### getLength

|     |     |
| --- | --- |
| **Description** | Returns the number of views in the stack. |
| **Signature** | `getLength() => Promise<number>` |

### getPrevious

|     |     |
| --- | --- |
| **Description** | Get the previous view. |
| **Signature** | `getPrevious(view?: ViewController) => Promise<ViewController ｜ undefined>` |
| **Parameters** | **view**: The view to get. |

### insert

|     |     |
| --- | --- |
| **Description** | Inserts a component into the navigation stack at the specified index. This is useful to add a component at any point in the navigation stack. |
| **Signature** | `insert<T extends NavComponent>(insertIndex: number, component: T, componentProps?: ComponentProps<T> ｜ null, opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **insertIndex**: The index to insert the component at in the stack.<br>**component**: The component to insert into the navigation stack.<br>**componentProps**: Any properties of the component.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

### insertPages

|     |     |
| --- | --- |
| **Description** | Inserts an array of components into the navigation stack at the specified index. The last component in the array will become instantiated as a view, and animate in to become the active view. |
| **Signature** | `insertPages(insertIndex: number, insertComponents: NavComponent[] ｜ NavComponentWithProps[], opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **insertIndex**: The index to insert the components at in the stack.<br>**insertComponents**: The components to insert into the navigation stack.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

### pop

|     |     |
| --- | --- |
| **Description** | Pop a component off of the navigation stack. Navigates back from the current component. |
| **Signature** | `pop(opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **opts**: The navigation options.<br>**done**: The transition complete function. |

### popTo

|     |     |
| --- | --- |
| **Description** | Pop to a specific index in the navigation stack. |
| **Signature** | `popTo(indexOrViewCtrl: number ｜ ViewController, opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **indexOrViewCtrl**: The index or view controller to pop to.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

### popToRoot

|     |     |
| --- | --- |
| **Description** | Navigate back to the root of the stack, no matter how far back that is. |
| **Signature** | `popToRoot(opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **opts**: The navigation options.<br>**done**: The transition complete function. |

### push

|     |     |
| --- | --- |
| **Description** | Push a new component onto the current navigation stack. Pass any additional information along as an object. This additional information is accessible through NavParams. |
| **Signature** | `push<T extends NavComponent>(component: T, componentProps?: ComponentProps<T> ｜ null, opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **component**: The component to push onto the navigation stack.<br>**componentProps**: Any properties of the component.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

### removeIndex

|     |     |
| --- | --- |
| **Description** | Removes a component from the navigation stack at the specified index. |
| **Signature** | `removeIndex(startIndex: number, removeCount?: number, opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **startIndex**: The number to begin removal at.<br>**removeCount**: The number of components to remove.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

### setPages

|     |     |
| --- | --- |
| **Description** | Set the views of the current navigation stack and navigate to the last view. By default animations are disabled, but they can be enabled by passing options to the navigation controller. Navigation parameters can also be passed to the individual pages in the array. |
| **Signature** | `setPages(views: NavComponent[] ｜ NavComponentWithProps[], opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **views**: The list of views to set as the navigation stack.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

### setRoot

|     |     |
| --- | --- |
| **Description** | Set the root for the current navigation stack to a component. |
| **Signature** | `setRoot<T extends NavComponent>(component: T, componentProps?: ComponentProps<T> ｜ null, opts?: NavOptions ｜ null, done?: TransitionDoneFn) => Promise<boolean>` |
| **Parameters** | **component**: The component to set as the root of the navigation stack.<br>**componentProps**: Any properties of the component.<br>**opts**: The navigation options.<br>**done**: The transition complete function. |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
