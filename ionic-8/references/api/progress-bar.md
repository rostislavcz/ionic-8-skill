# Ionic Progress Bars

Source: https://ionicframework.com/docs/api/progress-bar

Sections: Determinate · Indeterminate · Progress Bars in Toolbars · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Progress bars inform users about the status of ongoing processes, such as loading an app, submitting a form, or saving updates. There are two types of progress bars: `determinate` and `indeterminate`.

## Determinate

Determinate is the default type. It should be used when the percentage of an operation is known. The progress is represented by setting the `value` property. This can be used to show the progress increasing from 0 to 100% of the track.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-progress-bar [value]="progress"></ion-progress-bar>
```

```ts
import { Component } from '@angular/core';
import { IonProgressBar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonProgressBar],
})
export class ExampleComponent {
  public progress = 0;

  constructor() {
    setInterval(() => {
      this.progress += 0.01;

      // Reset the progress bar when it reaches 100%
      // to continuously show the demo
      if (this.progress > 1) {
        setTimeout(() => {
          this.progress = 0;
        }, 1000);
      }
    }, 50);
  }
}
```

### Buffer

If the `buffer` property is set, a buffer stream will show with animated circles to indicate activity. The value of the `buffer` property will also be represented by how much visible track there is. If the value of `buffer` is less than the `value` property, there will be no visible track. If `buffer` is equal to `1` then the buffer stream will be hidden.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-progress-bar [buffer]="buffer" [value]="progress"></ion-progress-bar>
```

```ts
import { Component } from '@angular/core';
import { IonProgressBar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonProgressBar],
})
export class ExampleComponent {
  public buffer = 0.06;
  public progress = 0;

  constructor() {
    setInterval(() => {
      this.buffer += 0.06;
      this.progress += 0.06;

      // Reset the progress bar when it reaches 100%
      // to continuously show the demo
      if (this.progress > 1) {
        setTimeout(() => {
          this.buffer = 0.06;
          this.progress = 0;
        }, 1000);
      }
    }, 1000);
  }
}
```

## Indeterminate

The indeterminate type should be used when it is unknown how long the process will take. The progress bar is not tied to the `value`, instead it continually slides along the track until the process is complete.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-progress-bar type="indeterminate"></ion-progress-bar>
```

```ts
import { Component } from '@angular/core';
import { IonProgressBar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonProgressBar],
})
export class ExampleComponent {}
```

## Progress Bars in Toolbars

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Toolbar</ion-title>
    <ion-progress-bar type="indeterminate"></ion-progress-bar>
  </ion-toolbar>
</ion-header>
```

```ts
import { Component } from '@angular/core';
import { IonHeader, IonProgressBar, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonHeader, IonProgressBar, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-progress-bar type="indeterminate" color="primary"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="secondary"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="tertiary"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="success"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="warning"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="danger"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="light"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="medium"></ion-progress-bar>
<ion-progress-bar type="indeterminate" color="dark"></ion-progress-bar>
```

```ts
import { Component } from '@angular/core';
import { IonProgressBar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonProgressBar],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-progress-bar value=".25" buffer=".5"></ion-progress-bar> <ion-progress-bar type="indeterminate"></ion-progress-bar>
```

```css
ion-progress-bar {
  --background: #f3e895;
  --progress-background: #09c567;
}
```

```ts
import { Component } from '@angular/core';
import { IonProgressBar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonProgressBar],
})
export class ExampleComponent {}
```

### CSS Shadow Parts

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-progress-bar value=".25" buffer=".5"></ion-progress-bar> <ion-progress-bar type="indeterminate"></ion-progress-bar>
```

```css
ion-progress-bar::part(track) {
  background: #f3e895;
}

ion-progress-bar::part(progress) {
  background: #09c567;
}

ion-progress-bar::part(stream) {
  background-image: radial-gradient(ellipse at center, #e475f3 0%, #e475f3 30%, transparent 30%);
}
```

```ts
import { Component } from '@angular/core';
import { IonProgressBar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonProgressBar],
})
export class ExampleComponent {}
```

## Properties

### buffer

|     |     |
| --- | --- |
| **Description** | If the buffer and value are smaller than 1, the buffer circles will show. The buffer should be between \[0, 1\]. |
| **Attribute** | `buffer` |
| **Type** | `number` |
| **Default** | `1` |

### color

|     |     |
| --- | --- |
| **Description** | The color to use from your application's color palette. Default options are: `"primary"`, `"secondary"`, `"tertiary"`, `"success"`, `"warning"`, `"danger"`, `"light"`, `"medium"`, and `"dark"`. For more information on colors, see [theming](https://ionicframework.com/docs/theming/basics). |
| **Attribute** | `color` |
| **Type** | `"danger" ｜ "dark" ｜ "light" ｜ "medium" ｜ "primary" ｜ "secondary" ｜ "success" ｜ "tertiary" ｜ "warning" ｜ string ｜ undefined` |
| **Default** | `undefined` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

### reversed

|     |     |
| --- | --- |
| **Description** | If true, reverse the progress bar direction. |
| **Attribute** | `reversed` |
| **Type** | `boolean` |
| **Default** | `false` |

### type

|     |     |
| --- | --- |
| **Description** | The state of the progress bar, based on if the time the process takes is known or not. Default options are: `"determinate"` (no animation), `"indeterminate"` (animate from left to right). |
| **Attribute** | `type` |
| **Type** | `"determinate" ｜ "indeterminate"` |
| **Default** | `'determinate'` |

### value

|     |     |
| --- | --- |
| **Description** | The value determines how much of the active bar should display when the `type` is `"determinate"`. The value should be between \[0, 1\]. |
| **Attribute** | `value` |
| **Type** | `number` |
| **Default** | `0` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `progress` | The progress bar that shows the current value when `type` is `"determinate"` and slides back and forth when `type` is `"indeterminate"`. |
| `stream` | The animated circles that appear while buffering. This only shows when `buffer` is set and `type` is `"determinate"`. |
| `track` | The track bar behind the progress bar. If the `buffer` property is set and `type` is `"determinate"` the track will be the width of the `buffer` value. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the progress track, or the buffer bar if `buffer` is set |
| `--progress-background` | Background of the progress bar representing the current value |

| Name | Description |
| --- | --- |
| `--background` | Background of the progress track, or the buffer bar if `buffer` is set |
| `--progress-background` | Background of the progress bar representing the current value |

## Slots

No slots available for this component.
