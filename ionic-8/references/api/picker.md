# Ionic Picker Guide

Source: https://ionicframework.com/docs/api/picker

Sections: Prefix & Suffix Content · Theming · Picker in Modal · Accessibility · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

A Picker displays one or more columns with options for users to choose from.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-picker>
  <ion-picker-column value="javascript">
    <ion-picker-column-option value="" disabled="true">--</ion-picker-column-option>
    <ion-picker-column-option value="javascript">Javascript</ion-picker-column-option>
    <ion-picker-column-option value="typescript">Typescript</ion-picker-column-option>
    <ion-picker-column-option value="rust">Rust</ion-picker-column-option>
    <ion-picker-column-option value="c#">C#</ion-picker-column-option>
  </ion-picker-column>
</ion-picker>
```

```ts
import { Component } from '@angular/core';
import { IonPicker, IonPickerColumn, IonPickerColumnOption } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonPicker, IonPickerColumn, IonPickerColumnOption],
})
export class ExampleComponent {}
```

## Prefix & Suffix Content

Use the `prefix` and `suffix` slots to add additional content to the picker.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-picker>
  <ion-picker-column [value]="1">
    <div slot="prefix">$</div>
    <ion-picker-column-option value="" disabled="true">--</ion-picker-column-option>
    <ion-picker-column-option [value]="1">1</ion-picker-column-option>
    <ion-picker-column-option [value]="2">2</ion-picker-column-option>
    <ion-picker-column-option [value]="3">3</ion-picker-column-option>
    <ion-picker-column-option [value]="4">4</ion-picker-column-option>
    <ion-picker-column-option [value]="5">5</ion-picker-column-option>
    <div slot="suffix">USD</div>
  </ion-picker-column>
</ion-picker>
```

```ts
import { Component } from '@angular/core';
import { IonPicker, IonPickerColumn, IonPickerColumnOption } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonPicker, IonPickerColumn, IonPickerColumnOption],
})
export class ExampleComponent {}
```

## Theming

### CSS Variables

The picker highlight and fade can be customized using CSS variables on `ion-picker`. Developers can customize the individual appearance of `ion-picker-column-options` by targeting them directly and using host level styling.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-picker>
  <ion-picker-column value="red">
    <ion-picker-column-option value="" disabled="true">--</ion-picker-column-option>
    <ion-picker-column-option value="red">Red</ion-picker-column-option>
    <ion-picker-column-option value="blue">Blue</ion-picker-column-option>
    <ion-picker-column-option value="green">Green</ion-picker-column-option>
  </ion-picker-column>
</ion-picker>
```

```css
ion-picker {
  --highlight-background: var(--ion-color-dark);
  --highlight-border-radius: 50px;

  --fade-background-rgb: var(--ion-color-light-rgb);
}

ion-picker-column-option {
  text-transform: uppercase;
  background-size: auto auto;
  background-clip: border-box;
  background-size: 200% auto;
  color: #fff;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: textclip 2s linear infinite;
}

ion-picker-column-option[value='red'] {
  background-image: linear-gradient(-225deg, #231557 0%, #44107a 29%, #ff1361 67%, #fff800 100%);
}
ion-picker-column-option[value='blue'] {
  background-image: linear-gradient(-225deg, #2cd8d5 0%, #c5c1ff 56%, #ffbac3 100%);
}
ion-picker-column-option[value='green'] {
  background-image: linear-gradient(-225deg, #11998e 0%, #38ef7d 48%, #40e0d0 100%);
}

@keyframes textclip {
  to {
    background-position: 200% center;
  }
}
```

```ts
import { Component } from '@angular/core';
import { IonPicker, IonPickerColumn, IonPickerColumnOption } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonPicker, IonPickerColumn, IonPickerColumnOption],
})
export class ExampleComponent {}
```

## Picker in Modal

Pickers can be displayed inside of overlays, such as `ion-modal` to create a picker experience with confirmation or cancellation buttons.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts
- src/app/example.component.css

```html
<ion-button id="open-modal">Open modal</ion-button>
<ion-modal #modal trigger="open-modal" [isOpen]="true" (didDismiss)="onDidDismiss($event)">
  <ng-template>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-button (click)="modal.dismiss(null, 'cancel')">Cancel</ion-button>
      </ion-buttons>
      <ion-buttons slot="end">
        <ion-button (click)="modal.dismiss(currentValue, 'confirm')">Done</ion-button>
      </ion-buttons>
    </ion-toolbar>
    <ion-picker>
      <ion-picker-column [value]="currentValue" (ionChange)="onIonChange($event)">
        <ion-picker-column-option value="" disabled="true">--</ion-picker-column-option>
        <ion-picker-column-option value="javascript">Javascript</ion-picker-column-option>
        <ion-picker-column-option value="typescript">Typescript</ion-picker-column-option>
        <ion-picker-column-option value="rust">Rust</ion-picker-column-option>
        <ion-picker-column-option value="c#">C#</ion-picker-column-option>
      </ion-picker-column>
    </ion-picker>
  </ng-template>
</ion-modal>
```

```ts
import { Component } from '@angular/core';
import {
  IonButton,
  IonButtons,
  IonModal,
  IonPicker,
  IonPickerColumn,
  IonPickerColumnOption,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.css'],
  imports: [IonButton, IonButtons, IonModal, IonPicker, IonPickerColumn, IonPickerColumnOption, IonToolbar],
})
export class ExampleComponent {
  currentValue = 'javascript';

  onIonChange(event: CustomEvent) {
    this.currentValue = event.detail.value;
  }

  onDidDismiss(event: CustomEvent) {
    console.log('didDismiss', JSON.stringify(event.detail));
  }
}
```

```css
ion-modal {
  --height: auto;

  align-items: end;
}

ion-picker {
  margin-bottom: var(--ion-safe-area-bottom);
}
```

## Accessibility

### Screen Readers

Picker supports navigation using a screen reader by implementing the [`slider` role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/slider_role) on each [Picker Column](https://ionicframework.com/docs/api/picker-column). The following gestures can be used to navigate the Picker.

| Gesture | Function |
| --- | --- |
| Swipe Left | Move focus to the previous Picker Column. |
| Swipe Right | Move focus to the next Picker Column. |
| Swipe Up | Select the next option in the Picker Column. |
| Swipe Down | Select the previous option in the Picker Column. |
| Double Tap and Slide Up/Down | Adjust the selected option in the Picker Column. Can be used as an alternative to swiping up and down. |

caution

The Swipe Up and Swipe Down gestures rely on the correct key events being synthesized as noted on the [`slider` documentation](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/slider_role). [Chromium-based browsers do not synthesize keyboard events correctly](https://issues.chromium.org/issues/40816094), but the "Double Tap and Slide Up/Down" gesture can be used as an alternative until this has been implemented in Chromium-based browsers.

### Keyboard Interactions

Each [Picker Column](https://ionicframework.com/docs/api/picker-column) can be navigated using the keyboard when focused.

| Key | Description |
| --- | --- |
| `ArrowUp` | Scroll to the previous option. |
| `ArrowDown` | Scroll to the next option. |
| `PageUp` | Scroll up by more than one option. |
| `PageDown` | Scroll down by more than one option. |
| `Home` | Scroll to the first option. |
| `End` | Scroll to the last option. |

## Properties

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
| `--fade-background-rgb` | Background of the gradient covering non-selected items in rgb format |
| `--highlight-background` | Background of the picker highlight for the selected item |
| `--highlight-border-radius` | Border radius of the picker highlight for the selected item |

| Name | Description |
| --- | --- |
| `--fade-background-rgb` | Background of the gradient covering non-selected items in rgb format |
| `--highlight-background` | Background of the picker highlight for the selected item |
| `--highlight-border-radius` | Border radius of the picker highlight for the selected item |

## Slots

No slots available for this component.
