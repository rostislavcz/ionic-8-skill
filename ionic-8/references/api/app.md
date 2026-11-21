# Ionic App Component

Source: https://ionicframework.com/docs/api/app

Sections: Programmatic Focus · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

App is a container element for an Ionic application. There should only be one `<ion-app>` element per project. An app can have many Ionic components including menus, headers, content, and footers. The overlay components get appended to the `<ion-app>` when they are presented.

Using `ion-app` enables the following behaviors:

- [Keyboard Lifecycle Events](https://ionicframework.com/docs/developing/keyboard#keyboard-lifecycle-events) without the need for any native plugins
- [Hardware Back Button Listeners](https://ionicframework.com/docs/developing/hardware-back-button) for customizing the hardware back button behavior on Android devices
- Status bar support in Capacitor or Cordova which allows users to scroll to the top of the view by tapping the status bar
- Scroll assist utilities which scroll the content so focused text inputs are not covered by the on-screen keyboard
- [Ripple effect](https://ionicframework.com/docs/api/ripple-effect) when activating buttons on Material Design mode
- Other tap and focus utilities which make the experience of using an Ionic app feel more native

## Programmatic Focus

Ionic offers focus utilities for components with the `ion-focusable` class. These utilities automatically manage focus for components when certain keyboard keys, like `Tab`, are pressed. Components can also be programmatically focused in response to user actions using the `setFocus` method from `ion-app`.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-button id="buttonToFocus" fill="outline">Button</ion-button>

<ion-radio-group value="a">
  <ion-radio id="radioToFocus" value="a">Radio</ion-radio>
</ion-radio-group>

<br />

<ion-button (click)="focusElement('#buttonToFocus')">Focus Button</ion-button>
<ion-button (click)="focusElement('#radioToFocus')">Focus Radio</ion-button>
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonRadio, IonRadioGroup],
})
export class ExampleComponent {
  focusElement(id: string) {
    const el = document.querySelector(id) as HTMLElement;

    const app = el.closest('ion-app');
    if (app) {
      app.setFocus([el]);
    }
  }
}
```

## Properties

No properties available for this component.

## Events

No events available for this component.

## Methods

### setFocus

|     |     |
| --- | --- |
| **Description** | Used to set focus on an element that uses `ion-focusable`. Do not use this if focusing the element as a result of a keyboard event as the focus utility should handle this for us. This method should be used when we want to programmatically focus an element as a result of another user action. (Ex: We focus the first element inside of a popover when the user presents it, but the popover is not always presented as a result of keyboard action.) |
| **Signature** | `setFocus(elements: HTMLElement[]) => Promise<void>` |
| **Parameters** | **elements**: An array of HTML elements to set focus on. |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
