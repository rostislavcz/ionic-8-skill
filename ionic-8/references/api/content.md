# Ionic Content Overview

Source: https://ionicframework.com/docs/api/content

Sections: Basic Usage · Header & Footer · Fullscreen Content · Fixed Content · Scroll Methods · Scroll Events · Theming · Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The content component provides an easy to use content area with some useful methods
to control the scrollable area. There should only be one content in a single
view.

Content, along with many other Ionic components, can be customized to modify its padding, margin, and more using the global styles provided in the [CSS Utilities](https://ionicframework.com/docs/layout/css-utilities) or by individually styling it using CSS and the available [CSS Custom Properties](https://ionicframework.com/docs/api/content#css-custom-properties).

## Basic Usage

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content class="ion-padding">
  <h1>Heading 1</h1>
  <h2>Heading 2</h2>
  <h3>Heading 3</h3>
  <h4>Heading 4</h4>
  <h5>Heading 5</h5>
  <h6>Heading 6</h6>

  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import { IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent],
})
export class ExampleComponent {}
```

## Header & Footer

Content can be the only top-level component in a page, or it can be used alongside a [header](https://ionicframework.com/docs/api/header), [footer](https://ionicframework.com/docs/api/footer), or both. When used with a header or footer, it will adjust its size to fill the remaining height.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title> Header </ion-title>
  </ion-toolbar>
</ion-header>
<ion-content class="ion-padding">
  <h1>Heading 1</h1>
  <h2>Heading 2</h2>
  <h3>Heading 3</h3>
  <h4>Heading 4</h4>
  <h5>Heading 5</h5>
  <h6>Heading 6</h6>

  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-footer>
  <ion-toolbar>
    <ion-title> Footer </ion-title>
  </ion-toolbar>
</ion-footer>
```

```ts
import { Component } from '@angular/core';
import { IonContent, IonFooter, IonHeader, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent, IonFooter, IonHeader, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Fullscreen Content

By default, content fills the space between a [header](https://ionicframework.com/docs/api/header) and [footer](https://ionicframework.com/docs/api/footer) but does not go behind them. In certain cases, it may be desired to have the content scroll behind the header and footer, such as when the `translucent` property is set on either of them, or `opacity` is set on the toolbar. This can be achieved by setting the `fullscreen` property on the content to `true`.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title> Header </ion-title>
  </ion-toolbar>
</ion-header>
<ion-content [fullscreen]="true" class="ion-padding">
  <h1>Scroll the content and notice that the text goes behind the header and footer.</h1>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean sed tellus nec mauris auctor dignissim fermentum in
    risus. Sed nec convallis sapien, id tincidunt enim. Mauris ornare eleifend nunc id mattis. Fusce augue diam,
    sagittis nec posuere at, consectetur tempor lectus. Nulla at lectus eget mauris iaculis malesuada mollis sed neque.
    Curabitur et risus tristique, malesuada mauris finibus, elementum massa. Proin lacinia mauris quis ligula blandit
    ullamcorper. Donec ut posuere lorem. In volutpat magna vitae tellus posuere pulvinar. Nam varius ligula justo, nec
    placerat lacus pharetra ac. Aenean massa orci, tristique in nisl ut, aliquet consectetur libero. Etiam luctus
    placerat vulputate. Aliquam ipsum massa, porttitor at mollis ut, pretium sit amet mi. In neque mauris, placerat et
    neque vel, tempor interdum dolor. Suspendisse gravida malesuada tellus, vel dapibus nisl dignissim vel. Cras ut
    nulla sit amet erat malesuada euismod vel a nulla.
  </p>
  <p>
    Phasellus sit amet iaculis odio, eget feugiat erat. Etiam sit amet turpis sit amet massa viverra maximus. Aenean
    venenatis porttitor pharetra. Fusce vulputate urna purus, vel efficitur mauris auctor non. Etiam libero odio,
    sodales in velit a, faucibus venenatis erat. Ut convallis sit amet urna in ultrices. Cras neque est, vehicula sed
    lorem ac, placerat commodo elit. Praesent turpis metus, elementum eget iaculis ac, elementum in odio. Nunc et elit
    faucibus, condimentum mauris consequat, ornare dolor. Sed ac lectus a est blandit tempor. Etiam lobortis tristique
    maximus.
  </p>
  <p>
    Quisque tempus porttitor massa, vel condimentum risus finibus a. Aliquam viverra maximus odio, id ornare justo
    tristique ac. Mauris euismod arcu eget neque sagittis rutrum. Ut vehicula porta lacus nec lobortis. Vestibulum et
    elit ultrices, lacinia metus in, lobortis est. Vivamus nisi justo, venenatis sit amet arcu ac, congue faucibus
    justo. Duis volutpat posuere enim, vel sagittis elit dictum et. Sed et congue mauris. Nam venenatis venenatis risus,
    ac condimentum neque sagittis sed. In eget nulla ultricies urna sollicitudin posuere. Aenean sagittis congue mauris.
    Proin nec libero mi. In hac habitasse platea dictumst. Praesent nunc nulla, dictum id molestie sed, pretium vitae
    turpis.
  </p>
  <p>
    Pellentesque vitae dapibus lacus. Nullam suscipit ornare risus quis ullamcorper. Nullam feugiat, sapien et sodales
    fermentum, risus ligula semper risus, id efficitur ligula augue id diam. Suspendisse lobortis est sit amet quam
    facilisis, ut vestibulum nunc dignissim. Donec at vestibulum magna. Maecenas maximus pretium metus. Phasellus congue
    sapien vel odio imperdiet, nec mollis odio euismod. Sed vel eros ut sapien accumsan condimentum vehicula vitae
    lectus. Donec sed efficitur lorem. Aenean tristique mi libero, eleifend tincidunt libero finibus at. Mauris
    condimentum fermentum rutrum.
  </p>
  <p>
    Nulla tristique ultricies suscipit. Donec non ornare elit. Vivamus id pretium mauris, nec sagittis leo. Fusce mattis
    eget est id sollicitudin. Suspendisse dictum sem magna, in imperdiet metus suscipit et. Suspendisse enim enim,
    venenatis et orci eu, suscipit congue lacus. Praesent vel ligula non eros tempor interdum. Proin justo orci,
    ultricies vitae diam sed, semper consectetur ligula. Aenean finibus ante velit, nec efficitur libero cursus cursus.
    Duis mi nunc, imperdiet sed condimentum vel, porttitor ut lacus. Quisque dui ipsum, vehicula sed vestibulum id,
    semper vel libero. Suspendisse tincidunt mollis condimentum. Nulla facilisi. Etiam neque nisl, egestas nec iaculis
    sed, tristique faucibus sem. Sed mollis dui quis ligula cursus rutrum.
  </p>
</ion-content>
<ion-footer>
  <ion-toolbar>
    <ion-title> Footer </ion-title>
  </ion-toolbar>
</ion-footer>
```

```css
ion-toolbar {
  --opacity: 0.5;
}
```

```ts
import { Component } from '@angular/core';
import { IonContent, IonFooter, IonHeader, IonTitle, IonToolbar } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent, IonFooter, IonHeader, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Fixed Content

To place elements outside of the scrollable area, assign them to the `fixed` slot. Doing so will [absolutely position](https://developer.mozilla.org/en-US/docs/Web/CSS/position#absolute_positioning) the element to the top left of the content. In order to change the position of the element, it can be styled using the [top, right, bottom, and left](https://developer.mozilla.org/en-US/docs/Web/CSS/position) CSS properties.

The `fixedSlotPlacement` property is used to determine if content in the `fixed` slot is placed before or after the main content in the DOM. When set to `before`, fixed slot content will be placed before the main content and will therefore receive keyboard focus before the main content receives keyboard focus. This can be useful when the main content contains an infinitely-scrolling list, preventing a [FAB](https://ionicframework.com/docs/api/fab) or other fixed content from being reachable by pressing the tab key.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-content class="ion-padding">
  <h1>Scroll the content and notice that the fixed button does not scroll.</h1>

  <ion-button>Normal Button</ion-button>
  <ion-button slot="fixed">Fixed Button</ion-button>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean sed tellus nec mauris auctor dignissim fermentum in
    risus. Sed nec convallis sapien, id tincidunt enim. Mauris ornare eleifend nunc id mattis. Fusce augue diam,
    sagittis nec posuere at, consectetur tempor lectus. Nulla at lectus eget mauris iaculis malesuada mollis sed neque.
    Curabitur et risus tristique, malesuada mauris finibus, elementum massa. Proin lacinia mauris quis ligula blandit
    ullamcorper. Donec ut posuere lorem. In volutpat magna vitae tellus posuere pulvinar. Nam varius ligula justo, nec
    placerat lacus pharetra ac. Aenean massa orci, tristique in nisl ut, aliquet consectetur libero. Etiam luctus
    placerat vulputate. Aliquam ipsum massa, porttitor at mollis ut, pretium sit amet mi. In neque mauris, placerat et
    neque vel, tempor interdum dolor. Suspendisse gravida malesuada tellus, vel dapibus nisl dignissim vel. Cras ut
    nulla sit amet erat malesuada euismod vel a nulla.
  </p>
  <p>
    Phasellus sit amet iaculis odio, eget feugiat erat. Etiam sit amet turpis sit amet massa viverra maximus. Aenean
    venenatis porttitor pharetra. Fusce vulputate urna purus, vel efficitur mauris auctor non. Etiam libero odio,
    sodales in velit a, faucibus venenatis erat. Ut convallis sit amet urna in ultrices. Cras neque est, vehicula sed
    lorem ac, placerat commodo elit. Praesent turpis metus, elementum eget iaculis ac, elementum in odio. Nunc et elit
    faucibus, condimentum mauris consequat, ornare dolor. Sed ac lectus a est blandit tempor. Etiam lobortis tristique
    maximus.
  </p>
  <p>
    Quisque tempus porttitor massa, vel condimentum risus finibus a. Aliquam viverra maximus odio, id ornare justo
    tristique ac. Mauris euismod arcu eget neque sagittis rutrum. Ut vehicula porta lacus nec lobortis. Vestibulum et
    elit ultrices, lacinia metus in, lobortis est. Vivamus nisi justo, venenatis sit amet arcu ac, congue faucibus
    justo. Duis volutpat posuere enim, vel sagittis elit dictum et. Sed et congue mauris. Nam venenatis venenatis risus,
    ac condimentum neque sagittis sed. In eget nulla ultricies urna sollicitudin posuere. Aenean sagittis congue mauris.
    Proin nec libero mi. In hac habitasse platea dictumst. Praesent nunc nulla, dictum id molestie sed, pretium vitae
    turpis.
  </p>
  <p>
    Pellentesque vitae dapibus lacus. Nullam suscipit ornare risus quis ullamcorper. Nullam feugiat, sapien et sodales
    fermentum, risus ligula semper risus, id efficitur ligula augue id diam. Suspendisse lobortis est sit amet quam
    facilisis, ut vestibulum nunc dignissim. Donec at vestibulum magna. Maecenas maximus pretium metus. Phasellus congue
    sapien vel odio imperdiet, nec mollis odio euismod. Sed vel eros ut sapien accumsan condimentum vehicula vitae
    lectus. Donec sed efficitur lorem. Aenean tristique mi libero, eleifend tincidunt libero finibus at. Mauris
    condimentum fermentum rutrum.
  </p>
  <p>
    Nulla tristique ultricies suscipit. Donec non ornare elit. Vivamus id pretium mauris, nec sagittis leo. Fusce mattis
    eget est id sollicitudin. Suspendisse dictum sem magna, in imperdiet metus suscipit et. Suspendisse enim enim,
    venenatis et orci eu, suscipit congue lacus. Praesent vel ligula non eros tempor interdum. Proin justo orci,
    ultricies vitae diam sed, semper consectetur ligula. Aenean finibus ante velit, nec efficitur libero cursus cursus.
    Duis mi nunc, imperdiet sed condimentum vel, porttitor ut lacus. Quisque dui ipsum, vehicula sed vestibulum id,
    semper vel libero. Suspendisse tincidunt mollis condimentum. Nulla facilisi. Etiam neque nisl, egestas nec iaculis
    sed, tristique faucibus sem. Sed mollis dui quis ligula cursus rutrum.
  </p>
</ion-content>
```

```css
ion-button[slot='fixed'] {
  top: 50%;
  right: 20px;
}
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonContent],
})
export class ExampleComponent {}
```

## Scroll Methods

Content provides [methods](https://ionicframework.com/docs/api/content#methods) that can be called to scroll the content to the bottom, top, or to a specific point. They can be passed a `duration` in order to smoothly transition instead of instantly changing the position.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content class="ion-padding">
  <h1>Click on the buttons to scroll the content.</h1>

  <ion-button expand="block" (click)="scrollToBottom()">Scroll to Bottom</ion-button>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean sed tellus nec mauris auctor dignissim fermentum in
    risus. Sed nec convallis sapien, id tincidunt enim. Mauris ornare eleifend nunc id mattis. Fusce augue diam,
    sagittis nec posuere at, consectetur tempor lectus. Nulla at lectus eget mauris iaculis malesuada mollis sed neque.
    Curabitur et risus tristique, malesuada mauris finibus, elementum massa. Proin lacinia mauris quis ligula blandit
    ullamcorper. Donec ut posuere lorem. In volutpat magna vitae tellus posuere pulvinar. Nam varius ligula justo, nec
    placerat lacus pharetra ac. Aenean massa orci, tristique in nisl ut, aliquet consectetur libero. Etiam luctus
    placerat vulputate. Aliquam ipsum massa, porttitor at mollis ut, pretium sit amet mi. In neque mauris, placerat et
    neque vel, tempor interdum dolor. Suspendisse gravida malesuada tellus, vel dapibus nisl dignissim vel. Cras ut
    nulla sit amet erat malesuada euismod vel a nulla.
  </p>
  <p>
    Phasellus sit amet iaculis odio, eget feugiat erat. Etiam sit amet turpis sit amet massa viverra maximus. Aenean
    venenatis porttitor pharetra. Fusce vulputate urna purus, vel efficitur mauris auctor non. Etiam libero odio,
    sodales in velit a, faucibus venenatis erat. Ut convallis sit amet urna in ultrices. Cras neque est, vehicula sed
    lorem ac, placerat commodo elit. Praesent turpis metus, elementum eget iaculis ac, elementum in odio. Nunc et elit
    faucibus, condimentum mauris consequat, ornare dolor. Sed ac lectus a est blandit tempor. Etiam lobortis tristique
    maximus.
  </p>
  <p>
    Quisque tempus porttitor massa, vel condimentum risus finibus a. Aliquam viverra maximus odio, id ornare justo
    tristique ac. Mauris euismod arcu eget neque sagittis rutrum. Ut vehicula porta lacus nec lobortis. Vestibulum et
    elit ultrices, lacinia metus in, lobortis est. Vivamus nisi justo, venenatis sit amet arcu ac, congue faucibus
    justo. Duis volutpat posuere enim, vel sagittis elit dictum et. Sed et congue mauris. Nam venenatis venenatis risus,
    ac condimentum neque sagittis sed. In eget nulla ultricies urna sollicitudin posuere. Aenean sagittis congue mauris.
    Proin nec libero mi. In hac habitasse platea dictumst. Praesent nunc nulla, dictum id molestie sed, pretium vitae
    turpis.
  </p>
  <p>
    Pellentesque vitae dapibus lacus. Nullam suscipit ornare risus quis ullamcorper. Nullam feugiat, sapien et sodales
    fermentum, risus ligula semper risus, id efficitur ligula augue id diam. Suspendisse lobortis est sit amet quam
    facilisis, ut vestibulum nunc dignissim. Donec at vestibulum magna. Maecenas maximus pretium metus. Phasellus congue
    sapien vel odio imperdiet, nec mollis odio euismod. Sed vel eros ut sapien accumsan condimentum vehicula vitae
    lectus. Donec sed efficitur lorem. Aenean tristique mi libero, eleifend tincidunt libero finibus at. Mauris
    condimentum fermentum rutrum.
  </p>
  <p>
    Nulla tristique ultricies suscipit. Donec non ornare elit. Vivamus id pretium mauris, nec sagittis leo. Fusce mattis
    eget est id sollicitudin. Suspendisse dictum sem magna, in imperdiet metus suscipit et. Suspendisse enim enim,
    venenatis et orci eu, suscipit congue lacus. Praesent vel ligula non eros tempor interdum. Proin justo orci,
    ultricies vitae diam sed, semper consectetur ligula. Aenean finibus ante velit, nec efficitur libero cursus cursus.
    Duis mi nunc, imperdiet sed condimentum vel, porttitor ut lacus. Quisque dui ipsum, vehicula sed vestibulum id,
    semper vel libero. Suspendisse tincidunt mollis condimentum. Nulla facilisi. Etiam neque nisl, egestas nec iaculis
    sed, tristique faucibus sem. Sed mollis dui quis ligula cursus rutrum.
  </p>

  <ion-button expand="block" (click)="scrollToTop()">Scroll to Top</ion-button>
</ion-content>
```

```ts
import { Component, ViewChild } from '@angular/core';
import { IonButton, IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonContent],
})
export class ExampleComponent {
  @ViewChild(IonContent) content!: IonContent;

  scrollToBottom() {
    // Passing a duration to the method makes it so the scroll slowly
    // goes to the bottom instead of instantly
    this.content.scrollToBottom(500);
  }

  scrollToTop() {
    // Passing a duration to the method makes it so the scroll slowly
    // goes to the top instead of instantly
    this.content.scrollToTop(500);
  }
}
```

## Scroll Events

Scroll events are disabled by default for content due to performance. However, they can be enabled by setting `scrollEvents` to `true`. This is necessary before listening to any of the scroll [events](https://ionicframework.com/docs/api/content#events).

`Console`

`Console messages will appear here when logged from the example above.`

- src/app/example.component.html
- src/app/example.component.ts

```html
<!-- Scroll events are disabled by default for content for performance reasons, enable them to listen to them -->
<!-- Casting $event to $any is a temporary fix for this bug https://github.com/ionic-team/ionic-framework/issues/24245 -->
<ion-content
  [scrollEvents]="true"
  (ionScrollStart)="handleScrollStart()"
  (ionScroll)="handleScroll($any($event))"
  (ionScrollEnd)="handleScrollEnd()"
  class="ion-padding"
>
  <h1>Scroll to fire the scroll events and view them in the console.</h1>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean sed tellus nec mauris auctor dignissim fermentum in
    risus. Sed nec convallis sapien, id tincidunt enim. Mauris ornare eleifend nunc id mattis. Fusce augue diam,
    sagittis nec posuere at, consectetur tempor lectus. Nulla at lectus eget mauris iaculis malesuada mollis sed neque.
    Curabitur et risus tristique, malesuada mauris finibus, elementum massa. Proin lacinia mauris quis ligula blandit
    ullamcorper. Donec ut posuere lorem. In volutpat magna vitae tellus posuere pulvinar. Nam varius ligula justo, nec
    placerat lacus pharetra ac. Aenean massa orci, tristique in nisl ut, aliquet consectetur libero. Etiam luctus
    placerat vulputate. Aliquam ipsum massa, porttitor at mollis ut, pretium sit amet mi. In neque mauris, placerat et
    neque vel, tempor interdum dolor. Suspendisse gravida malesuada tellus, vel dapibus nisl dignissim vel. Cras ut
    nulla sit amet erat malesuada euismod vel a nulla.
  </p>
  <p>
    Phasellus sit amet iaculis odio, eget feugiat erat. Etiam sit amet turpis sit amet massa viverra maximus. Aenean
    venenatis porttitor pharetra. Fusce vulputate urna purus, vel efficitur mauris auctor non. Etiam libero odio,
    sodales in velit a, faucibus venenatis erat. Ut convallis sit amet urna in ultrices. Cras neque est, vehicula sed
    lorem ac, placerat commodo elit. Praesent turpis metus, elementum eget iaculis ac, elementum in odio. Nunc et elit
    faucibus, condimentum mauris consequat, ornare dolor. Sed ac lectus a est blandit tempor. Etiam lobortis tristique
    maximus.
  </p>
  <p>
    Quisque tempus porttitor massa, vel condimentum risus finibus a. Aliquam viverra maximus odio, id ornare justo
    tristique ac. Mauris euismod arcu eget neque sagittis rutrum. Ut vehicula porta lacus nec lobortis. Vestibulum et
    elit ultrices, lacinia metus in, lobortis est. Vivamus nisi justo, venenatis sit amet arcu ac, congue faucibus
    justo. Duis volutpat posuere enim, vel sagittis elit dictum et. Sed et congue mauris. Nam venenatis venenatis risus,
    ac condimentum neque sagittis sed. In eget nulla ultricies urna sollicitudin posuere. Aenean sagittis congue mauris.
    Proin nec libero mi. In hac habitasse platea dictumst. Praesent nunc nulla, dictum id molestie sed, pretium vitae
    turpis.
  </p>
  <p>
    Pellentesque vitae dapibus lacus. Nullam suscipit ornare risus quis ullamcorper. Nullam feugiat, sapien et sodales
    fermentum, risus ligula semper risus, id efficitur ligula augue id diam. Suspendisse lobortis est sit amet quam
    facilisis, ut vestibulum nunc dignissim. Donec at vestibulum magna. Maecenas maximus pretium metus. Phasellus congue
    sapien vel odio imperdiet, nec mollis odio euismod. Sed vel eros ut sapien accumsan condimentum vehicula vitae
    lectus. Donec sed efficitur lorem. Aenean tristique mi libero, eleifend tincidunt libero finibus at. Mauris
    condimentum fermentum rutrum.
  </p>
  <p>
    Nulla tristique ultricies suscipit. Donec non ornare elit. Vivamus id pretium mauris, nec sagittis leo. Fusce mattis
    eget est id sollicitudin. Suspendisse dictum sem magna, in imperdiet metus suscipit et. Suspendisse enim enim,
    venenatis et orci eu, suscipit congue lacus. Praesent vel ligula non eros tempor interdum. Proin justo orci,
    ultricies vitae diam sed, semper consectetur ligula. Aenean finibus ante velit, nec efficitur libero cursus cursus.
    Duis mi nunc, imperdiet sed condimentum vel, porttitor ut lacus. Quisque dui ipsum, vehicula sed vestibulum id,
    semper vel libero. Suspendisse tincidunt mollis condimentum. Nulla facilisi. Etiam neque nisl, egestas nec iaculis
    sed, tristique faucibus sem. Sed mollis dui quis ligula cursus rutrum.
  </p>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import { IonContent, ScrollDetail } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent],
})
export class ExampleComponent {
  handleScrollStart() {
    console.log('scroll start');
  }

  handleScroll(event: CustomEvent<ScrollDetail>) {
    console.log('scroll', JSON.stringify(event.detail));
  }

  handleScrollEnd() {
    console.log('scroll end');
  }
}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-content color="primary" class="ion-padding">
  <h1>Primary content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="secondary" class="ion-padding">
  <h1>Secondary content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="tertiary" class="ion-padding">
  <h1>Tertiary content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="success" class="ion-padding">
  <h1>Success content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="warning" class="ion-padding">
  <h1>Warning content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="danger" class="ion-padding">
  <h1>Danger content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="light" class="ion-padding">
  <h1>Light content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="medium" class="ion-padding">
  <h1>Medium content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
<ion-content color="dark" class="ion-padding">
  <h1>Dark content</h1>
  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import { IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent],
})
export class ExampleComponent {}
```

### CSS Shadow Parts

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-content class="ion-padding">
  <h1>Heading 1</h1>
  <h2>Heading 2</h2>
  <h3>Heading 3</h3>
  <h4>Heading 4</h4>
  <h5>Heading 5</h5>
  <h6>Heading 6</h6>

  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
```

```css
ion-content::part(background) {
  background: #d31373;
}

ion-content::part(scroll) {
  color: #fff;
}
```

```ts
import { Component } from '@angular/core';
import { IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-content class="ion-padding">
  <h1>Heading 1</h1>
  <h2>Heading 2</h2>
  <h3>Heading 3</h3>
  <h4>Heading 4</h4>
  <h5>Heading 5</h5>
  <h6>Heading 6</h6>

  <p>Here's a small text description for the content. Nothing more, nothing less.</p>
</ion-content>
```

```css
ion-content {
  --background: #d31373;
  --color: #fff;
}
```

```ts
import { Component } from '@angular/core';
import { IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent],
})
export class ExampleComponent {}
```

### Safe Area Padding

The content component will not automatically apply padding to any of its sides to account for the [safe area](https://ionicframework.com/docs/theming/advanced#safe-area-padding). This is because the content component is often used in conjunction with other components that apply their own padding, such as [headers](https://ionicframework.com/docs/api/header) and [footers](https://ionicframework.com/docs/api/footer). However, if the content component is being used on its own, it may be desired to apply padding to the safe area. This can be done through CSS by using the `--ion-safe-area-(dir)` variables described in [Application Variables](https://ionicframework.com/docs/theming/advanced#application-variables).

The most common use case for this is to apply padding to the top of the content to account for the status bar. This can be done by setting the `padding-top` property to the value of the `--ion-safe-area-top` variable.

```css
ion-content::part(scroll) {
  padding-top: var(--ion-safe-area-top, 0);
}
```

Another common use case is to apply padding to the left side of the content to account for the notch when the device is in landscape mode and the notch is on the left side. This can be done by setting the `padding-left` property to the value of the `--ion-safe-area-left` variable.

```css
ion-content::part(scroll) {
  padding-left: var(--ion-safe-area-left, 0);
}
```

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts
- src/global.css

```html
<ion-content>
  <span>Here's a small text description for the content. Nothing more, nothing less.</span>
</ion-content>
```

```css
ion-content::part(scroll) {
  padding-top: var(--ion-safe-area-top, 0);
  padding-bottom: var(--ion-safe-area-bottom, 0);
  padding-left: var(--ion-safe-area-left, 0);
  padding-right: var(--ion-safe-area-right, 0);
}
```

```ts
import { Component } from '@angular/core';
import { IonContent } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent],
})
export class ExampleComponent {}
```

```css
:root {
  /**
   * Setting the variables for DEMO purposes only.
   * Values will be set automatically when building an iOS or Android app.
   */
  --ion-safe-area-top: 20px;
  --ion-safe-area-bottom: 20px;
  --ion-safe-area-left: 20px;
  --ion-safe-area-right: 20px;
}
```

## Interfaces

### ScrollBaseDetail

```typescript
interface ScrollBaseDetail {
  isScrolling: boolean;
}
```

### ScrollDetail

```typescript
interface ScrollDetail extends GestureDetail, ScrollBaseDetail {
  scrollTop: number;
  scrollLeft: number;
}
```

### ScrollBaseCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing on the `ionScrollStart` and `ionScrollEnd` events.

```typescript
interface ScrollBaseCustomEvent extends CustomEvent {
  detail: ScrollBaseDetail;
  target: HTMLIonContentElement;
}
```

### ScrollCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing on the `ionScroll` event.

```typescript
interface ScrollCustomEvent extends ScrollBaseCustomEvent {
  detail: ScrollDetail;
}
```

## Properties

### color

|     |     |
| --- | --- |
| **Description** | The color to use from your application's color palette. Default options are: `"primary"`, `"secondary"`, `"tertiary"`, `"success"`, `"warning"`, `"danger"`, `"light"`, `"medium"`, and `"dark"`. For more information on colors, see [theming](https://ionicframework.com/docs/theming/basics). |
| **Attribute** | `color` |
| **Type** | `"danger" ｜ "dark" ｜ "light" ｜ "medium" ｜ "primary" ｜ "secondary" ｜ "success" ｜ "tertiary" ｜ "warning" ｜ string ｜ undefined` |
| **Default** | `undefined` |

### fixedSlotPlacement

|     |     |
| --- | --- |
| **Description** | Controls where the fixed content is placed relative to the main content in the DOM. This can be used to control the order in which fixed elements receive keyboard focus. For example, if a FAB in the fixed slot should receive keyboard focus before the main page content, set this property to `'before'`. |
| **Attribute** | `fixed-slot-placement` |
| **Type** | `"after" ｜ "before"` |
| **Default** | `'after'` |

### forceOverscroll

|     |     |
| --- | --- |
| **Description** | If `true` and the content does not cause an overflow scroll, the scroll interaction will cause a bounce. If the content exceeds the bounds of ionContent, nothing will change. Note, this does not disable the system bounce on iOS. That is an OS level setting. |
| **Attribute** | `force-overscroll` |
| **Type** | `boolean ｜ undefined` |
| **Default** | `undefined` |

### fullscreen

|     |     |
| --- | --- |
| **Description** | If `true`, the content will scroll behind the headers and footers. This effect can easily be seen by setting the toolbar to transparent. |
| **Attribute** | `fullscreen` |
| **Type** | `boolean` |
| **Default** | `false` |

### scrollEvents

|     |     |
| --- | --- |
| **Description** | Because of performance reasons, ionScroll events are disabled by default, in order to enable them and start listening from (ionScroll), set this property to `true`. |
| **Attribute** | `scroll-events` |
| **Type** | `boolean` |
| **Default** | `false` |

### scrollX

|     |     |
| --- | --- |
| **Description** | If you want to enable the content scrolling in the X axis, set this property to `true`. |
| **Attribute** | `scroll-x` |
| **Type** | `boolean` |
| **Default** | `false` |

### scrollY

|     |     |
| --- | --- |
| **Description** | If you want to disable the content scrolling in the Y axis, set this property to `false`. |
| **Attribute** | `scroll-y` |
| **Type** | `boolean` |
| **Default** | `true` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionScroll` | Emitted while scrolling. This event is disabled by default. Set `scrollEvents` to `true` to enable. | `true` |
| `ionScrollEnd` | Emitted when the scroll has ended. This event is disabled by default. Set `scrollEvents` to `true` to enable. | `true` |
| `ionScrollStart` | Emitted when the scroll has started. This event is disabled by default. Set `scrollEvents` to `true` to enable. | `true` |

## Methods

### getScrollElement

|     |     |
| --- | --- |
| **Description** | Get the element where the actual scrolling takes place. This element can be used to subscribe to `scroll` events or manually modify `scrollTop`. However, it's recommended to use the API provided by `ion-content`:<br>i.e. Using `ionScroll`, `ionScrollStart`, `ionScrollEnd` for scrolling events and `scrollToPoint()` to scroll the content into a certain point. |
| **Signature** | `getScrollElement() => Promise<HTMLElement>` |

### scrollByPoint

|     |     |
| --- | --- |
| **Description** | Scroll by a specified X/Y distance in the component. |
| **Signature** | `scrollByPoint(x: number, y: number, duration: number) => Promise<void>` |
| **Parameters** | **x**: The amount to scroll by on the horizontal axis.<br>**y**: The amount to scroll by on the vertical axis.<br>**duration**: The amount of time to take scrolling by that amount. |

### scrollToBottom

|     |     |
| --- | --- |
| **Description** | Scroll to the bottom of the component. |
| **Signature** | `scrollToBottom(duration?: number) => Promise<void>` |
| **Parameters** | **duration**: The amount of time to take scrolling to the bottom. Defaults to `0`. |

### scrollToPoint

|     |     |
| --- | --- |
| **Description** | Scroll to a specified X/Y location in the component. |
| **Signature** | `scrollToPoint(x: number ｜ undefined ｜ null, y: number ｜ undefined ｜ null, duration?: number) => Promise<void>` |
| **Parameters** | **x**: The point to scroll to on the horizontal axis.<br>**y**: The point to scroll to on the vertical axis.<br>**duration**: The amount of time to take scrolling to that point. Defaults to `0`. |

### scrollToTop

|     |     |
| --- | --- |
| **Description** | Scroll to the top of the component. |
| **Signature** | `scrollToTop(duration?: number) => Promise<void>` |
| **Parameters** | **duration**: The amount of time to take scrolling to the top. Defaults to `0`. |

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `background` | The background of the content. |
| `scroll` | The scrollable container of the content. |

## CSS Custom Properties

| Name | Description |
| --- | --- |
| `--background` | Background of the content |
| `--color` | Color of the content |
| `--keyboard-offset` | Keyboard offset of the content |
| `--offset-bottom` | Offset bottom of the content |
| `--offset-top` | Offset top of the content |
| `--padding-bottom` | Bottom padding of the content |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the content |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the content |
| `--padding-top` | Top padding of the content |

## Slots

| Name | Description |
| --- | --- |
| \`\` | Content is placed in the scrollable area if provided without a slot. |
| `fixed` | Should be used for fixed content that should not scroll. |
