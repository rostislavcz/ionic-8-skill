# Ionic Router Overview

Source: https://ionicframework.com/docs/api/router

Sections: Basic Usage · Interfaces · Usage · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

The router is a component for handling routing inside vanilla and Stencil JavaScript projects.

note

Note: This component should only be used with vanilla and Stencil JavaScript projects. See the routing guides for [Angular](https://ionicframework.com/docs/angular/navigation), [React](https://ionicframework.com/docs/react/navigation), and [Vue](https://ionicframework.com/docs/vue/navigation) for framework-specific routing solutions.

Apps should have a single `ion-router` component in the codebase.
This component controls all interactions with the browser history and it aggregates updates through an event system.

`ion-router` is just a URL coordinator for the navigation outlets of ionic: `ion-nav`, `ion-tabs`, and `ion-router-outlet`.

That means the `ion-router` never touches the DOM, it does NOT show the components or emit any kind of lifecycle events, it just tells `ion-nav`, `ion-tabs`, and `ion-router-outlet` what and when to "show" based on the browser's URL.

In order to configure this relationship between components (to load/select) and URLs, `ion-router` uses a declarative syntax using JSX/HTML to define a tree of routes.

## Basic Usage

Angular

JavaScript

React

Vue

```html
<ion-router>
  <ion-route url="/" component="page-one"></ion-route>
  <ion-route url="/page-two" component="page-two"></ion-route>
</ion-router>

<ion-router-outlet></ion-router-outlet>

<script>
  class PageOne extends HTMLElement {
    connectedCallback() {
      this.innerHTML = `
    <ion-header>
      <ion-toolbar>
        <ion-title>Page One</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      This is the content for page 1.
      <ion-router-link href="#/page-two">
        <ion-button>Go to Page 2</ion-button>
      </ion-router-link>
    </ion-content>`;
    }
  }

  class PageTwo extends HTMLElement {
    connectedCallback() {
      this.innerHTML = `
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button default-href="/"></ion-back-button>
        </ion-buttons>
        <ion-title>Page Two</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      This is the content for page 2.
    </ion-content>`;
    }
  }

  customElements.define('page-one', PageOne);
  customElements.define('page-two', PageTwo);
</script>
```

## Interfaces

### RouterEventDetail

```typescript
interface RouterEventDetail {
  from: string | null;
  redirectedFrom: string | null;
  to: string;
}
```

### RouterCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface RouterCustomEvent extends CustomEvent {
  detail: RouterEventDetail;
  target: HTMLIonRouterElement;
}
```

## Usage

```html
<ion-router>
  <ion-route component="page-tabs">
    <ion-route url="/schedule" component="tab-schedule">
      <ion-route component="page-schedule"></ion-route>
      <ion-route url="/session/:sessionId" component="page-session"></ion-route>
    </ion-route>

    <ion-route url="/speakers" component="tab-speaker">
      <ion-route component="page-speaker-list"></ion-route>
      <ion-route url="/session/:sessionId" component="page-session"></ion-route>
      <ion-route url="/:speakerId" component="page-speaker-detail"></ion-route>
    </ion-route>

    <ion-route url="/map" component="page-map"></ion-route>
    <ion-route url="/about" component="page-about"></ion-route>
  </ion-route>

  <ion-route url="/tutorial" component="page-tutorial"></ion-route>
  <ion-route url="/login" component="page-login"></ion-route>
  <ion-route url="/account" component="page-account"></ion-route>
  <ion-route url="/signup" component="page-signup"></ion-route>
  <ion-route url="/support" component="page-support"></ion-route>
</ion-router>
```

## Properties

### root

|     |     |
| --- | --- |
| **Description** | The root path to use when matching URLs. By default, this is set to "/", but you can specify an alternate prefix for all URL paths. |
| **Attribute** | `root` |
| **Type** | `string` |
| **Default** | `'/'` |

### useHash

|     |     |
| --- | --- |
| **Description** | The router can work in two "modes": - With hash: `/index.html#/path/to/page` \- Without hash: `/path/to/page`<br>Using one or another might depend in the requirements of your app and/or where it's deployed.<br>Usually "hash-less" navigation works better for SEO and it's more user friendly too, but it might requires additional server-side configuration in order to properly work.<br>On the other side hash-navigation is much easier to deploy, it even works over the file protocol.<br>By default, this property is `true`, change to `false` to allow hash-less URLs. |
| **Attribute** | `use-hash` |
| **Type** | `boolean` |
| **Default** | `true` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionRouteDidChange` | Emitted when the route had changed | `true` |
| `ionRouteWillChange` | Event emitted when the route is about to change | `true` |

## Methods

### back

|     |     |
| --- | --- |
| **Description** | Go back to previous page in the window.history. |
| **Signature** | `back() => Promise<void>` |

### push

|     |     |
| --- | --- |
| **Description** | Navigate to the specified path. |
| **Signature** | `push(path: string, direction?: RouterDirection, animation?: AnimationBuilder) => Promise<boolean>` |
| **Parameters** | **path**: The path to navigate to.<br>**direction**: The direction of the animation. Defaults to `"forward"`.<br>**animation**: A custom animation to use for the transition. |

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
