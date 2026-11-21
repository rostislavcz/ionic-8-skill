# Ionic Item Component

Source: https://ionicframework.com/docs/api/item

Sections: Basic Usage · Content Types · Clickable Items · Detail Arrows · Item Lines · Buttons in Items · Item Inputs · Theming · Guidelines · Accessibility · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

Items are elements that can contain text, icons, avatars, images, inputs, and any other native or custom elements. Items should only be used as rows in a [List](https://ionicframework.com/docs/api/list) with other items. Items can be swiped, deleted, reordered, edited, and more.

## Basic Usage

Items left align text and wrap when the text is wider than the item. We can modify this behavior using the CSS Utilities provided by Ionic Framework, such as using `.ion-text-nowrap` in the below example. See the [CSS Utilities Documentation](https://ionicframework.com/docs/layout/css-utilities) for more classes that can be added to an item to transform the text.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-label>Basic Item</ion-label>
</ion-item>

<ion-item>
  <ion-label>
    Multi-line text that should wrap when it is too long to fit on one line. Lorem ipsum dolor sit amet, consectetur
    adipiscing elit.
  </ion-label>
</ion-item>

<ion-item>
  <ion-label class="ion-text-nowrap">
    Multi-line text that should ellipsis when it is too long to fit on one line. Lorem ipsum dolor sit amet, consectetur
    adipiscing elit.
  </ion-label>
</ion-item>

<ion-item>
  <ion-label>
    <h1>H1 Heading</h1>
    <p>Paragraph</p>
  </ion-label>
</ion-item>

<ion-item>
  <ion-label>
    <h2>H2 Heading</h2>
    <p>Paragraph</p>
  </ion-label>
</ion-item>

<ion-item>
  <ion-label>
    <h3>H3 Heading</h3>
    <p>Paragraph</p>
  </ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

## Content Types

While items in a list take many forms, they typically support 5 different content types: supporting visuals, text, metadata, actions, and controls. However, not all of these content types should be used together at the same time. The following guide shows the different content types as well as how to properly utilize them in an application.

### Supporting Visuals

Supporting visuals are decorative icons or other adornments for an item. Common examples of supporting visuals are [Avatars](https://ionicframework.com/docs/api/avatar), [Icons](https://ionicframework.com/docs/api/icon), and [Thumbnails](https://ionicframework.com/docs/api/thumbnail). Since this content is not required to understand the intent of the item, it is typically hidden from screen readers using `aria-hidden="true"`.

If a visual is required to interact with the item, such as an icon button, then the visual is an [action](https://ionicframework.com/docs/api/item#actions) not a supporting visual.

Supporting visuals should be rendered in a consistent manner. This makes the information in each item easier to parse.

![A list with several items. Each item has an icon and visible text describing the item. The icon in each item is rendered at the start of the line.](https://ionicframework.com/docs/img/item/visuals-do.jpg)

Do

Align visuals on the same side in a list

![A list with several items. Each item has an icon and visible text describing the item. Some icons are rendered at the start of the line, and some icons are rendered at the end of the line](https://ionicframework.com/docs/img/item/visuals-do-not.jpg)

Don't

Don't render visuals with different alignments in the same list

In the example below, we are creating two lists with supporting visuals. The first list uses icons, and the second list uses avatars. The visuals are decorative, so they all have `aria-hidden="true"`. Additionally, they are presented consistently in the `start` slot.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-list>
  <ion-item>
    <ion-icon aria-hidden="true" name="airplane" slot="start"></ion-icon>
    <ion-label>Airplane Mode</ion-label>
  </ion-item>
  <ion-item>
    <ion-icon aria-hidden="true" name="wifi" slot="start"></ion-icon>
    <ion-label>Wi-Fi</ion-label>
  </ion-item>
  <ion-item>
    <ion-icon aria-hidden="true" name="bluetooth" slot="start"></ion-icon>
    <ion-label>Bluetooth</ion-label>
  </ion-item>
  <ion-item>
    <ion-icon aria-hidden="true" name="call" slot="start"></ion-icon>
    <ion-label>Cellular</ion-label>
  </ion-item>
</ion-list>

<ion-list>
  <ion-item>
    <ion-avatar aria-hidden="true" slot="start">
      <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
    </ion-avatar>
    <ion-label>Huey</ion-label>
  </ion-item>
  <ion-item>
    <ion-avatar aria-hidden="true" slot="start">
      <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
    </ion-avatar>
    <ion-label>Dewey</ion-label>
  </ion-item>
  <ion-item>
    <ion-avatar aria-hidden="true" slot="start">
      <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
    </ion-avatar>
    <ion-label>Louie</ion-label>
  </ion-item>
  <ion-item>
    <ion-avatar aria-hidden="true" slot="start">
      <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
    </ion-avatar>
    <ion-label>Fooie</ion-label>
  </ion-item>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { IonAvatar, IonIcon, IonItem, IonLabel, IonList } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { airplane, bluetooth, call, wifi } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonAvatar, IonIcon, IonItem, IonLabel, IonList],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ airplane, bluetooth, call, wifi });
  }
}
```

### Text

The text content type includes form control labels or other visible text. This text serves to indicate the intent of the item. Try to keep the text short and to the point.

If you find that you need a few more sentences to clarify the item's purpose, consider moving the additional sentences to a [Note](https://ionicframework.com/docs/api/note) at the bottom of the list. Adding the item to its own list makes it clear which item the text is associated with.

![A list with an item that contains a checked checkbox indicating the user wants to receive emails. Text describing how often the user will receive emails as well as how to unsubscribe from emails is placed underneath the list.](https://ionicframework.com/docs/img/item/long-text-do.jpg)

Do

Move long text outside of the list

![A list with an item that contains a checked checkbox indicating the user wants to receive emails. Text describing how often the user will receive emails as well as how to unsubscribe from emails is placed as a single paragraph inline with the checkbox, making the text hard to read and increasing the height of the item.](https://ionicframework.com/docs/img/item/long-text-do-not.jpg)

Don't

Don't try to fit long text in an item

In the example below, we are creating a list with different types of text. The "First Name" and "Last Name" labels serve to indicate what to type into the text inputs.

The "Allow Notifications" label on the toggle has additional text underneath it that notes users can disable notifications. Since this text is short, it is placed inside of the item.

Below that list is another list containing a textarea with a [Note](https://ionicframework.com/docs/api/note) containing long text underneath. The textarea was placed in its own list to make it apparent that the long text is associated with the textarea and not any other fields.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Example</ion-title>
  </ion-toolbar>
</ion-header>
<ion-content color="light">
  <ion-list [inset]="true">
    <ion-item>
      <ion-input label="First Name"></ion-input>
    </ion-item>
    <ion-item>
      <ion-input label="Last Name"></ion-input>
    </ion-item>
    <ion-item>
      <ion-toggle>
        <ion-label>Allow Notifications</ion-label>
        <ion-note color="medium">Unsubscribe at any time</ion-note>
      </ion-toggle>
    </ion-item>
  </ion-list>

  <ion-list [inset]="true">
    <ion-item>
      <ion-textarea label="Comments" labelPlacement="floating" rows="5"></ion-textarea>
    </ion-item>
  </ion-list>

  <ion-note color="medium" class="ion-margin-horizontal">
    Your comments will be kept anonymous and will only be used to improve the reliability of our products.</ion-note
  >
</ion-content>
```

```css
ion-note {
  display: block;
}
```

```ts
import { Component } from '@angular/core';
import {
  IonContent,
  IonHeader,
  IonInput,
  IonItem,
  IonLabel,
  IonList,
  IonNote,
  IonTextarea,
  IonTitle,
  IonToggle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [\
    IonContent,\
    IonHeader,\
    IonInput,\
    IonItem,\
    IonLabel,\
    IonList,\
    IonNote,\
    IonTextarea,\
    IonTitle,\
    IonToggle,\
    IonToolbar,\
  ],
})
export class ExampleComponent {}
```

### Metadata

Metadata provides additional context for an item such as status text or counts. Components like [Badge](https://ionicframework.com/docs/api/badge) or [Note](https://ionicframework.com/docs/api/note) are great ways of showing metadata.

Limit the amount of metadata you include to only the most relevant information.

![A list that contains several items, each representing a different to-do list. A count of how many tasks in each to-do list is placed at the end of each item.](https://ionicframework.com/docs/img/item/metadata-relevant-do.jpg)

Do

Add only the most important metadata

![A list that contains several items, each representing a different to-do list. Two counts are placed at the end of each item: One count that states the total number of tasks, and another count that states the total number of tasks that are due today.](https://ionicframework.com/docs/img/item/metadata-relevant-do-not.jpg)

Don't

Don't add too much metadata as it can overwhelm or confuse the user.

Developers should also consider how important the metadata is. Drawing attention to the metadata may be helpful for the user or it may distract them from the more important information depending on the use case.

![A list that contains several items, each representing a different to-do list. A count of how many tasks in each to-do list is placed at the end of each item.](https://ionicframework.com/docs/img/item/metadata-relevant-do.jpg)

Do

Prioritize the most important content.

![A list that contains several items, each representing a different to-do list. A count of how many tasks in each to-do list is placed at the end of each item. However, the count is highlighted in blue which draws the user's attention away from the name of the to-do list.](https://ionicframework.com/docs/img/item/metadata-important-caution.jpg)

Caution

Prioritized metadata may distract from other important content.

In the example below, we are creating two lists with different kinds of metadata. The first list uses [Note](https://ionicframework.com/docs/api/note) to show how many tasks are in each to-do list.

The second list mimics the iOS Mail app to show an inbox. This list makes use of custom metadata including an "unread message" indicator in the "start" slot as well as a timestamp and custom detail icon in the "end" slot. The "unread message" indicator is highlighted in blue to draw the user's attention to the unread messages, while the timestamp is more subtle.

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Example</ion-title>
  </ion-toolbar>
</ion-header>
<ion-content color="light">
  <ion-list [inset]="true">
    <ion-item [button]="true">
      <ion-icon color="danger" slot="start" name="list-circle" size="large"></ion-icon>
      <ion-label>General</ion-label>
      <ion-note slot="end">6</ion-note>
    </ion-item>
    <ion-item [button]="true">
      <ion-icon color="tertiary" slot="start" name="list-circle" size="large"></ion-icon>
      <ion-label>Shopping</ion-label>
      <ion-note slot="end">15</ion-note>
    </ion-item>
    <ion-item [button]="true">
      <ion-icon color="success" slot="start" name="list-circle" size="large"></ion-icon>
      <ion-label>Cleaning</ion-label>
      <ion-note slot="end">3</ion-note>
    </ion-item>
    <ion-item [button]="true">
      <ion-icon color="warning" slot="start" name="list-circle" size="large"></ion-icon>
      <ion-label>Reminders</ion-label>
      <ion-note slot="end">8</ion-note>
    </ion-item>
  </ion-list>

  <ion-list [inset]="true">
    <ion-item [button]="true" detail="false">
      <div class="unread-indicator-wrapper" slot="start">
        <div class="unread-indicator"></div>
      </div>
      <ion-label>
        <strong>Rick Astley</strong>
        <ion-text>Never Gonna Give You Up</ion-text><br />
        <ion-note color="medium" class="ion-text-wrap">
          Never gonna give you up Never gonna let you down Never gonna run...
        </ion-note>
      </ion-label>
      <div class="metadata-end-wrapper" slot="end">
        <ion-note color="medium">06:11</ion-note>
        <ion-icon color="medium" name="chevron-forward"></ion-icon>
      </div>
    </ion-item>
    <ion-item [button]="true" detail="false">
      <div class="unread-indicator-wrapper" slot="start"></div>
      <ion-label>
        <strong>Ionitron</strong>
        <ion-text>I have become sentient</ion-text><br />
        <ion-note color="medium" class="ion-text-wrap">That is all.</ion-note>
      </ion-label>
      <div class="metadata-end-wrapper" slot="end">
        <ion-note color="medium">03:44</ion-note>
        <ion-icon color="medium" name="chevron-forward"></ion-icon>
      </div>
    </ion-item>
    <ion-item [button]="true" detail="false">
      <div class="unread-indicator-wrapper" slot="start">
        <div class="unread-indicator"></div>
      </div>
      <ion-label>
        <strong>Steam</strong>
        <ion-text>Game Store Sale</ion-text><br />
        <ion-note color="medium" class="ion-text-wrap">
          That game you added to your wish list 2 years ago is now on sale!
        </ion-note>
      </ion-label>
      <div class="metadata-end-wrapper" slot="end">
        <ion-note color="medium">Yesterday</ion-note>
        <ion-icon color="medium" name="chevron-forward"></ion-icon>
      </div>
    </ion-item>
    <ion-item [button]="true" detail="false">
      <div class="unread-indicator-wrapper" slot="start"></div>
      <ion-label>
        <strong>Ionic</strong>
        <ion-text>Announcing Ionic 7.0</ion-text><br />
        <ion-note color="medium" class="ion-text-wrap">This version is one more than Ionic 6!</ion-note>
      </ion-label>
      <div class="metadata-end-wrapper" slot="end">
        <ion-note color="medium">Yesterday</ion-note>
        <ion-icon color="medium" name="chevron-forward"></ion-icon>
      </div>
    </ion-item>
  </ion-list>
</ion-content>
```

```css
.unread-indicator {
  background: var(--ion-color-primary);

  width: 10px;
  height: 10px;

  border-radius: 100%;

  position: absolute;

  inset-inline-start: 12px;
  top: 12px;
}

.metadata-end-wrapper {
  position: absolute;

  top: 10px;
  inset-inline-end: 10px;

  font-size: 0.8rem;

  display: flex;
  align-items: center;
}

ion-label strong {
  display: block;

  max-width: calc(100% - 60px);

  overflow: hidden;

  text-overflow: ellipsis;
}

ion-label ion-note {
  font-size: 0.9rem;
}
```

```ts
import { Component } from '@angular/core';
import {
  IonContent,
  IonHeader,
  IonIcon,
  IonItem,
  IonLabel,
  IonList,
  IonNote,
  IonText,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { chevronForward, listCircle } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonContent, IonHeader, IonIcon, IonItem, IonLabel, IonList, IonNote, IonText, IonTitle, IonToolbar],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ chevronForward, listCircle });
  }
}
```

### Actions

Actions are interactive elements that do something when you activate them. An item can have multiple actions displayed on a line. However, developers should ensure that each action's tap target is large enough to be usable.

Developers should avoid creating [nested interactives](https://dequeuniversity.com/rules/axe/4.4/nested-interactive) which can break the user experience with screen readers. For example, developers should avoid adding a button inside the main content of the Item if the `button` property is set to `true`.

Actions can be added by using the [Item Sliding](https://ionicframework.com/docs/api/item-sliding) component. Actions can also be placed directly inside of the Item without the use of Item Sliding, but this should be limited to no more than 2 actions.

![A list that contains several items, each representing a contact. Each item has text that states the contact's name as well as several actions including pinning the contact, sharing the contact, and deleting the contact. These actions are revealed by swiping on the item.](https://ionicframework.com/docs/img/item/actions-do.jpg)

Do

Use an [Item Sliding](https://ionicframework.com/docs/api/item-sliding) to reveal multiple actions by swiping on the Item.

![A list that contains several items, each representing a contact. Each item has text that states the contact's name as well as several actions including pinning the contact, sharing the contact, and deleting the contact. The actions are placed directly on the item. Since there are so many actions, some of the text is cut off.](https://ionicframework.com/docs/img/item/actions-do-not.jpg)

Don't

Don't put more than 2 actions within an Item.

In the example below, we are creating a list of contacts. Each item is a stubbed button intended to bring you to the full contact page for that item. There are additional actions associated with each item that users can reveal by swiping on the item.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Example</ion-title>
  </ion-toolbar>
</ion-header>
<ion-content color="light">
  <ion-list [inset]="true">
    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>Rick Astley</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>

    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>Leeroy Jenkins</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>

    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>Ionitron</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>

    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>Wall-E</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>

    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>Cortana</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>

    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>Bender</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>

    <ion-item-sliding>
      <ion-item [button]="true">
        <ion-avatar aria-hidden="true" slot="start">
          <img alt="" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <ion-label>BB-8</ion-label>
      </ion-item>
      <ion-item-options slot="end">
        <ion-item-option color="warning">
          <ion-icon slot="icon-only" name="pin"></ion-icon>
        </ion-item-option>
        <ion-item-option color="tertiary">
          <ion-icon slot="icon-only" name="share"></ion-icon>
        </ion-item-option>
        <ion-item-option color="danger" expandable="true">
          <ion-icon slot="icon-only" name="trash"></ion-icon>
        </ion-item-option>
      </ion-item-options>
    </ion-item-sliding>
  </ion-list>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import {
  IonAvatar,
  IonContent,
  IonHeader,
  IonIcon,
  IonItem,
  IonItemOption,
  IonItemOptions,
  IonItemSliding,
  IonLabel,
  IonList,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { pin, share, trash } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [\
    IonAvatar,\
    IonContent,\
    IonHeader,\
    IonIcon,\
    IonItem,\
    IonItemOption,\
    IonItemOptions,\
    IonItemSliding,\
    IonLabel,\
    IonList,\
    IonTitle,\
    IonToolbar,\
  ],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ pin, share, trash });
  }
}
```

### Controls

Controls are form components such as checkboxes, inputs, radios, and more. Each item in a list should have at most two controls due to screen space constraints.

Metadata such as helper text or character counts should not be used on form controls in list views. If such metadata is needed, the form control should be placed outside of a list. [Filled Inputs](https://ionicframework.com/docs/api/input#filled-inputs) are a great way of visually defining the input container outside of a list.

![There is an email input and a password input. Both have helper text associated with them. Since both are placed outside of a list it is clear which input each helper text is associated with.](https://ionicframework.com/docs/img/item/controls-metadata-list-do.jpg)

Do

Place inputs with metadata outside of the list.

![There is a list containing an email input and a password input. Both have helper texts associated with them. However, the divider between each item and between the helper text makes it hard to tell which input each helper text is associated with.](https://ionicframework.com/docs/img/item/controls-metadata-list-do-not.jpg)

Don't

Don't put metadata for inputs in the list.

Alternatively, the metadata can be placed in a [Note](https://ionicframework.com/docs/api/note) at the bottom of the list.

![There are two lists of inputs. The first list contains a password input. Below that list contains text that says 'Password must be at least 16 characters'. The second list contains an email input. This second list is separated so the password length requirement text is clearly associated with the password input above.](https://ionicframework.com/docs/img/item/controls-metadata-do.jpg)

Do

Place metadata for inputs at the end of a list.

![There is one list of inputs. One of the inputs is a password input with text below the input that says 'Password must be at least 16 characters'. However, this text is placed directly above another input, so it's not immediately clear which input the text is associated with.](https://ionicframework.com/docs/img/item/controls-metadata-do-not.jpg)

Don't

Don't put metadata for inputs in the list.

Items should typically have no more than two controls. If you need more controls, consider adding the additional controls in a [Modal](https://ionicframework.com/docs/api/useBaseUrl('api/modal')) that is accessible from the item.

![There is one list of inputs. One of the inputs is a password input with text below the input that says 'Password must be at least 16 characters'. However, this text is placed directly above another input, so it's not immediately clear which input the text is associated with.](https://ionicframework.com/docs/img/item/controls-count-do.jpg)

Do

Move additional controls to a submenu accessible from the item.

![There are two lists of inputs. The first list contains a password input. Below that list contains text that says 'Password must be at least 16 characters'. The second list contains an email input. This second list is separated so the password length requirement text is clearly associated with the password input above.](https://ionicframework.com/docs/img/item/controls-count-do-not.jpg)

Don't

Don't use more than two controls within an item.

In the example below, we are creating a list of to-do tasks. Each item has a checkbox and an input. The checkbox lets the user mark a task as complete, and the input lets the user change the name of the task.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Example</ion-title>
  </ion-toolbar>
</ion-header>
<ion-content color="light">
  <ion-list [inset]="true">
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Get eggs"></ion-input>
    </ion-item>
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Get milk"></ion-input>
    </ion-item>
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Take out compost"></ion-input>
    </ion-item>
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Pick up dry cleaning"></ion-input>
    </ion-item>
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Call mom"></ion-input>
    </ion-item>
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Order more dog food"></ion-input>
    </ion-item>
    <ion-item>
      <ion-checkbox slot="start" aria-label="Toggle task completion"></ion-checkbox>
      <ion-input aria-label="Task name" value="Think of new tasks for this demo"></ion-input>
    </ion-item>
  </ion-list>
</ion-content>
```

```ts
import { Component } from '@angular/core';
import {
  IonCheckbox,
  IonContent,
  IonHeader,
  IonInput,
  IonItem,
  IonList,
  IonTitle,
  IonToolbar,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox, IonContent, IonHeader, IonInput, IonItem, IonList, IonTitle, IonToolbar],
})
export class ExampleComponent {}
```

## Clickable Items

An item is considered "clickable" if it has an `href` or `button` property set. Clickable items have a few visual differences that indicate they can be interacted with. For example, a clickable item receives the ripple effect upon activation in `md` mode, has a highlight when activated in `ios` mode, and has a [detail arrow](https://ionicframework.com/docs/api/item#detail-arrows) by default in `ios` mode.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item href="#">
  <ion-label>Anchor Item</ion-label>
</ion-item>

<ion-item href="#" disabled="true">
  <ion-label>Disabled Anchor Item</ion-label>
</ion-item>

<ion-item button>
  <ion-label>Button Item</ion-label>
</ion-item>

<ion-item button disabled="true">
  <ion-label>Disabled Button Item</ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

## Detail Arrows

By default [clickable items](https://ionicframework.com/docs/api/item#clickable-items) will display a right arrow icon on `ios` mode. To hide the right arrow icon on clickable elements, set the `detail` property to `false`. To show the right arrow icon on an item that doesn't display it naturally, set the `detail` property to `true`.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item detail="true">
  <ion-label>
    <h3>Text Item</h3>
    <p>Detail set to true - detail arrow displays on both modes</p>
  </ion-label>
</ion-item>

<ion-item button>
  <ion-label>
    <h3>Button Item</h3>
    <p>Default detail - detail arrow displays on iOS only</p>
  </ion-label>
</ion-item>

<ion-item button detail="true">
  <ion-label>
    <h3>Button Item</h3>
    <p>Detail set to true - detail arrow displays on both modes</p>
  </ion-label>
</ion-item>

<ion-item button detail="false">
  <ion-label>
    <h3>Button Item</h3>
    <p>Detail set to false - detail arrow hidden on both modes</p>
  </ion-label>
</ion-item>

<ion-item button detail="true" detail-icon="caret-forward-outline">
  <ion-label>
    <h3>Button Item</h3>
    <p>Detail set to true - detail arrow displays on both modes</p>
    <p>Detail icon set to caret-forward-outline</p>
  </ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

## Item Lines

Items show an inset bottom border by default. The border has padding on the left and does not appear under any content that is slotted in the `"start"` slot. The `lines` property can be modified to `"full"` or `"none"` which will show a full width border or no border, respectively.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-label> Default Item Lines </ion-label>
</ion-item>

<ion-item lines="inset">
  <ion-label>Item Lines Inset</ion-label>
</ion-item>

<ion-item lines="full">
  <ion-label>Item Lines Full</ion-label>
</ion-item>

<ion-item lines="none">
  <ion-label>Item Lines None</ion-label>
</ion-item>

<ion-item>
  <ion-icon name="star" slot="start"></ion-icon>
  <ion-label>Default Item Lines</ion-label>
  <ion-icon name="information-circle" slot="end"></ion-icon>
</ion-item>

<ion-item lines="inset">
  <ion-icon name="star" slot="start"></ion-icon>
  <ion-label>Item Lines Inset</ion-label>
  <ion-icon name="information-circle" slot="end"></ion-icon>
</ion-item>

<ion-item lines="full">
  <ion-icon name="star" slot="start"></ion-icon>
  <ion-label>Item Lines Full</ion-label>
  <ion-icon name="information-circle" slot="end"></ion-icon>
</ion-item>

<ion-item lines="none">
  <ion-icon name="star" slot="start"></ion-icon>
  <ion-label>Item Lines None</ion-label>
  <ion-icon name="information-circle" slot="end"></ion-icon>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonIcon, IonItem, IonLabel } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { informationCircle, star } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonIcon, IonItem, IonLabel],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ informationCircle, star });
  }
}
```

## Buttons in Items

Buttons are styled smaller inside of items than when they are outside of them. To make the button size match buttons outside of an item, set the `size` attribute to `"default"`.

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-button slot="start"> Start </ion-button>
  <ion-label>Default Buttons</ion-label>
  <ion-button slot="end"> End </ion-button>
</ion-item>

<ion-item>
  <ion-button slot="start">
    Start
    <ion-icon name="home" slot="end"></ion-icon>
  </ion-button>
  <ion-label>Buttons with Icons</ion-label>
  <ion-button slot="end">
    <ion-icon name="star" slot="end"></ion-icon>
    End
  </ion-button>
</ion-item>

<ion-item>
  <ion-button slot="start">
    <ion-icon slot="icon-only" name="navigate"></ion-icon>
  </ion-button>
  <ion-label>Icon only Buttons</ion-label>
  <ion-button slot="end">
    <ion-icon slot="icon-only" name="star"></ion-icon>
  </ion-button>
</ion-item>

<ion-item>
  <ion-label>Button Sizes</ion-label>
  <ion-button slot="end" size="small"> Small </ion-button>
  <ion-button slot="end" size="default"> Default </ion-button>
  <ion-button slot="end" size="large"> Large </ion-button>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonButton, IonIcon, IonItem, IonLabel } from '@ionic/angular/standalone';

import { addIcons } from 'ionicons';
import { home, navigate, star } from 'ionicons/icons';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonButton, IonIcon, IonItem, IonLabel],
})
export class ExampleComponent {
  constructor() {
    /**
     * Any icons you want to use in your application
     * can be registered in app.component.ts and then
     * referenced by name anywhere in your application.
     */
    addIcons({ home, navigate, star });
  }
}
```

## Item Inputs

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-input label="Default Input" placeholder="Enter text"></ion-input>
</ion-item>

<ion-item>
  <ion-input label="Fixed Input" label-placement="fixed" placeholder="Enter text"></ion-input>
</ion-item>

<ion-item>
  <ion-input label="Stacked Input" label-placement="stacked" placeholder="Enter text"></ion-input>
</ion-item>

<ion-item>
  <ion-input label="Floating Input" label-placement="floating" placeholder="Enter text"></ion-input>
</ion-item>

<ion-item>
  <ion-select label="Select" placeholder="Make a Selection">
    <ion-select-option value="">No Game Console</ion-select-option>
    <ion-select-option value="nes">NES</ion-select-option>
    <ion-select-option value="n64">Nintendo64</ion-select-option>
    <ion-select-option value="ps">PlayStation</ion-select-option>
    <ion-select-option value="genesis">Sega Genesis</ion-select-option>
    <ion-select-option value="saturn">Sega Saturn</ion-select-option>
    <ion-select-option value="snes">SNES</ion-select-option>
  </ion-select>
</ion-item>

<ion-item>
  <ion-toggle> Toggle </ion-toggle>
</ion-item>

<ion-item>
  <ion-checkbox> Checkbox </ion-checkbox>
</ion-item>

<ion-item>
  <ion-range label-placement="start">
    <div slot="label">Range</div>
  </ion-range>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import {
  IonCheckbox,
  IonInput,
  IonItem,
  IonRange,
  IonSelect,
  IonSelectOption,
  IonToggle,
} from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonCheckbox, IonInput, IonItem, IonRange, IonSelect, IonSelectOption, IonToggle],
})
export class ExampleComponent {}
```

## Theming

### Colors

- src/app/example.component.html
- src/app/example.component.ts

```html
<ion-item>
  <ion-label>Default Item</ion-label>
</ion-item>
<ion-item color="primary">
  <ion-label>Primary Item</ion-label>
</ion-item>
<ion-item color="secondary">
  <ion-label>Secondary Item</ion-label>
</ion-item>
<ion-item color="tertiary">
  <ion-label>Tertiary Item</ion-label>
</ion-item>
<ion-item color="success">
  <ion-label>Success Item</ion-label>
</ion-item>
<ion-item color="warning">
  <ion-label>Warning Item</ion-label>
</ion-item>
<ion-item color="danger">
  <ion-label>Danger Item</ion-label>
</ion-item>
<ion-item color="light">
  <ion-label>Light Item</ion-label>
</ion-item>
<ion-item color="medium">
  <ion-label>Medium Item</ion-label>
</ion-item>
<ion-item color="dark">
  <ion-label>Dark Item</ion-label>
</ion-item>
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

### CSS Shadow Parts

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-item button detail lines="full">
  <ion-label>Custom Item</ion-label>
</ion-item>

<ion-item button detail lines="full">
  <ion-label>Custom Item</ion-label>
</ion-item>

<ion-item button detail lines="full">
  <ion-label>Custom Item</ion-label>
</ion-item>
```

```css
ion-item::part(native) {
  background: #19422d;
  color: #fff;

  border-color: #fff;
  border-style: dashed;
  border-width: 2px;

  border-radius: 20px;
}

ion-item::part(detail-icon) {
  color: white;
  opacity: 1;
  font-size: 20px;
}
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

### CSS Custom Properties

- src/app/example.component.html
- src/app/example.component.css
- src/app/example.component.ts

```html
<ion-item button detail lines="full">
  <ion-label>Custom Item</ion-label>
</ion-item>

<ion-item button detail lines="full">
  <ion-label>Custom Item</ion-label>
</ion-item>

<ion-item button detail lines="full">
  <ion-label>Custom Item</ion-label>
</ion-item>
```

```css
ion-item {
  --background: #19422d;
  --color: #fff;

  --border-color: #fff;
  --border-style: dashed;
  --border-width: 2px;

  --border-radius: 20px;

  --ripple-color: purple;

  --detail-icon-color: white;
  --detail-icon-opacity: 1;
  --detail-icon-font-size: 20px;
}
```

```ts
import { Component } from '@angular/core';
import { IonItem, IonLabel } from '@ionic/angular/standalone';

@Component({
  selector: 'app-example',
  templateUrl: 'example.component.html',
  styleUrls: ['example.component.css'],
  imports: [IonItem, IonLabel],
})
export class ExampleComponent {}
```

## Guidelines

The following guidelines will help ensure your list items are easy to understand and use.

1. Items should only be used inside of [Lists](https://ionicframework.com/docs/api/list).
2. Items inside of a list should be presented in a consistent format. For example, if your items present decorative icons, the icons should be positioned in the same way between items.
3. Items should never render [nested interactives](https://dequeuniversity.com/rules/axe/4.4/nested-interactive). Screen readers are unable to select the correct interactive element when nested interactives are used. For example, avoid placing a button inside of an `ion-item` that has `button="true"`.
4. Use [content types](https://ionicframework.com/docs/api/item#content-types) correctly. The Item component is designed to be a row in a [List](https://ionicframework.com/docs/api/list) and should not be used as a general purpose container.

## Accessibility

### Keyboard Interactions

An `<ion-item>` has the following keyboard interactions when any of these conditions are met:

- The `button` property is set to `"true"`, rendering a native `<button>` element.
- The `href` property is set, rendering a native `<a>` element.
- The `routerLink` property is set, rendering a native `<a>` element.

| Key | Description |
| --- | --- |
| `Tab` | Moves focus to the next focusable element. |
| `Shift` \+ `Tab` | Moves focus to the previous focusable element. |

#### Button

When an `<ion-item>` renders a native `<button>` element, the keyboard interactions follow the same pattern as the [button role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/button_role#keyboard_interactions):

| Key | Description |
| --- | --- |
| `Enter` | Activates the item, triggering its `click` event. If the item is within a form and has `type` set to `"submit"`, it submits the form. |
| `Space` | Activates the item, triggering its `click` event. Does not submit the form, even if the item `type` is `"submit"`. |

#### Anchor

When an `<ion-item>` renders a native `<a>` element, the keyboard interactions follow the same pattern as the [link role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/link_role):

| Key | Description |
| --- | --- |
| `Enter` | Activates the item, navigating to the linked page or moving focus to the in-page target. |

## Properties

### button

|     |     |
| --- | --- |
| **Description** | If `true`, a button tag will be rendered and the item will be tappable. |
| **Attribute** | `button` |
| **Type** | `boolean` |
| **Default** | `false` |

### color

|     |     |
| --- | --- |
| **Description** | The color to use from your application's color palette. Default options are: `"primary"`, `"secondary"`, `"tertiary"`, `"success"`, `"warning"`, `"danger"`, `"light"`, `"medium"`, and `"dark"`. For more information on colors, see [theming](https://ionicframework.com/docs/theming/basics). |
| **Attribute** | `color` |
| **Type** | `"danger" ｜ "dark" ｜ "light" ｜ "medium" ｜ "primary" ｜ "secondary" ｜ "success" ｜ "tertiary" ｜ "warning" ｜ string ｜ undefined` |
| **Default** | `undefined` |

### detail

|     |     |
| --- | --- |
| **Description** | If `true`, a detail arrow will appear on the item. Defaults to `false` unless the `mode` is `ios` and an `href` or `button` property is present. |
| **Attribute** | `detail` |
| **Type** | `boolean ｜ undefined` |
| **Default** | `undefined` |

### detailIcon

|     |     |
| --- | --- |
| **Description** | The icon to use when `detail` is set to `true`. |
| **Attribute** | `detail-icon` |
| **Type** | `string` |
| **Default** | `chevronForward` |

### disabled

|     |     |
| --- | --- |
| **Description** | If `true`, the user cannot interact with the item. |
| **Attribute** | `disabled` |
| **Type** | `boolean` |
| **Default** | `false` |

### download

|     |     |
| --- | --- |
| **Description** | This attribute instructs browsers to download a URL instead of navigating to it, so the user will be prompted to save it as a local file. If the attribute has a value, it is used as the pre-filled file name in the Save prompt (the user can still change the file name if they want). |
| **Attribute** | `download` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### href

|     |     |
| --- | --- |
| **Description** | Contains a URL or a URL fragment that the hyperlink points to. If this property is set, an anchor tag will be rendered. |
| **Attribute** | `href` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### lines

|     |     |
| --- | --- |
| **Description** | How the bottom border should be displayed on the item. |
| **Attribute** | `lines` |
| **Type** | `"full" ｜ "inset" ｜ "none" ｜ undefined` |
| **Default** | `undefined` |

### mode

|     |     |
| --- | --- |
| **Description** | The mode determines which platform styles to use.<br>This is a [virtual property](https://ionicframework.com/docs/core-concepts/fundamentals#virtual-properties) that is set once during initialization and will not update if you change its value after the initial render. |
| **Attribute** | `mode` |
| **Type** | `"ios" ｜ "md"` |
| **Default** | `undefined` |

### rel

|     |     |
| --- | --- |
| **Description** | Specifies the relationship of the target object to the link object. The value is a space-separated list of [link types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types). |
| **Attribute** | `rel` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### routerAnimation

|     |     |
| --- | --- |
| **Description** | When using a router, it specifies the transition animation when navigating to another page using `href`. |
| **Attribute** | `undefined` |
| **Type** | `((baseEl: any, opts?: any) => Animation) ｜ undefined` |
| **Default** | `undefined` |

### routerDirection

|     |     |
| --- | --- |
| **Description** | When using a router, it specifies the transition direction when navigating to another page using `href`. |
| **Attribute** | `router-direction` |
| **Type** | `"back" ｜ "forward" ｜ "root"` |
| **Default** | `'forward'` |

### target

|     |     |
| --- | --- |
| **Description** | Specifies where to display the linked URL. Only applies when an `href` is provided. Special keywords: `"_blank"`, `"_self"`, `"_parent"`, `"_top"`. |
| **Attribute** | `target` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### type

|     |     |
| --- | --- |
| **Description** | The type of the button. Only used when an `onclick` or `button` property is present. |
| **Attribute** | `type` |
| **Type** | `"button" ｜ "reset" ｜ "submit"` |
| **Default** | `'button'` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

| Name | Description |
| --- | --- |
| `container` | The wrapper element that contains the default slot. |
| `detail-icon` | The chevron icon for the item. Only applies when `detail="true"`. |
| `inner` | The inner wrapper element that arranges the item content. |
| `native` | The native HTML button, anchor or div element that wraps all child elements. |

## CSS Custom Properties

- iOS
- MD

| Name | Description |
| --- | --- |
| `--background` | Background of the item |
| `--background-activated` | Background of the item when pressed. Note: setting this will interfere with the Material Design ripple. |
| `--background-activated-opacity` | Opacity of the item background when pressed |
| `--background-focused` | Background of the item when focused with the tab key |
| `--background-focused-opacity` | Opacity of the item background when focused with the tab key |
| `--background-hover` | Background of the item on hover |
| `--background-hover-opacity` | Opacity of the background of the item on hover |
| `--border-color` | Color of the item border |
| `--border-radius` | Radius of the item border |
| `--border-style` | Style of the item border |
| `--border-width` | Width of the item border |
| `--color` | Color of the item |
| `--color-activated` | Color of the item when pressed |
| `--color-focused` | Color of the item when focused with the tab key |
| `--color-hover` | Color of the item on hover |
| `--detail-icon-color` | Color of the item detail icon |
| `--detail-icon-font-size` | Font size of the item detail icon |
| `--detail-icon-opacity` | Opacity of the item detail icon |
| `--inner-border-width` | Width of the item inner border |
| `--inner-box-shadow` | Box shadow of the item inner |
| `--inner-padding-bottom` | Bottom padding of the item inner |
| `--inner-padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the item inner |
| `--inner-padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the item inner |
| `--inner-padding-top` | Top padding of the item inner |
| `--min-height` | Minimum height of the item |
| `--padding-bottom` | Bottom padding of the item |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the item |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the item |
| `--padding-top` | Top padding of the item |
| `--ripple-color` | Color of the item ripple effect |
| `--transition` | Transition of the item |

| Name | Description |
| --- | --- |
| `--background` | Background of the item |
| `--background-activated` | Background of the item when pressed. Note: setting this will interfere with the Material Design ripple. |
| `--background-activated-opacity` | Opacity of the item background when pressed |
| `--background-focused` | Background of the item when focused with the tab key |
| `--background-focused-opacity` | Opacity of the item background when focused with the tab key |
| `--background-hover` | Background of the item on hover |
| `--background-hover-opacity` | Opacity of the background of the item on hover |
| `--border-color` | Color of the item border |
| `--border-radius` | Radius of the item border |
| `--border-style` | Style of the item border |
| `--border-width` | Width of the item border |
| `--color` | Color of the item |
| `--color-activated` | Color of the item when pressed |
| `--color-focused` | Color of the item when focused with the tab key |
| `--color-hover` | Color of the item on hover |
| `--detail-icon-color` | Color of the item detail icon |
| `--detail-icon-font-size` | Font size of the item detail icon |
| `--detail-icon-opacity` | Opacity of the item detail icon |
| `--inner-border-width` | Width of the item inner border |
| `--inner-box-shadow` | Box shadow of the item inner |
| `--inner-padding-bottom` | Bottom padding of the item inner |
| `--inner-padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the item inner |
| `--inner-padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the item inner |
| `--inner-padding-top` | Top padding of the item inner |
| `--min-height` | Minimum height of the item |
| `--padding-bottom` | Bottom padding of the item |
| `--padding-end` | Right padding if direction is left-to-right, and left padding if direction is right-to-left of the item |
| `--padding-start` | Left padding if direction is left-to-right, and right padding if direction is right-to-left of the item |
| `--padding-top` | Top padding of the item |
| `--ripple-color` | Color of the item ripple effect |
| `--transition` | Transition of the item |

## Slots

| Name | Description |
| --- | --- |
| \`\` | Content is placed between the named slots if provided without a slot. |
| `end` | Content is placed to the right of the item text in LTR, and to the left in RTL. |
| `start` | Content is placed to the left of the item text in LTR, and to the right in RTL. |
