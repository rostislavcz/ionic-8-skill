# Avatar Component Guide

Source: https://ionicframework.com/docs/api/avatar

Sections: Basic Usage · Chip Avatar · Item Avatar · Theming · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Avatars are circular components that usually wrap an image or icon. They can be used to represent a person or an object.

Avatars can be used by themselves or inside of any element. If placed inside of an `ion-chip` or `ion-item`, the avatar will resize to fit the parent component. To position an avatar on the left or right side of an item, set the slot to `start` or `end`, respectively.

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-avatar>
  <img alt="Silhouette of a person's head" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
</ion-avatar>
```

```ts
import { Component } from '@angular/core';
import { IonAvatar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar],
})
export class ExampleComponent {}
```

## Chip Avatar

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-chip>
  <ion-avatar>
    <img alt="Silhouette of a person's head" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
  </ion-avatar>
  <ion-label>Chip Avatar</ion-label>
</ion-chip>
```

```ts
import { Component } from '@angular/core';
import { IonAvatar, IonChip, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonChip, IonLabel],
})
export class ExampleComponent {}
```

## Item Avatar

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-avatar slot="start">
    <img alt="Silhouette of a person's head" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
  </ion-avatar>
  <ion-label>Item Avatar</ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonAvatar, IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonItem, IonLabel],
})
export class ExampleComponent {}
```

## Theming

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-avatar>
  <img alt="Silhouette of a person's head" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
</ion-avatar>
```

```css
ion-avatar {
  --border-radius: 4px;
}
```

```ts
import { Component } from '@angular/core';
import { IonAvatar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar],
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

- iOS
- MD

| Name | Description |
| --- | --- |
| `--border-radius` | Border radius of the avatar and inner image |

| Name | Description |
| --- | --- |
| `--border-radius` | Border radius of the avatar and inner image |

## Slots

No slots available for this component.
