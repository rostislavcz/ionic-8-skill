# Ionic Range Slider

Source: https://ionicframework.com/docs/api/range

Sections: Labels · Decorations · Dual Knobs · Pins · Snapping & Ticks · Event Handling · Theming · Interfaces · Types · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The Range slider lets users select from a range of values by moving the slider knob. By default one knob controls the value of the range. This behavior can be customized using [dual knobs](https://ionicframework.com/docs/api/range#dual-knobs).

By default the Range slider has a minimum value of `0` and a maximum value of `100`. This can be configured with the `min` and `max` properties.

## Labels

Labels should be used to describe the range. They can be used visually, and they will also be read out by screen readers when the user is focused on the range. This makes it easy for the user to understand the intent of the range. Range has several ways to assign a label:

- `label` property: used for plaintext labels
- `label` slot: used for custom HTML labels
- `aria-label`: used to provide a label for screen readers but adds no visible label

### Label Placement

The below demo shows how to use the `labelPlacement` property to change the position of the label relative to the range. While the `label` property is used here, `labelPlacement` can also be used with the `label` slot.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range labelPlacement="start" label="Label at the Start"></ion-range>

<br />

<ion-range labelPlacement="end" label="Label at the End"></ion-range>

<br />

<ion-range labelPlacement="fixed" label="Fixed Width Label"></ion-range>

<br />

<ion-range labelPlacement="stacked" label="Stacked Label"></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {}
```

### Label Slot

While plaintext labels should be passed in via the `label` property, if custom HTML is needed, it can be passed through the `label` slot instead.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range>
  <div slot="label">Label with <ion-text color="primary">custom HTML</ion-text></div>
</ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange, IonText } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange, IonText],
})
export class ExampleComponent {}
```

### No Visible Label

If no visible label is needed, developers should still supply an `aria-label` so the range is accessible to screen readers.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range aria-label="Volume"></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {}
```

## Decorations

Decorative elements can be passed into the `start` or `end` slots of the range. This is useful for adding icons such as low volume or high volume icons. Since these elements are decorative, they should not be announced by assistive technology such as screen readers.

If the directionality of the document is set to left to right, the contents slotted to the `start` position will display to the left of the range, where as contents slotted to the `end` position will display to the right of the range. In right to left (rtl) directionality, the contents slotted to the `start` position will display to the right of the range, where as contents slotted to the `end` position will display to the left of the range.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range aria-label="Temperature">
  <ion-icon slot="start" name="snow-outline"></ion-icon>
  <ion-icon slot="end" name="sunny-outline"></ion-icon>
</ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonIcon, IonRange } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { snowOutline, sunnyOutline } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonIcon, IonRange],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ snowOutline, sunnyOutline });
  }
}
```

## Dual Knobs

Dual knobs introduce two knob controls that users can use to select a value at a lower and upper bounds. When selected, the Range will emit an `ionChange` event with a [RangeValue](https://ionicframework.com/docs/api/range#rangevalue), containing the upper and lower values selected.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range aria-label="Dual Knobs Range" [dualKnobs]="true" [value]="{ lower: 20, upper: 80 }"></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {}
```

## Pins

The `pin` attribute will display the value of the Range above the knob when dragged. This allows users to select a specific value within the Range.

With the `pinFormatter` function, developers can customize the formatting of the range value to the user.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range aria-label="Range with pin" [pin]="true" [pinFormatter]="pinFormatter"></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {
  pinFormatter(value: number) {
    return `${value}%`;
  }
}
```

## Snapping & Ticks

Ticks show indications for each available value on the Range. In order to use ticks, developers must set both `snaps` and the `ticks` property to `true`.

With snapping enabled, the Range knob will snap to the nearest available value as the knob is dragged and released.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range aria-label="Range with ticks" [ticks]="true" [snaps]="true" [min]="0" [max]="10"></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {}
```

## Event Handling

### Using `ionChange`

The `ionChange` event emits as the Range knob value changes.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range aria-label="Range with ionChange" (ionChange)="onIonChange($event)"></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange, RangeCustomEvent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {
  onIonChange(event: RangeCustomEvent) {
    console.log('ionChange emitted value:', event.detail.value);
  }
}
```

### Using `ionKnobMoveStart` and `ionKnobMoveEnd`

The `ionKnobMoveStart` event emits when the Range knob begins dragging, whether through mouse drag, touch gesture or keyboard interaction. Inversely, `ionKnobMoveEnd` emits when the Range knob is released. Both events emit with the `RangeValue` type and work in combination with the `dualKnobs` property.

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-range
  aria-label="Range with knob events"
  (ionKnobMoveStart)="onIonKnobMoveStart($event)"
  (ionKnobMoveEnd)="onIonKnobMoveEnd($event)"
></ion-range>
```

```ts
import { Component } from '@angular/core';
import { IonRange, RangeCustomEvent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {
  onIonKnobMoveStart(event: RangeCustomEvent) {
    console.log('ionKnobMoveStart:', event.detail.value);
  }

  onIonKnobMoveEnd(event: RangeCustomEvent) {
    console.log('ionKnobMoveEnd:', event.detail.value);
  }
}
```

## Theming

### CSS Custom Properties

Range includes [CSS Variables](https://ionicframework.com/docs/api/range#css-custom-properties) to quickly theme and customize the appearance of the Range component to match your application's design.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-range aria-label="Custom range" [value]="50" [pin]="true"></ion-range>
```

```css
ion-range {
  --bar-background: #a2d2ff;
  --bar-background-active: #bde0fe;
  --bar-height: 8px;
  --bar-border-radius: 8px;
  --knob-background: #ffc8dd;
  --knob-size: 40px;
  --pin-background: #ffafcc;
  --pin-color: #fff;
}
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {}
```

### CSS Shadow Parts

Range includes [CSS Shadow Parts](https://ionicframework.com/docs/api/range#css-shadow-parts) to allow complete customization of specific element nodes within the Range component. CSS Shadow Parts offer the most customization capabilities and are the recommended approach when requiring advance styling with the Range component.

When `dualKnobs` is enabled, additional Shadow Parts are exposed to allow each knob to be styled independently. These are available in two forms: **static identity parts** (`A` and `B`) and **dynamic position parts** (`lower` and `upper`). The A and B parts always refer to the same physical knobs, even if the knobs cross. In contrast, the lower and upper parts reflect the current value position and automatically swap if the knobs cross. This allows styling by consistent identity or by relative value within the range.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<h2>Single Knob</h2>
<ion-range
  id="range-single"
  aria-label="Custom range"
  [min]="0"
  [max]="10"
  [value]="5"
  [pin]="true"
  [ticks]="true"
  [snaps]="true"
></ion-range>

<h2>Dual Knobs (A/B)</h2>
<ion-range
  id="range-a-b"
  aria-label="Custom dual knob range with A/B styling"
  [min]="0"
  [max]="10"
  [value]="{lower: 3, upper: 7}"
  [dualKnobs]="true"
  [pin]="true"
></ion-range>

<h2>Dual Knobs (Lower/Upper)</h2>
<ion-range
  id="range-lower-upper"
  aria-label="Custom dual knob range with lower/upper styling"
  [min]="0"
  [max]="10"
  [value]="{lower: 3, upper: 7}"
  [dualKnobs]="true"
  [pin]="true"
></ion-range>
```

```css
/* Shared styles for all ranges */
ion-range {
  --knob-size: 34px;
}

ion-range::part(knob) {
  background: #fff;

  box-sizing: border-box;
}

/* Hide the Material Design indicator */
ion-range::part(knob)::before {
  display: none;
}

ion-range::part(pin) {
  color: #fff;
  border-radius: 50%;
}

ion-range::part(tick),
ion-range::part(tick-active) {
  height: 8px;
  top: 17px;
}

/* Single Knob Range */
#range-single::part(bar),
#range-single::part(tick) {
  background: #bed4ff;
}

#range-single::part(bar-active),
#range-single::part(tick-active) {
  background: #40a2fd;
}

#range-single::part(knob) {
  border: 4px solid #40a2fd;
}

#range-single::part(knob pressed) {
  background: #bed4ff;
}

#range-single::part(pin),
#range-single::part(pin)::before {
  background: #40a2fd;
}

/* Dual Knobs (A/B) Range */
#range-a-b::part(bar-active) {
  background: #1ea9ca;
}

#range-a-b::part(knob-a) {
  border: 4px solid #0f8fd6;
}

#range-a-b::part(knob-a pressed) {
  background: #cfeefe;
}

#range-a-b::part(pin-a),
#range-a-b::part(pin-a)::before {
  background: #0f8fd6;
}

#range-a-b::part(knob-b) {
  border: 4px solid #2dc2bd;
}

#range-a-b::part(knob-b pressed) {
  background: #d4f5f3;
}

#range-a-b::part(pin-b),
#range-a-b::part(pin-b)::before {
  background: #2dc2bd;
}

/* Dual Knobs (Lower/Upper) Range */
#range-lower-upper::part(bar-active) {
  background: linear-gradient(to right, #0059ff 0%, #b77bff 100%);
}

#range-lower-upper::part(knob-lower) {
  border: 4px solid #0059ff;
}

#range-lower-upper::part(knob-lower pressed) {
  background: #bed4ff;
}

#range-lower-upper::part(pin-lower),
#range-lower-upper::part(pin-lower)::before {
  background: #0059ff;
}

#range-lower-upper::part(knob-upper) {
  border: 4px solid #b77bff;
}

#range-lower-upper::part(knob-upper pressed) {
  background: #f1e5ff;
}

#range-lower-upper::part(pin-upper),
#range-lower-upper::part(pin-upper)::before {
  background: #b77bff;
}
```

```ts
import { Component } from '@angular/core';
import { IonRange } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRange],
})
export class ExampleComponent {}
```

## Interfaces

### RangeChangeEventDetail

```typescript
interface RangeChangeEventDetail {
  value: RangeValue;
}
```

### RangeKnobMoveStartEventDetail

```typescript
interface RangeKnobMoveStartEventDetail {
  value: RangeValue;
}
```

### RangeKnobMoveEndEventDetail

```typescript
interface RangeKnobMoveEndEventDetail {
  value: RangeValue;
}
```

### RangeCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface RangeCustomEvent extends CustomEvent {
  detail: RangeChangeEventDetail;
  target: HTMLIonRangeElement;
}
```

## Types

### RangeValue

```typescript
type RangeValue = number | { lower: number, upper: number };
```

## Properties

### activeBarStart

|     |     |
| --- | --- |
| **Description** | The start position of the range active bar. This feature is only available with a single knob (dualKnobs="false"). Valid values are greater than or equal to the min value and less than or equal to the max value. |
| **Attribute** | `active-bar-start` |
| **Type** | `number ｜ undefined` |
| **Default** | `undefined` |

### color

|     |     |
| --- | --- |
| **Description** | The color to use from your application's color palette. Default options are: `"primary"`, `"secondary"`, `"tertiary"`, `"success"`, `"warning"`, `"danger"`, `"light"`, `"medium"`, and `"dark"`. For more information on colors, see [theming](https://ionicframework.com/docs/theming/basics). |
| **Attribute** | `color` |
| **Type** | `"danger" ｜ "dark" ｜ "light" ｜ "medium" ｜ "primary" ｜ "secondary" ｜ "success" ｜ "tertiary" ｜ "warning" ｜ string ｜ undefined` |
| **Default** | `undefined` |

### debounce

|     |     |
| --- | --- |
| **Description** | How long, in milliseconds, to wait to trigger the `ionInput` event after each change in the range value. |
| **Attribute** | `debounce` |
| **Type** | `number ｜ undefined` |
| **Default** | `undefined` |

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the user cannot interact with the range. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### dualKnobs

|     |     |
| --- | --- |
| **Description** | Show two knobs. |
| **Attribute** | `dual-knobs` |
| **Type** | `boolean` |
| **Default** | `false` |

### label

|     |     |
| --- | --- |
| **Description** | The text to display as the control's label. Use this over the `label` slot if you only need plain text. The `label` property will take priority over the `label` slot if both are used. |
| **Attribute** | `label` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### labelPlacement

|     |     |
| --- | --- |
| **Description** | Where to place the label relative to the range. `"start"`: The label will appear to the left of the range in LTR and to the right in RTL. `"end"`: The label will appear to the right of the range in LTR and to the left in RTL. `"fixed"`: The label has the same behavior as `"start"` except it also has a fixed width. Long text will be truncated with ellipses ("..."). `"stacked"`: The label will appear above the range regardless of the direction. |
| **Attribute** | `label-placement` |
| **Type** | `"end" ｜ "fixed" ｜ "stacked" ｜ "start"` |
| **Default** | `'start'` |

### max

|     |     |
| --- | --- |
| **Description** | Maximum integer value of the range. |
| **Attribute** | `max` |
| **Type** | `number` |
| **Default** | `100` |

### min

|     |     |
| --- | --- |
| **Description** | Minimum integer value of the range.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `min` |
| **Type** | `number` |
| **Default** | `0` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

### name

|     |     |
| --- | --- |
| **Description** | The name of the control, which is submitted with the form data. |
| **Attribute** | `name` |
| **Type** | `string` |
| **Default** | `this.rangeId` |

### pin

|     |     |
| --- | --- |
| **Description** | If `true`, a pin with integer value is shown when the knob is pressed. |
| **Attribute** | `pin` |
| **Type** | `boolean` |
| **Default** | `false` |

### pinFormatter

|     |     |
| --- | --- |
| **Description** | A callback used to format the pin text. By default the pin text is set to `Math.round(value)`.<br>See [https://ionicframework.com/docs/troubleshooting/runtime#accessing-this](https://ionicframework.com/docs/troubleshooting/runtime#accessing-this) if you need to access `this` from within the callback. |
| **Attribute** | `undefined` |
| **Type** | `(value: number) => string ｜ number` |
| **Default** | `(value: number): number => Math.round(value)` |

### snaps

|     |     |
| --- | --- |
| **Description** | If `true`, the knob snaps to tick marks evenly spaced based on the step property value. |
| **Attribute** | `snaps` |
| **Type** | `boolean` |
| **Default** | `false` |

### step

|     |     |
| --- | --- |
| **Description** | Specifies the value granularity. |
| **Attribute** | `step` |
| **Type** | `number` |
| **Default** | `1` |

### ticks

|     |     |
| --- | --- |
| **Description** | If `true`, tick marks are displayed based on the step value. Only applies when `snaps` is `true`. |
| **Attribute** | `ticks` |
| **Type** | `boolean` |
| **Default** | `true` |

### value

|     |     |
| --- | --- |
| **Description** | the value of the range. |
| **Attribute** | `value` |
| **Type** | `number ｜ { lower: number; upper: number; }` |
| **Default** | `0` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionBlur` | Emitted when the range loses focus. | `true` |
| `ionChange` | The `ionChange` event is fired for `<ion-range>` elements when the user modifies the element's value: - When the user releases the knob after dragging; - When the user moves the knob with keyboard arrows<br>This event will not emit when programmatically setting the `value` property. | `true` |
| `ionFocus` | Emitted when the range has focus. | `true` |
| `ionInput` | The `ionInput` event is fired for `<ion-range>` elements when the value is modified. Unlike `ionChange`, `ionInput` is fired continuously while the user is dragging the knob. | `true` |
| `ionKnobMoveEnd` | Emitted when the user finishes moving the range knob, whether through mouse drag, touch gesture, or keyboard interaction. | `true` |
| `ionKnobMoveStart` | Emitted when the user starts moving the range knob, whether through mouse drag, touch gesture, or keyboard interaction. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `activated` | Added to the knob-handle, knob, and pin when the knob is active. Only one set has this part at a time when `dualKnobs` is `true`. |
| `bar` | The inactive part of the bar. |
| `bar-active` | The active part of the bar. |
| `focused` | Added to the knob-handle, knob, and pin that currently has focus. Only one set has this part at a time when `dualKnobs` is `true`. |
| `hover` | Added to the knob-handle, knob, and pin when the knob has hover. Only one set has this part at a time when `dualKnobs` is `true`. |
| `knob` | The visual knob element on the range track. |
| `knob-a` | The visual knob for the static `A` identity when `dualKnobs` is `true`. This identity does not change, even if the knobs cross and swap which one represents the lower or upper value. |
| `knob-b` | The visual knob for the static `B` identity when `dualKnobs` is `true`. This identity does not change, even if the knobs cross and swap which one represents the lower or upper value. |
| `knob-handle` | The container that wraps the knob and handles drag interactions. |
| `knob-handle-a` | The container for the knob with the static `A` identity when `dualKnobs` is `true`. This identity does not change, even if the knobs cross and swap which one represents the lower or upper value. |
| `knob-handle-b` | The container for the knob with the static `B` identity when `dualKnobs` is `true`. This identity does not change, even if the knobs cross and swap which one represents the lower or upper value. |
| `knob-handle-lower` | The container for the knob whose current `value` is `lower` when `dualKnobs` is `true`. The lower and upper parts swap which knob handle they refer to when the knobs cross. |
| `knob-handle-upper` | The container for the knob whose current `value` is `upper` when `dualKnobs` is `true`. The lower and upper parts swap which knob handle they refer to when the knobs cross. |
| `knob-lower` | The visual knob whose current `value` is `lower` when `dualKnobs` is `true`. The lower and upper parts swap which knob they refer to when the knobs cross. |
| `knob-upper` | The visual knob whose current `value` is `upper` when `dualKnobs` is `true`. The lower and upper parts swap which knob they refer to when the knobs cross. |
| `label` | The label text describing the range. |
| `pin` | The value indicator displayed above a knob. |
| `pin-a` | The value indicator above the knob with the static `A` identity when `dualKnobs` is `true`. This identity does not change, even if the knobs cross and swap which one represents the lower or upper value. |
| `pin-b` | The value indicator above the knob with the static `B` identity when `dualKnobs` is `true`. This identity does not change, even if the knobs cross and swap which one represents the lower or upper value. |
| `pin-lower` | The value indicator above the knob whose current `value` is `lower` when `dualKnobs` is `true`. The lower and upper parts swap which pin they refer to when the knobs cross. |
| `pin-upper` | The value indicator above the knob whose current `value` is `upper` when `dualKnobs` is `true`. The lower and upper parts swap which pin they refer to when the knobs cross. |
| `pressed` | Added to the knob-handle, knob, and pin that is currently being pressed to drag. Only one set has this part at a time when `dualKnobs` is `true`. |
| `tick` | An inactive tick mark. |
| `tick-active` | An active tick mark. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--bar-background` | Background of the range bar |
| `--bar-background-active` | Background of the active range bar |
| `--bar-border-radius` | Border radius of the range bar |
| `--bar-height` | Height of the range bar |
| `--height` | Height of the range |
| `--knob-background` | Background of the range knob |
| `--knob-border-radius` | Border radius of the range knob |
| `--knob-box-shadow` | Box shadow of the range knob |
| `--knob-size` | Size of the range knob |
| `--pin-background` | Background of the range pin (only available in MD mode) |
| `--pin-color` | Color of the range pin (only available in MD mode) |

| Name | Description |
| --- | --- |
| `--bar-background` | Background of the range bar |
| `--bar-background-active` | Background of the active range bar |
| `--bar-border-radius` | Border radius of the range bar |
| `--bar-height` | Height of the range bar |
| `--height` | Height of the range |
| `--knob-background` | Background of the range knob |
| `--knob-border-radius` | Border radius of the range knob |
| `--knob-box-shadow` | Box shadow of the range knob |
| `--knob-size` | Size of the range knob |
| `--pin-background` | Background of the range pin (only available in MD mode) |
| `--pin-color` | Color of the range pin (only available in MD mode) |

## Slots

| Name | Description |
| --- | --- |
| `end` | Content is placed to the right of the range slider in LTR, and to the left in RTL. |
| `label` | The label text to associate with the range. Use the "labelPlacement" property to control where the label is placed relative to the range. |
| `start` | Content is placed to the left of the range slider in LTR, and to the right in RTL. |
