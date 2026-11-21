# Ionic Checkbox API

Source: https://ionicframework.com/docs/api/checkbox

Sections: Basic Usage · Label Placement · Alignment · Justification · Indeterminate Checkboxes · Links inside of Labels · Helper & Error Text · Theming · Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Checkboxes allow the selection of multiple options from a set of options. They appear as checked (ticked) when activated. Clicking on a checkbox will toggle the `checked` property. They can also be checked programmatically by setting the `checked` property.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-checkbox>I agree to the terms and conditions</ion-checkbox>
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox],
})
export class ExampleComponent {}
```

## Label Placement

Developers can use the `labelPlacement` property to control how the label is placed relative to the control. This property mirrors the flexbox `flex-direction` property.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-checkbox labelPlacement="start">Label at the Start</ion-checkbox>

<br />

<ion-checkbox labelPlacement="end">Label at the End</ion-checkbox>

<br />

<ion-checkbox labelPlacement="fixed">Fixed Width Label</ion-checkbox>

<br />

<ion-checkbox labelPlacement="stacked">Stacked Label</ion-checkbox>
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox],
})
export class ExampleComponent {}
```

## Alignment

Developers can use the `alignment` property to control how the label and control are aligned on the cross axis. This property mirrors the flexbox `align-items` property.

note

Stacked checkboxes can be aligned using the `alignment` property. This can be useful when the label and control need to be centered horizontally.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-checkbox label-placement="stacked" alignment="start">Aligned to the Start</ion-checkbox>
  </ion-item>

  <ion-item>
    <ion-checkbox label-placement="stacked" alignment="center">Aligned to the Center</ion-checkbox>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox, IonItem, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox, IonItem, IonList],
})
export class ExampleComponent {}
```

## Justification

Developers can use the `justify` property to control how the label and control are packed on a line. This property mirrors the flexbox `justify-content` property.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-checkbox justify="start">Packed at the Start of Line</ion-checkbox>
  </ion-item>

  <ion-item>
    <ion-checkbox justify="end">Packed at the End of Line</ion-checkbox>
  </ion-item>

  <ion-item>
    <ion-checkbox justify="space-between">Space Between Label and Control</ion-checkbox>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox, IonItem, IonList } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox, IonItem, IonList],
})
export class ExampleComponent {}
```

note

`ion-item` is only used in the demos to emphasize how `justify` works. It is not needed in order for `justify` to function correctly.

## Indeterminate Checkboxes

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-checkbox [indeterminate]="true">Indeterminate checkbox</ion-checkbox>
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox],
})
export class ExampleComponent {}
```

## Links inside of Labels

Checkbox labels can sometimes be accompanied with links. These links can provide more information related to the checkbox. However, clicking the link should not check the checkbox. To achieve this, we can use [stopPropagation](https://developer.mozilla.org/en-US/docs/Web/API/Event/stopPropagation) to prevent the click event from bubbling. When using this approach, the rest of the label still remains clickable.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-checkbox>I agree to the <a href="#" (click)="$event.stopPropagation()">terms and conditions</a></ion-checkbox>
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox],
})
export class ExampleComponent {}
```

## Helper & Error Text

Helper and error text can be used inside of a checkbox with the `helperText` and `errorText` property. The error text will not be displayed unless the `ion-invalid` and `ion-touched` classes are added to the `ion-checkbox`. This ensures errors are not shown before the user has a chance to enter data.

In Angular, this is done automatically through form validation. In JavaScript, React and Vue, the class needs to be manually added based on your own validation.

- src/app/example.component.html
- src/app/example.component.ts

```html
<form [formGroup]="myForm" (ngSubmit)="onSubmit()">
  <ion-checkbox
    formControlName="agree"
    helperText="Agree to the terms before continuing"
    errorText="You must agree to the terms to continue"
  >
    I agree to the terms and conditions
  </ion-checkbox>

  <br />

  <ion-button type="submit" size="small">Submit</ion-button>
</form>
```

```ts
import { Component } from '@angular/core';
import { FormBuilder, FormGroup, Validators, ReactiveFormsModule } from '@angular/forms';
import { IonCheckbox, IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  standalone: true,
  imports: [IonCheckbox, IonButton, ReactiveFormsModule],
  templateUrl: './example.component.html',
  styleUrl: './example.component.css',
})
export class ExampleComponent {
  myForm: FormGroup;

  constructor(private fb: FormBuilder) {
    this.myForm = this.fb.group({
      agree: [false, Validators.requiredTrue],
    });
  }

  onSubmit() {
    // Mark the control as touched to trigger the error message.
    // This is needed if the user submits the form without interacting
    // with the checkbox.
    this.myForm.get('agree')!.markAsTouched();
  }
}
```

## Theming

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-checkbox>Themed checkbox</ion-checkbox>
```

```css
ion-checkbox {
  --size: 32px;
  --checkbox-background-checked: #6815ec;
}

ion-checkbox::part(container) {
  border-radius: 6px;
  border: 2px solid #6815ec;
}
```

```ts
import { Component } from '@angular/core';
import { IonCheckbox } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox],
})
export class ExampleComponent {}
```

## Interfaces

### CheckboxChangeEventDetail

```typescript
interface CheckboxChangeEventDetail<T = any> {
  value: T;
  checked: boolean;
}
```

### CheckboxCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface CheckboxCustomEvent<T = any> extends CustomEvent {
  detail: CheckboxChangeEventDetail<T>;
  target: HTMLIonCheckboxElement;
}
```

## Properties

### alignment

|     |     |
| --- | --- |
| **Description** | How to control the alignment of the checkbox and label on the cross axis. `"start"`: The label and control will appear on the left of the cross axis in LTR, and on the right side in RTL. `"center"`: The label and control will appear at the center of the cross axis in both LTR and RTL. Setting this property will change the checkbox `display` to `block`. |
| **Attribute** | `alignment` |
| **Type** | `"center" ｜ "start" ｜ undefined` |
| **Default** | `undefined` |

### checked

|     |     |
| --- | --- |
| **Description** | If `true`, the checkbox is selected. |
| **Attribute** | `checked` |
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
| **Description** | If `true`, the user cannot interact with the checkbox. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### errorText

|     |     |
| --- | --- |
| **Description** | Text that is placed under the checkbox label and displayed when an error is detected. |
| **Attribute** | `error-text` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### helperText

|     |     |
| --- | --- |
| **Description** | Text that is placed under the checkbox label and displayed when no error is detected. |
| **Attribute** | `helper-text` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### indeterminate

|     |     |
| --- | --- |
| **Description** | If `true`, the checkbox will visually appear as indeterminate. |
| **Attribute** | `indeterminate` |
| **Type** | `boolean` |
| **Default** | `false` |

### justify

|     |     |
| --- | --- |
| **Description** | How to pack the label and checkbox within a line. `"start"`: The label and checkbox will appear on the left in LTR and on the right in RTL. `"end"`: The label and checkbox will appear on the right in LTR and on the left in RTL. `"space-between"`: The label and checkbox will appear on opposite ends of the line with space between the two elements. Setting this property will change the checkbox `display` to `block`. |
| **Attribute** | `justify` |
| **Type** | `"end" ｜ "space-between" ｜ "start" ｜ undefined` |
| **Default** | `undefined` |

### labelPlacement

|     |     |
| --- | --- |
| **Description** | Where to place the label relative to the checkbox. `"start"`: The label will appear to the left of the checkbox in LTR and to the right in RTL. `"end"`: The label will appear to the right of the checkbox in LTR and to the left in RTL. `"fixed"`: The label has the same behavior as `"start"` except it also has a fixed width. Long text will be truncated with ellipses ("..."). `"stacked"`: The label will appear above the checkbox regardless of the direction. The alignment of the label can be controlled with the `alignment` property. |
| **Attribute** | `label-placement` |
| **Type** | `"end" ｜ "fixed" ｜ "stacked" ｜ "start"` |
| **Default** | `'start'` |

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
| **Default** | `this.inputId` |

### required

|     |     |
| --- | --- |
| **Description** | If true, screen readers will announce it as a required field. This property works only for accessibility purposes, it will not prevent the form from submitting if the value is invalid. |
| **Attribute** | `required` |
| **Type** | `boolean` |
| **Default** | `false` |

### value

|     |     |
| --- | --- |
| **Description** | The value of the checkbox does not mean if it's checked or not, use the `checked` property for that.<br>The value of a checkbox is analogous to the value of an `<input type="checkbox">`, it's only used when the checkbox participates in a native `<form>`. |
| **Attribute** | `value` |
| **Type** | `any` |
| **Default** | `'on'` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionBlur` | Emitted when the checkbox loses focus. | `true` |
| `ionChange` | Emitted when the checked property has changed as a result of a user action such as a click.<br>This event will not emit when programmatically setting the `checked` property. | `true` |
| `ionFocus` | Emitted when the checkbox has focus. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `container` | The container for the checkbox mark. |
| `error-text` | Supporting text displayed beneath the checkbox label when the checkbox is invalid and touched. |
| `helper-text` | Supporting text displayed beneath the checkbox label when the checkbox is valid. |
| `label` | The label text describing the checkbox. |
| `mark` | The checkmark used to indicate the checked state. |
| `supporting-text` | Supporting text displayed beneath the checkbox label. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--border-color` | Border color of the checkbox icon |
| `--border-color-checked` | Border color of the checkbox icon when checked |
| `--border-radius` | Border radius of the checkbox icon |
| `--border-style` | Border style of the checkbox icon |
| `--border-width` | Border width of the checkbox icon |
| `--checkbox-background` | Background of the checkbox icon |
| `--checkbox-background-checked` | Background of the checkbox icon when checked |
| `--checkmark-color` | Color of the checkbox checkmark when checked |
| `--checkmark-width` | Stroke width of the checkbox checkmark |
| `--size` | Size of the checkbox icon |
| `--transition` | Transition of the checkbox icon |

| Name | Description |
| --- | --- |
| `--border-color` | Border color of the checkbox icon |
| `--border-color-checked` | Border color of the checkbox icon when checked |
| `--border-radius` | Border radius of the checkbox icon |
| `--border-style` | Border style of the checkbox icon |
| `--border-width` | Border width of the checkbox icon |
| `--checkbox-background` | Background of the checkbox icon |
| `--checkbox-background-checked` | Background of the checkbox icon when checked |
| `--checkmark-color` | Color of the checkbox checkmark when checked |
| `--checkmark-width` | Stroke width of the checkbox checkmark |
| `--size` | Size of the checkbox icon |
| `--transition` | Transition of the checkbox icon |

## Slots

| Name | Description |
| --- | --- |
| \`\` | The label text to associate with the checkbox. Use the "labelPlacement" property to control where the label is placed relative to the checkbox. |
