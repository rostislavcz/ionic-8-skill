# Ionic Item Group

Source: https://ionicframework.com/docs/api/item-group

Sections: Basic Usage · Sliding Items · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

Item groups are containers that organize similar [items](https://ionicframework.com/docs/api/item) together. They can contain [item dividers](https://ionicframework.com/docs/api/item-divider) to divide the items into multiple sections. They can also be used to group [sliding items](https://ionicframework.com/docs/api/item-sliding).

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item-group>
  <ion-item-divider>
    <ion-label>A</ion-label>
  </ion-item-divider>

  <ion-item>
    <ion-label>Angola</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Argentina</ion-label>
  </ion-item>
  <ion-item lines="none">
    <ion-label>Armenia</ion-label>
  </ion-item>
</ion-item-group>

<ion-item-group>
  <ion-item-divider>
    <ion-label>B</ion-label>
  </ion-item-divider>

  <ion-item>
    <ion-label>Bangladesh</ion-label>
  </ion-item>
  <ion-item>
    <ion-label>Belarus</ion-label>
  </ion-item>
  <ion-item lines="none">
    <ion-label>Belgium</ion-label>
  </ion-item>
</ion-item-group>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonItemDivider, IonItemGroup, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonItemDivider, IonItemGroup, IonLabel],
})
export class ExampleComponent {}
```

## Sliding Items

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item-group>
  <ion-item-divider>
    <ion-label> Fruits </ion-label>
  </ion-item-divider>

  <ion-item-sliding>
    <ion-item>
      <ion-label> Grapes </ion-label>
    </ion-item>
    <ion-item-options>
      <ion-item-option> Favorite </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item>
      <ion-label> Apples </ion-label>
    </ion-item>
    <ion-item-options>
      <ion-item-option> Favorite </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item lines="none">
      <ion-label> Bananas </ion-label>
    </ion-item>
    <ion-item-options>
      <ion-item-option> Favorite </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>
</ion-item-group>

<ion-item-group>
  <ion-item-divider>
    <ion-label> Vegetables </ion-label>
  </ion-item-divider>

  <ion-item-sliding>
    <ion-item>
      <ion-label> Carrots </ion-label>
    </ion-item>
    <ion-item-options>
      <ion-item-option> Favorite </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item>
      <ion-label> Broccoli </ion-label>
    </ion-item>
    <ion-item-options>
      <ion-item-option> Favorite </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>

  <ion-item-sliding>
    <ion-item lines="none">
      <ion-label> Celery </ion-label>
    </ion-item>
    <ion-item-options>
      <ion-item-option> Favorite </ion-item-option>
    </ion-item-options>
  </ion-item-sliding>
</ion-item-group>
```

```ts
import { Component } from '@angular/core';
import {
  IonItem,
  IonItemDivider,
  IonItemGroup,
  IonItemOption,
  IonItemOptions,
  IonItemSliding,
  IonLabel,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonItemDivider, IonItemGroup, IonItemOption, IonItemOptions, IonItemSliding, IonLabel],
})
export class ExampleComponent {}
```

## Properties

No properties available for this component.

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
