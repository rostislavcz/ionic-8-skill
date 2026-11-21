# Ionic Ripple Effect

Source: https://ionicframework.com/docs/api/ripple-effect

Sections: Basic Usage · Type · Customizing · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The ripple effect component adds the [Material Design ink ripple interaction effect](https://material.io/develop/web/supporting/ripple). This component can only be used inside of an `<ion-app>` and can be added inside of any element.

It's important to set [relative positioning](https://developer.mozilla.org/en-US/docs/Web/CSS/position) on the parent element because the ripple effect is absolutely positioned and will cover its closest parent that has relative positioning. The parent element should also be given the `ion-activatable` class, which tells the ripple effect that the element is clickable. It's recommended to add `overflow: hidden` to the parent element if the ripple is overflowing its container.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<div class="wrapper">
  <b>Click on a shape to see the ripple</b>

  <div class="ion-activatable ripple-parent rectangle">
    <ion-ripple-effect></ion-ripple-effect>
  </div>

  <div class="ion-activatable ripple-parent rounded-rectangle">
    <ion-ripple-effect></ion-ripple-effect>
  </div>

  <div class="ion-activatable ripple-parent circle">
    <ion-ripple-effect></ion-ripple-effect>
  </div>
</div>
```

```css
.wrapper {
  display: flex;
  flex-wrap: wrap;

  align-items: center;
  justify-content: space-between;
  text-align: center;

  height: 300px;
  width: 300px;

  margin: 0 auto;
}

b {
  width: 100%;
}

.ripple-parent {
  position: relative;
  overflow: hidden;

  border: 1px solid #ddd;
}

.rectangle {
  width: 300px;
  height: 150px;
}

.rounded-rectangle {
  width: 185px;
  height: 65px;
  border-radius: 8px;
}

.circle {
  width: 90px;
  height: 90px;
  border-radius: 50%;
}
```

```ts
import { Component } from '@angular/core';
import { IonRippleEffect } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRippleEffect],
})
export class ExampleComponent {}
```

## Type

There are two types of ripple effects: `"bounded"` and `"unbounded"`. The default type, `"bounded"`, will expand the ripple effect from the click position outwards. To add a ripple effect that always starts in the center of the element and expands in a circle, set the type to `"unbounded"`.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<div class="wrapper">
  <b>Click on a shape to see the ripple</b>

  <div class="ion-activatable ripple-parent rounded-rectangle">
    Bounded
    <ion-ripple-effect></ion-ripple-effect>
  </div>

  <div class="ion-activatable ripple-parent circle">
    Unbounded
    <ion-ripple-effect type="unbounded"></ion-ripple-effect>
  </div>
</div>
```

```css
.wrapper {
  display: flex;
  flex-wrap: wrap;

  align-items: center;
  justify-content: space-between;
  text-align: center;

  height: 170px;
  width: 400px;

  margin: 0 auto;
}

b {
  width: 100%;
}

.ripple-parent {
  display: flex;
  align-items: center;
  justify-content: center;

  position: relative;
  overflow: hidden;

  border: 1px solid #ddd;

  user-select: none;
}

.rounded-rectangle {
  width: 250px;
  height: 75px;
  border-radius: 8px;
}

.circle {
  width: 120px;
  height: 120px;
  border-radius: 50%;
}
```

```ts
import { Component } from '@angular/core';
import { IonRippleEffect } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRippleEffect],
})
export class ExampleComponent {}
```

## Customizing

The ripple can be customized to a different color through CSS. By default the ripple color is set to inherit the text color, which is generally the body color. This can be changed by setting the CSS `color` on the parent or the ripple effect itself.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<div class="wrapper">
  <b>Click on a shape to see the ripple</b>

  <div class="ion-activatable ripple-parent custom-parent">
    Custom Parent Color
    <ion-ripple-effect></ion-ripple-effect>
  </div>

  <div class="ion-activatable ripple-parent">
    Custom Ripple Color
    <ion-ripple-effect class="custom-ripple"></ion-ripple-effect>
  </div>
</div>
```

```css
.wrapper {
  display: flex;
  flex-wrap: wrap;

  align-items: center;
  justify-content: space-between;
  text-align: center;

  height: 170px;
  width: 400px;

  margin: 0 auto;
}

b {
  width: 100%;
}

.ripple-parent {
  display: flex;
  align-items: center;
  justify-content: center;

  position: relative;
  overflow: hidden;

  border: 1px solid #ddd;

  user-select: none;

  width: 100%;
  height: 50px;
  border-radius: 8px;
}

.custom-parent {
  color: #de1e7e;
}

.custom-ripple {
  color: #501ace;
}
```

```ts
import { Component } from '@angular/core';
import { IonRippleEffect } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonRippleEffect],
})
export class ExampleComponent {}
```

## Properties

### type

|     |     |
| --- | --- |
| **Description** | Sets the type of ripple-effect:<br>\- `bounded`: the ripple effect expands from the user's click position - `unbounded`: the ripple effect expands from the center of the button and overflows the container.<br>NOTE: Surfaces for bounded ripples should have the overflow property set to hidden, while surfaces for unbounded ripples should have it set to visible. |
| **Attribute** | `type` |
| **Type** | `"bounded" ｜ "unbounded"` |
| **Default** | `'bounded'` |

## Events

No events available for this component.

## Methods

### addRipple

|     |     |
| --- | --- |
| **Description** | Adds the ripple effect to the parent element. |
| **Signature** | `addRipple(x: number, y: number) => Promise<() => void>` |
| **Parameters** | **x**: The horizontal coordinate of where the ripple should start.<br>**y**: The vertical coordinate of where the ripple should start. |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
