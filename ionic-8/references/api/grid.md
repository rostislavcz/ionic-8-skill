# Ionic Grid System

Source: https://ionicframework.com/docs/api/grid

Sections: Overview · Default Breakpoints · Basic Usage · Fixed Grid · Column Size · Column Offset · Column Push & Pull · Alignment · Customizing the Grid · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The grid is a powerful mobile-first flexbox system for building custom layouts. It is composed of three units — a grid, [row(s)](https://ionicframework.com/docs/api/row) and [column(s)](https://ionicframework.com/docs/api/col). Columns will expand to fill the row, and will resize to fit additional columns. It is based on a 12 column layout with different breakpoints based on the screen size. The number of columns can be customized using CSS.

## Overview

- Grids act as a container for all rows and columns. Grids take up the full width of their container,
but adding the `fixed` property will set the width based on the screen size, see [Fixed Grid](https://ionicframework.com/docs/api/grid#fixed-grid) below.
- Rows are horizontal groups of columns that line the columns up properly.
- Content should be placed within columns, and only columns may be immediate children of rows.
- The `size` property indicates the number of columns to use out of the default 12 per row.
So, `size="4"` can be added to a column in order to take up 1/3 of the grid, or 4 of the 12 columns.
- Columns without a value for size will automatically have equal widths. For example, four columns will each automatically be 25% wide.
- Column widths are set as a percentage, so they’re always fluid and sized relative to their parent element.
- There is padding between individual columns. However, the padding can be removed from the grid and
columns by adding the `ion-no-padding` class to the grid. See the [CSS Utilities](https://ionicframework.com/docs/layout/css-utilities) for more styles that can be applied to the grid.
- There are five grid tiers, one for each responsive breakpoint: all breakpoints (extra small), small, medium, large, and extra large.
- Grid tiers are based on minimum widths, meaning they apply to their tier and all those larger than them
(e.g., `size-sm="4"` applies to small, medium, large, and extra large devices).
- Grids can be customized via CSS variables. See [Customizing the Grid](https://ionicframework.com/docs/api/grid#customizing-the-grid).

## Default Breakpoints

The default breakpoints for the grid and the corresponding properties are defined in the table below. Breakpoint values can not be customized at this time. For more information on why they can't be customized, see [Variables in Media Queries](https://ionicframework.com/docs/theming/advanced#variables-in-media-queries).

| Name | Value | Width Property | Offset Property | Push Property | Pull Property | Description |
| --- | --- | --- | --- | --- | --- | --- |
| xs | 0 | `size` | `offset` | `push` | `pull` | Set columns when (min-width: 0) |
| sm | 576px | `sizeSm` | `offsetSm` | `pushSm` | `pullSm` | Set columns when (min-width: 576px) |
| md | 768px | `sizeMd` | `offsetMd` | `pushMd` | `pullMd` | Set columns when (min-width: 768px) |
| lg | 992px | `sizeLg` | `offsetLg` | `pushLg` | `pullLg` | Set columns when (min-width: 992px) |
| xl | 1200px | `sizeXl` | `offsetXl` | `pushXl` | `pullXl` | Set columns when (min-width: 1200px) |

## Basic Usage

By default, columns will take up equal width inside of a row for all devices and screen sizes.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>

<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
    <ion-col>4</ion-col>
    <ion-col>5</ion-col>
    <ion-col>6</ion-col>
  </ion-row>
</ion-grid>

<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
    <ion-col>4</ion-col>
    <ion-col>5</ion-col>
    <ion-col>6</ion-col>
    <ion-col>7</ion-col>
    <ion-col>8</ion-col>
    <ion-col>9</ion-col>
    <ion-col>10</ion-col>
    <ion-col>11</ion-col>
    <ion-col>12</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Fixed Grid

Grids take up 100% width of their container. By adding the `fixed` property to the grid, the width will be set based on the screen size. The width of the grid for each breakpoint is listed in the table below, but it can be customized. For more information, see [Customizing the Grid](https://ionicframework.com/docs/api/grid#customizing-the-grid). Open the below example in StackBlitz and resize the screen to see the grid width change.

| Name | Value | Description |
| --- | --- | --- |
| xs | 100% | Width is 100% for xs screens |
| sm | 540px | Set grid width to 540px when (min-width: 576px) |
| md | 720px | Set grid width to 720px when (min-width: 768px) |
| lg | 960px | Set grid width to 960px when (min-width: 992px) |
| xl | 1140px | Set grid width to 1140px when (min-width: 1200px) |

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-grid [fixed]="true">
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Column Size

Columns can be set to specific sizes to take up a certain number out of the total number of columns, or resize their width based on the content. The default number of columns is 12, but this can be customized. See the [Number of Columns](https://ionicframework.com/docs/api/grid#number-of-columns) section below for more information.

### Content-based size

By setting the `size` to `"auto"` the column can size itself based on the natural width of its content. This is necessary when setting a column to an absolute width, such as a specific number of pixels. The columns next to the auto-width column will resize to fill the row.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Column 1 has <code>size</code> set to <code>"auto"</code></b>
<ion-grid>
  <ion-row>
    <ion-col size="auto">1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>

<b>Column 3 contains an input and has <code>size</code> set to <code>"auto"</code></b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col size="auto">
      <ion-input placeholder="3"></ion-input>
    </ion-col>
    <ion-col>4</ion-col>
    <ion-col>5</ion-col>
    <ion-col>6</ion-col>
  </ion-row>
</ion-grid>

<b>Column 2 has <code>size</code> set to <code>"auto"</code> and a defined width</b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col size="auto">
      <div style="width: 150px">2</div>
    </ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;

  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonInput, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonInput, IonRow],
})
export class ExampleComponent {}
```

### Specified size

Set the `size` of a column and the others will automatically resize around it. If a size is specified on all of the columns and it doesn't add up to the total number of columns, there will be empty space after the columns.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Column 2 has <code>size</code> set to <code>"8"</code></b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col size="8">2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>

<b>Columns 3 & 4 have <code>size</code> set to <code>"3"</code></b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col size="3">3</ion-col>
    <ion-col size="3">4</ion-col>
    <ion-col>5</ion-col>
    <ion-col>6</ion-col>
  </ion-row>
</ion-grid>

<b>Columns 1 & 2 have <code>size</code> set to <code>"4"</code></b>
<ion-grid>
  <ion-row>
    <ion-col size="4">1</ion-col>
    <ion-col size="4">2</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

### Responsive size

The `size` property will change the column width for all [breakpoints](https://ionicframework.com/docs/api/grid#default-breakpoints). Column also provides several size properties with the breakpoint name appended to the end of "size". These properties can be used to change the width of the column based on the screen size. Open the below example in StackBlitz and resize the screen to see the column widths change.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Stacked for xs breakpoint, equal width for sm and up</b>
<ion-grid>
  <ion-row>
    <ion-col size="12" size-sm="3">1</ion-col>
    <ion-col size="12" size-sm="3">2</ion-col>
    <ion-col size="12" size-sm="3">3</ion-col>
    <ion-col size="12" size-sm="3">4</ion-col>
  </ion-row>
</ion-grid>

<b>Equal width until md breakpoint, last column takes full width for md and up</b>
<ion-grid>
  <ion-row>
    <ion-col size-md="6">1</ion-col>
    <ion-col size-md="6">2</ion-col>
    <ion-col size-md="12">3</ion-col>
  </ion-row>
</ion-grid>

<b>2 per row until md breakpoint, 3 per row for md, equal width for lg and up</b>
<ion-grid>
  <ion-row>
    <ion-col size="6" size-md="4" size-lg="2">1</ion-col>
    <ion-col size="6" size-md="4" size-lg="2">2</ion-col>
    <ion-col size="6" size-md="4" size-lg="2">3</ion-col>
    <ion-col size="6" size-md="4" size-lg="2">4</ion-col>
    <ion-col size="6" size-md="4" size-lg="2">5</ion-col>
    <ion-col size="6" size-md="4" size-lg="2">6</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Column Offset

Columns can be offset to shift to the right by a certain number of columns out of the total number of columns.

### Specified offset

Columns can be moved to the right by using the `offset` property. This property increases the left margin of the column by the number of specified columns. It also shifts the columns to the right of it, if any exist.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Column 2 has <code>offset</code> set to <code>"3"</code></b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col offset="3">2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>

<b>Column 5 has <code>offset</code> set to <code>"2"</code></b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
    <ion-col>4</ion-col>
    <ion-col offset="2">5</ion-col>
  </ion-row>
</ion-grid>

<b>Column 1 has <code>offset</code> set to <code>"4"</code></b>
<ion-grid>
  <ion-row>
    <ion-col size="2" offset="4">1</ion-col>
    <ion-col size="2">2</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

### Responsive offset

The `offset` property will change the column's left margin for all [breakpoints](https://ionicframework.com/docs/api/grid#default-breakpoints). Column also provides several offset properties with the breakpoint name appended to the end of "offset". These properties can be used to change the offset of the column based on the screen size. Open the below example in StackBlitz and resize the screen to see the column offsets change.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>No offset for xs breakpoint, offset 1st column for sm and up</b>
<ion-grid>
  <ion-row>
    <ion-col offset-sm="2">1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
    <ion-col>4</ion-col>
    <ion-col>5</ion-col>
  </ion-row>
</ion-grid>

<b>No offset for xs breakpoint, offset last 3 columns for md and up</b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col offset-md="2">2</ion-col>
    <ion-col offset-md="2">3</ion-col>
    <ion-col offset-md="2">4</ion-col>
  </ion-row>
</ion-grid>

<b>Offset all columns by 6 for xs breakpoint, offset by 4 for md, offset by 2 for lg and up</b>
<ion-grid>
  <ion-row>
    <ion-col offset="6" offset-md="4" offset-lg="2">1</ion-col>
    <ion-col offset="6" offset-md="4" offset-lg="2">2</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Column Push & Pull

Columns can be pushed to to the right or pulled to the left by a certain number of columns out of the total number of columns.

### Specified push & pull

Reorder the columns by adding the `push` and `pull` properties. These properties adjust the `left` and `right` of the columns by the specified number of columns making it easy to reorder columns. This will cause columns to overlap if they are shifted to where another column is positioned.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Column 1 has <code>push</code> set to <code>"4"</code> and column 2 has <code>pull</code> set to <code>"4"</code></b>
<ion-grid>
  <ion-row>
    <ion-col push="4">1</ion-col>
    <ion-col pull="4">2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>

<b
  >Column 2 has <code>push</code> set to <code>"4"</code> and column 3 & 4 have <code>pull</code> set to
  <code>"2"</code></b
>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col push="4">2</ion-col>
    <ion-col pull="2">3</ion-col>
    <ion-col pull="2">4</ion-col>
    <ion-col>5</ion-col>
    <ion-col>6</ion-col>
  </ion-row>
</ion-grid>

<b>Column 1 has <code>push</code> set to <code>"3"</code> and column 2 has <code>pull</code> set to <code>"9"</code></b>
<ion-grid>
  <ion-row>
    <ion-col size="9" push="3">1</ion-col>
    <ion-col size="3" pull="9">2</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

### Responsive push & pull

The `push` and `pull` properties will change the column's position for all [breakpoints](https://ionicframework.com/docs/api/grid#default-breakpoints). Column also provides several `push` and `pull` properties with the breakpoint name appended to the end of "push" / "pull". These properties can be used to change the position of the column based on the screen size. Open the below example in StackBlitz and resize the screen to see the column positions change.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>No change for xs breakpoint, push 1st column & pull 2nd column for sm and up</b>
<ion-grid>
  <ion-row>
    <ion-col push-sm="6">1</ion-col>
    <ion-col pull-sm="6">2</ion-col>
  </ion-row>
</ion-grid>

<b>No change for xs breakpoint, push middle columns & pull last column for md and up</b>
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col push-md="3">2</ion-col>
    <ion-col push-md="3">3</ion-col>
    <ion-col pull-md="6">4</ion-col>
  </ion-row>
</ion-grid>

<b>Switch first and last 3 columns for xs breakpoints, reverse columns for lg and up</b>
<ion-grid>
  <ion-row>
    <ion-col push="6" push-lg="10">1</ion-col>
    <ion-col push="6" push-lg="6">2</ion-col>
    <ion-col push="6" push-lg="2">3</ion-col>
    <ion-col pull="6" pull-lg="2">4</ion-col>
    <ion-col pull="6" pull-lg="6">5</ion-col>
    <ion-col pull="6" pull-lg="10">6</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Alignment

### Vertical Alignment

All columns can be vertically aligned inside of a row by adding different classes to the row. For a list of available classes, see [css utilities](https://ionicframework.com/docs/layout/css-utilities#flex-container-properties).

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Columns aligned at the top</b>
<ion-grid>
  <ion-row class="ion-align-items-start">
    <ion-col> 1 </ion-col>
    <ion-col> 2 </ion-col>
    <ion-col> 3 </ion-col>
    <ion-col>
      4 <br />
      # <br />
      # <br />
      # <br />
    </ion-col>
  </ion-row>
</ion-grid>

<b>Columns aligned at the center</b>
<ion-grid>
  <ion-row class="ion-align-items-center">
    <ion-col> 1 </ion-col>
    <ion-col> 2 </ion-col>
    <ion-col> 3 </ion-col>
    <ion-col>
      4 <br />
      # <br />
      # <br />
      # <br />
    </ion-col>
  </ion-row>
</ion-grid>

<b>Columns aligned at the bottom</b>
<ion-grid>
  <ion-row class="ion-align-items-end">
    <ion-col> 1 </ion-col>
    <ion-col> 2 </ion-col>
    <ion-col> 3 </ion-col>
    <ion-col>
      4 <br />
      # <br />
      # <br />
      # <br />
    </ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

### Horizontal Alignment

All columns can be horizontally aligned inside of a row by adding different classes to the row. For a list of available classes, see [css utilities](https://ionicframework.com/docs/layout/css-utilities#flex-container-properties).

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Columns aligned at the start</b>
<ion-grid>
  <ion-row class="ion-justify-content-start">
    <ion-col size="3"> 1 </ion-col>
    <ion-col size="3"> 2 </ion-col>
  </ion-row>
</ion-grid>

<b>Columns aligned at the center</b>
<ion-grid>
  <ion-row class="ion-justify-content-center">
    <ion-col size="3"> 1 </ion-col>
    <ion-col size="3"> 2 </ion-col>
  </ion-row>
</ion-grid>

<b>Columns aligned at the end</b>
<ion-grid>
  <ion-row class="ion-justify-content-end">
    <ion-col size="3"> 1 </ion-col>
    <ion-col size="3"> 2 </ion-col>
  </ion-row>
</ion-grid>

<b>Columns aligned with space around</b>
<ion-grid>
  <ion-row class="ion-justify-content-around">
    <ion-col size="3"> 1 </ion-col>
    <ion-col size="3"> 2 </ion-col>
  </ion-row>
</ion-grid>

<b>Columns aligned with space between</b>
<ion-grid>
  <ion-row class="ion-justify-content-between">
    <ion-col size="3"> 1 </ion-col>
    <ion-col size="3"> 2 </ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Customizing the Grid

Using our built-in CSS variables, it’s possible to customize the predefined grid attributes. Change the values of the padding, the number of columns, and more.

### Fixed Width

The width of a fixed grid can be set for all breakpoints with the `--ion-grid-width` CSS variable. To override individual breakpoints, use the `--ion-grid-width-{breakpoint}` CSS variables. The default value for each of the breakpoints can be found in the [Fixed Grid](https://ionicframework.com/docs/api/grid#fixed-grid) section. Open the below example in StackBlitz and resize the screen to see the grid width change.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-grid [fixed]="true">
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-grid {
  --ion-grid-width: 50%;

  --ion-grid-width-xs: 50%;
  --ion-grid-width-sm: 288px;
  --ion-grid-width-md: 384px;
  --ion-grid-width-lg: 480px;
  --ion-grid-width-xl: 570px;
}

ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

### Number of Columns

The number of grid columns can be modified with the `--ion-grid-columns` CSS variable. By default there are 12 grid columns, but this can be changed to any positive integer and be used to calculate the width of each individual column.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<b>Total number of columns is set to <code>6</code>, column <code>size</code> is set to <code>1</code></b>
<ion-grid>
  <ion-row>
    <ion-col size="1">1</ion-col>
    <ion-col size="1">2</ion-col>
    <ion-col size="1">3</ion-col>
    <ion-col size="1">4</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-grid {
  --ion-grid-columns: 6;
}

ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

### Padding

The padding on the grid container can be set for all breakpoints with the `--ion-grid-padding` CSS variable. To override individual breakpoints, use the `--ion-grid-padding-{breakpoint}` CSS variables.

The padding on the columns can be set for all breakpoints with the `--ion-grid-column-padding` CSS variable. To override individual breakpoints, use the `--ion-grid-column-padding-{breakpoint}` CSS variables.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-grid>
  <ion-row>
    <ion-col>1</ion-col>
    <ion-col>2</ion-col>
    <ion-col>3</ion-col>
  </ion-row>
</ion-grid>
```

```css
ion-grid {
  --ion-grid-padding: 20px;

  --ion-grid-padding-xs: 20px;
  --ion-grid-padding-sm: 20px;
  --ion-grid-padding-md: 20px;
  --ion-grid-padding-lg: 20px;
  --ion-grid-padding-xl: 20px;

  --ion-grid-column-padding: 30px;

  --ion-grid-column-padding-xs: 30px;
  --ion-grid-column-padding-sm: 30px;
  --ion-grid-column-padding-md: 30px;
  --ion-grid-column-padding-lg: 30px;
  --ion-grid-column-padding-xl: 30px;
}

ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
```

```ts
import { Component } from '@angular/core';
import { IonCol, IonGrid, IonRow } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCol, IonGrid, IonRow],
})
export class ExampleComponent {}
```

## Properties

### fixed

|     |     |
| --- | --- |
| **Description** | If `true`, the grid will have a fixed width based on the screen size. |
| **Attribute** | `fixed` |
| **Type** | `boolean` |
| **Default** | `false` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

| Name | Description |
| --- | --- |
| `--ion-grid-padding` | Padding for the Grid |
| `--ion-grid-padding-lg` | Padding for the Grid on lg screens |
| `--ion-grid-padding-md` | Padding for the Grid on md screens |
| `--ion-grid-padding-sm` | Padding for the Grid on sm screens |
| `--ion-grid-padding-xl` | Padding for the Grid on xl screens |
| `--ion-grid-padding-xs` | Padding for the Grid on xs screens |
| `--ion-grid-width` | Width of the fixed Grid |
| `--ion-grid-width-lg` | Width of the fixed Grid on lg screens |
| `--ion-grid-width-md` | Width of the fixed Grid on md screens |
| `--ion-grid-width-sm` | Width of the fixed Grid on sm screens |
| `--ion-grid-width-xl` | Width of the fixed Grid on xl screens |
| `--ion-grid-width-xs` | Width of the fixed Grid on xs screens |

## Slots

No slots available for this component.
