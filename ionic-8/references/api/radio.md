# Ionic Radio Component

Source: https://ionicframework.com/docs/api/radio

Sections: Basic Usage · Label Placement · Label Wrapping · Object Value References · Alignment · Justification · Deselecting Radios · Helper & Error Text · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Radios should be used inside of a [radio group](https://ionicframework.com/docs/api/radio-group). Pressing a radio will check it and uncheck the previously selected radio, if there is one. They can also be checked programmatically by setting the value property of the parent radio group to the value of the radio.

When radios are inside of a radio group, only one radio will be checked at any time. If more than one item should be selected, [checkboxes](https://ionicframework.com/docs/api/checkbox) should be used instead. Radios can be disabled within a group to prevent interaction with them.

## Basic Usage

Radio

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-radio-group value="strawberries">
  <ion-radio value="grapes">Grapes</ion-radio><br />
  <ion-radio value="strawberries">Strawberries</ion-radio><br />
  <ion-radio value="pineapple">Pineapple</ion-radio><br />
  <ion-radio value="cherries">Cherries</ion-radio>
</ion-radio-group>
```

```ts
import { Component } from '@angular/core';
import { IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

## Label Placement

Developers can use the `labelPlacement` property to control how the label is placed relative to the control. This property mirrors the flexbox `flex-direction` property.

Radio

Radio

Label at the Start

Label at the End

Fixed Width Label

Stacked Label

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-radio-group value="start">
  <ion-radio value="start" labelPlacement="start">Label at the Start</ion-radio>
</ion-radio-group>

<br />

<ion-radio-group value="end">
  <ion-radio value="end" labelPlacement="end">Label at the End</ion-radio>
</ion-radio-group>

<br />

<ion-radio-group value="fixed">
  <ion-radio value="fixed" labelPlacement="fixed">Fixed Width Label</ion-radio>
</ion-radio-group>

<br />

<ion-radio-group value="stacked">
  <ion-radio value="stacked" labelPlacement="stacked">Stacked Label</ion-radio>
</ion-radio-group>
```

```ts
import { Component } from '@angular/core';
import { IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

## Label Wrapping

Regardless of label placement, long text will not wrap by default. If the width of the radio is constrained, overflowing text will be truncated with an ellipsis. You can enable text wrapping by adding the `ion-text-wrap` class to a wrapper around the radio text or styling the `label` shadow part using the `::part()` selector.

Radio

Truncated with ellipsis by default
Wrapping with text-wrap applied to label shadow part

Wrapping with ion-text-wrap class applied wrapper element

Radio

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-list>
  <ion-radio-group value="truncated">
    <ion-item>
      <ion-radio value="truncated">Truncated with ellipsis by default</ion-radio>
    </ion-item>
    <ion-item>
      <ion-radio value="wrapped-part" class="wrapped">Wrapping with text-wrap applied to label shadow part</ion-radio>
    </ion-item>
    <ion-item>
      <ion-radio value="wrapped-div">
        <div class="ion-text-wrap">Wrapping with ion-text-wrap class applied wrapper element</div>
      </ion-radio>
    </ion-item>
  </ion-radio-group>
</ion-list>
```

```css
ion-list {
  width: 250px;
}

ion-radio.wrapped::part(label) {
  white-space: normal;
}
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonList, IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonList, IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

## Object Value References

By default, the radio group uses strict equality (`===`) to determine if an option is selected. This can be overridden by providing a property name or a function to the `compareWith` property.

Radio

Radio

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-radio-group [compareWith]="compareWith" (ionChange)="handleChange($event)">
    @for (food of foods; track food.id) {
    <ion-item>
      <ion-radio [value]="food">{{ food.name }}</ion-radio>
    </ion-item>
    }
  </ion-radio-group>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonList, IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

interface Food {
  id: number;
  name: string;
  type: string;
}

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonList, IonRadio, IonRadioGroup],
})
export class ExampleComponent {
  foods: Food[] = [\
    {\
      id: 1,\
      name: 'Apples',\
      type: 'fruit',\
    },\
    {\
      id: 2,\
      name: 'Carrots',\
      type: 'vegetable',\
    },\
    {\
      id: 3,\
      name: 'Cupcakes',\
      type: 'dessert',\
    },\
  ];

  compareWith(o1: Food, o2: Food): boolean {
    return o1.id === o2.id;
  }

  handleChange(event: Event): void {
    const target = event.target as HTMLInputElement;
    console.log('Current value:', JSON.stringify(target.value));
  }
}
```

## Alignment

Developers can use the `alignment` property to control how the label and control are aligned on the cross axis. This property mirrors the flexbox `align-items` property.

note

Stacked radios can be aligned using the `alignment` property. This can be useful when the label and control need to be centered horizontally.

Radio

Radio

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-radio-group value="start">
    <ion-item>
      <ion-radio value="start" labelPlacement="stacked" alignment="start">Aligned to the Start</ion-radio>
    </ion-item>
  </ion-radio-group>

  <ion-radio-group value="center">
    <ion-item>
      <ion-radio value="center" labelPlacement="stacked" alignment="center">Aligned to the Center</ion-radio>
    </ion-item>
  </ion-radio-group>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonList, IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonList, IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

## Justification

Developers can use the `justify` property to control how the label and control are packed on a line. This property mirrors the flexbox `justify-content` property.

Radio

Radio

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-radio-group value="start">
    <ion-item>
      <ion-radio value="start" justify="start">Packed at the Start of Line</ion-radio>
    </ion-item>
  </ion-radio-group>

  <ion-radio-group value="end">
    <ion-item>
      <ion-radio value="end" justify="end">Packed at the End of Line</ion-radio>
    </ion-item>
  </ion-radio-group>

  <ion-radio-group value="space-between">
    <ion-item>
      <ion-radio value="space-between" justify="space-between">Space Between Label and Control</ion-radio>
    </ion-item>
  </ion-radio-group>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonList, IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonList, IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

note

`ion-item` is only used in the demos to emphasize how `justify` works. It is not needed in order for `justify` to function correctly.

## Deselecting Radios

By default, once a radio is selected it cannot be deselected; pressing it again will keep it selected. This behavior can be modified by using the `allowEmptySelection` property on the parent radio group, which enables the radios to be deselected.

Radio

Radio

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-radio-group [allowEmptySelection]="true" value="turtles">
  <ion-radio value="dogs">Dogs</ion-radio><br />
  <ion-radio value="cats">Cats</ion-radio><br />
  <ion-radio value="turtles">Turtles</ion-radio><br />
  <ion-radio value="fish">Fish</ion-radio><br />
</ion-radio-group>
```

```ts
import { Component } from '@angular/core';
import { IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

## Helper & Error Text

Helper and error text can be used inside of a radio group with the `helperText` and `errorText` property. The error text will not be displayed unless the `ion-invalid` and `ion-touched` classes are added to the `ion-radio-group`. This ensures errors are not shown before the user has a chance to enter data.

In Angular, this is done automatically through form validation. In JavaScript, React and Vue, the class needs to be manually added based on your own validation.

Input

Input

- src/app/example.component.html
- src/app/example.component.ts

```html
<form [formGroup]="myForm" (ngSubmit)="onSubmit()">
  <ion-radio-group
    formControlName="favFruit"
    helperText="Select your favorite fruit"
    errorText="This field is required"
  >
    <ion-radio value="grapes">Grapes</ion-radio><br />
    <ion-radio value="strawberries">Strawberries</ion-radio><br />
    <ion-radio value="pineapple">Pineapple</ion-radio><br />
    <ion-radio value="cherries">Cherries</ion-radio>
  </ion-radio-group>

  <br />

  <ion-button type="submit" size="small">Submit</ion-button>
</form>
```

```ts
import { Component } from '@angular/core';
import { FormBuilder, FormGroup, Validators, ReactiveFormsModule } from '@angular/forms';
import { IonRadioGroup, IonRadio, IonButton } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  standalone: true,
  imports: [IonRadioGroup, IonRadio, IonButton, ReactiveFormsModule],
  templateUrl: './example.component.html',
  styleUrl: './example.component.css',
})
export class ExampleComponent {
  myForm: FormGroup;

  constructor(private fb: FormBuilder) {
    this.myForm = this.fb.group({
      favFruit: ['', Validators.required],
    });
  }

  onSubmit() {
    // Mark the control as touched to trigger the error message.
    // This is needed if the user submits the form without interacting
    // with the toggle.
    this.myForm.get('favFruit')!.markAsTouched();
  }
}
```

## Theming

### Colors

Radio

Radio

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-radio-group value="primary">
  <ion-radio aria-label="Primary" color="primary" value="primary"></ion-radio>
</ion-radio-group>
<ion-radio-group value="secondary">
  <ion-radio aria-label="Secondary" color="secondary" value="secondary"></ion-radio>
</ion-radio-group>
<ion-radio-group value="tertiary">
  <ion-radio aria-label="Tertiary" color="tertiary" value="tertiary"></ion-radio>
</ion-radio-group>
<ion-radio-group value="success">
  <ion-radio aria-label="Success" color="success" value="success"></ion-radio>
</ion-radio-group>
<ion-radio-group value="warning">
  <ion-radio aria-label="Warning" color="warning" value="warning"></ion-radio>
</ion-radio-group>
<ion-radio-group value="danger">
  <ion-radio aria-label="Danger" color="danger" value="danger"></ion-radio>
</ion-radio-group>
<ion-radio-group value="light">
  <ion-radio aria-label="Light" color="light" value="light"></ion-radio>
</ion-radio-group>
<ion-radio-group value="medium">
  <ion-radio aria-label="Medium" color="medium" value="medium"></ion-radio>
</ion-radio-group>
<ion-radio-group value="dark">
  <ion-radio aria-label="Dark" color="dark" value="dark"></ion-radio>
</ion-radio-group>
```

```ts
import { Component } from '@angular/core';
import { IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

### CSS Custom Properties

Radio

Radio

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-radio-group value="custom-checked">
  <ion-radio value="custom" aria-label="Custom checkbox"></ion-radio>
  <ion-radio value="custom-checked" aria-label="Custom checkbox that is checked"></ion-radio>
</ion-radio-group>
```

```css
ion-radio {
  --border-radius: 4px;
  --inner-border-radius: 4px;

  --color: #ddd;
  --color-checked: #6815ec;
}

ion-radio.ios::part(container) {
  width: 20px;
  height: 20px;

  border: 2px solid #ddd;
  border-radius: 4px;
}

.radio-checked.ios::part(container) {
  border-color: #6815ec;
}
```

```ts
import { Component } from '@angular/core';
import { IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

### CSS Shadow Parts

Radio

Radio

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-radio-group value="custom-checked">
  <ion-radio value="custom" aria-label="Custom checkbox"></ion-radio>
  <ion-radio value="custom-checked" aria-label="Custom checkbox that is checked"></ion-radio>
</ion-radio-group>
```

```css
ion-radio::part(container) {
  width: 30px;
  height: 30px;

  border-radius: 8px;
  border: 2px solid #ddd;
}

ion-radio::part(mark) {
  background: none;
  transition: none;
  transform: none;
  border-radius: 0;
}

ion-radio.radio-checked::part(container) {
  background: #6815ec;
  border-color: transparent;
}

ion-radio.radio-checked::part(mark) {
  width: 6px;
  height: 10px;

  border-width: 0px 2px 2px 0px;
  border-style: solid;
  border-color: #fff;

  transform: rotate(45deg);
}
```

```ts
import { Component } from '@angular/core';
import { IonRadio, IonRadioGroup } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRadio, IonRadioGroup],
})
export class ExampleComponent {}
```

## Properties

### alignment

|     |     |
| --- | --- |
| **Description** | How to control the alignment of the radio and label on the cross axis. `"start"`: The label and control will appear on the left of the cross axis in LTR, and on the right side in RTL. `"center"`: The label and control will appear at the center of the cross axis in both LTR and RTL. Setting this property will change the radio `display` to `block`. |
| **Attribute** | `alignment` |
| **Type** | `"center" ｜ "start" ｜ undefined` |
| **Default** | `undefined` |

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
| **Description** | If `true`, the user cannot interact with the radio. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### justify

|     |     |
| --- | --- |
| **Description** | How to pack the label and radio within a line. `"start"`: The label and radio will appear on the left in LTR and on the right in RTL. `"end"`: The label and radio will appear on the right in LTR and on the left in RTL. `"space-between"`: The label and radio will appear on opposite ends of the line with space between the two elements. Setting this property will change the radio `display` to `block`. |
| **Attribute** | `justify` |
| **Type** | `"end" ｜ "space-between" ｜ "start" ｜ undefined` |
| **Default** | `undefined` |

### labelPlacement

|     |     |
| --- | --- |
| **Description** | Where to place the label relative to the radio. `"start"`: The label will appear to the left of the radio in LTR and to the right in RTL. `"end"`: The label will appear to the right of the radio in LTR and to the left in RTL. `"fixed"`: The label has the same behavior as `"start"` except it also has a fixed width. Long text will be truncated with ellipses ("..."). `"stacked"`: The label will appear above the radio regardless of the direction. The alignment of the label can be controlled with the `alignment` property. |
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

### value

|     |     |
| --- | --- |
| **Description** | the value of the radio. |
| **Attribute** | `value` |
| **Type** | `any` |
| **Default** | `undefined` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionBlur` | Emitted when the radio button loses focus. | `true` |
| `ionFocus` | Emitted when the radio button has focus. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `container` | The container for the radio mark. |
| `label` | The label text describing the radio. |
| `mark` | The checkmark or dot used to indicate the checked state. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--border-radius` | Border radius of the radio |
| `--color` | Color of the radio |
| `--color-checked` | Color of the checked radio |
| `--inner-border-radius` | Border radius of the inner checked radio |

| Name | Description |
| --- | --- |
| `--border-radius` | Border radius of the radio |
| `--color` | Color of the radio |
| `--color-checked` | Color of the checked radio |
| `--inner-border-radius` | Border radius of the inner checked radio |

## Slots

| Name | Description |
| --- | --- |
| \`\` | The label text to associate with the radio. Use the "labelPlacement" property to control where the label is placed relative to the radio. |
