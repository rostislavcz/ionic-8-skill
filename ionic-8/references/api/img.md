# Ionic Img Component

Source: https://ionicframework.com/docs/api/img

Sections: Basic Usage · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Img is a tag that will lazily load an image whenever the tag is in the viewport. This is extremely useful when generating a large list as images are only loaded when they're visible. The component uses [Intersection Observer](https://caniuse.com/#feat=intersectionobserver) internally, which is supported in most modern browsers, but falls back to a `setTimeout` when it is not supported.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-img
  src="https://docs-demo.ionic.io/assets/madison.jpg"
  alt="The Wisconsin State Capitol building in Madison, WI at night"
></ion-img>
```

```ts
import { Component } from '@angular/core';
import { IonImg } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonImg],
})
export class ExampleComponent {}
```

## Properties

### alt

|     |     |
| --- | --- |
| **Description** | This attribute defines the alternative text describing the image. Users will see this text displayed if the image URL is wrong, the image is not in one of the supported formats, or if the image is not yet downloaded. |
| **Attribute** | `alt` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### src

|     |     |
| --- | --- |
| **Description** | The image URL. This attribute is mandatory for the `<img>` element. |
| **Attribute** | `src` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionError` | Emitted when the img fails to load | `true` |
| `ionImgDidLoad` | Emitted when the image has finished loading | `true` |
| `ionImgWillLoad` | Emitted when the img src has been set | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `image` | The inner `img` element. |

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
