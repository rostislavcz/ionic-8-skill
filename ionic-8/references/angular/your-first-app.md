# Ionic Photo Gallery App

Source: https://ionicframework.com/docs/angular/your-first-app

Sections: What We'll Build · Download Required Tools · Install Ionic Tooling · Create an App · Run the App · Photo Gallery

The great thing about Ionic is that with one codebase, you can build for any platform using just HTML, CSS, and JavaScript. Follow along as we learn the fundamentals of Ionic app development by creating a realistic app step by step.

Here’s the finished app running on all 3 platforms:

Your First Ionic App: Building a Photo Gallery - YouTube

Tap to unmute

[Your First Ionic App: Building a Photo Gallery](https://www.youtube.com/watch?v=0ASQ13Y1Rk4) [Ionic](https://www.youtube.com/channel/UChYheBnVeCfhCmqZfCUdJQw)

![thumbnail-image](https://yt3.ggpht.com/YL6IJgSyoxsgitiEyN1erhREvIMuvqA-BRlcn2BMD7v1vG2RV7trCUF0wHkcnrQOIiYj3i1KHA=s68-c-k-c0x00ffffff-no-rj)

Ionic39.5K subscribers

[Watch on](https://www.youtube.com/watch?v=0ASQ13Y1Rk4)

note

Looking for the previous version of this guide that covered Ionic 4 and Cordova? [See here.](https://ionicframework.com/docs/developer-resources/guides/first-app-v4/intro)

## What We'll Build

We'll create a Photo Gallery app that offers the ability to take photos with your device's camera, display them in a grid, and store them permanently on the device.

Highlights include:

- One Angular-based codebase that runs on the web, iOS, and Android using Ionic Framework [UI components](https://ionicframework.com/docs/components).
- Deployed as a native iOS and Android mobile app using [Capacitor](https://capacitorjs.com/), Ionic's official native app runtime.
- Photo Gallery functionality powered by the Capacitor [Camera](https://ionicframework.com/docs/native/camera), [Filesystem](https://ionicframework.com/docs/native/filesystem), and [Preferences](https://ionicframework.com/docs/native/preferences) APIs.

Find the [complete app code](https://github.com/ionic-team/tutorial-photo-gallery-angular) referenced in this guide on GitHub.

## Download Required Tools

Download and install these right away to ensure an optimal Ionic development experience:

- **Node.js** for interacting with the Ionic ecosystem. [Download the LTS version here](https://nodejs.org/en/).
- **A code editor** for... writing code! We are fans of [Visual Studio Code](https://code.visualstudio.com/).
- **Command-line interface/terminal (CLI)**:
  - **Windows** users: for the best Ionic experience, we recommend the built-in command line (cmd) or the Powershell CLI, running in Administrator mode.
  - **Mac/Linux** users: virtually any terminal will work.

## Install Ionic Tooling

Run the following in the command line terminal to install the Ionic CLI (`ionic`), `native-run`, used to run native binaries on devices and simulators/emulators, and `cordova-res`, used to generate native app icons and splash screens:

note

To open a terminal in Visual Studio Code, go to Terminal -> New Terminal.

```shell
npm install -g @ionic/cli native-run cordova-res
```

note

The `-g` option means _install globally_. When packages are installed globally, `EACCES` permission errors can occur.

Consider setting up npm to operate globally without elevated permissions. See [Resolving Permission Errors](https://ionicframework.com/docs/developing/tips#resolving-permission-errors) for more information.

## Create an App

Next, create an Ionic Angular app that uses the "Tabs" starter template and adds Capacitor for native functionality:

```shell
ionic start photo-gallery tabs --type=angular
```

note

When prompted to choose between `NgModules` and `Standalone`, opt for `NgModules` as this tutorial follows the `NgModules` approach.

This starter project comes complete with three pre-built pages and best practices for Ionic development. With common building blocks already in place, we can add more features easily!

Next, change into the app folder:

```shell
cd photo-gallery
```

Next we'll need to install the necessary Capacitor plugins to make the app's native functionality work:

```shell
npm install @capacitor/camera @capacitor/preferences @capacitor/filesystem
```

### PWA Elements

Some Capacitor plugins, including the [Camera API](https://ionicframework.com/docs/native/camera), provide the web-based functionality and UI via the Ionic [PWA Elements library](https://github.com/ionic-team/pwa-elements).

It's a separate dependency, so install it next:

```shell
npm install @ionic/pwa-elements
```

Next, import `@ionic/pwa-elements` by editing `src/main.ts`.

```ts
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';
// CHANGE: Add the following import
import { defineCustomElements } from '@ionic/pwa-elements/loader';

// CHANGE: Call the element loader before the `bootstrapModule` call
defineCustomElements(window);

platformBrowserDynamic()
  .bootstrapModule(AppModule)
  .catch((err) => console.log(err));
```

That’s it! Now for the fun part - let’s see the app in action.

## Run the App

Run this command next:

```shell
ionic serve
```

And voilà! Your Ionic app is now running in a web browser. Most of your app can be built and tested right in the browser, greatly increasing development and testing speed.

## Photo Gallery

There are three tabs. Click on the "Tab2" tab. It’s a blank canvas, aka the perfect spot to transform into a Photo Gallery. The Ionic CLI features Live Reload, so when you make changes and save them, the app is updated immediately!

![Animated GIF showing the live reload feature in an Ionic app, with changes in code immediately updating the app in a web browser.](https://ionicframework.com/docs/assets/images/email-photogallery-dfb7fe448bcb1bdcd748ee18ed759e8b.gif)

Open `/src/app/tab2/tab2.page.html`. We see:

```html
<ion-header [translucent]="true">
  <ion-toolbar>
    <ion-title> Tab 2 </ion-title>
  </ion-toolbar>
</ion-header>

<ion-content [fullscreen]="true">
  <ion-header collapse="condense">
    <ion-toolbar>
      <ion-title size="large">Tab 2</ion-title>
    </ion-toolbar>
  </ion-header>

  <app-explore-container name="Tab 2 page"></app-explore-container>
</ion-content>
```

`ion-header` represents the top navigation and toolbar, with "Tab 2" as the title (there are two of them due to iOS [Collapsible Large Title](https://ionicframework.com/docs/api/title#collapsible-large-titles) support). Rename both `ion-title` elements to:

```html
<ion-header [translucent]="true">
  <ion-toolbar>
    <!-- CHANGE: Update title -->
    <ion-title> Photo Gallery </ion-title>
  </ion-toolbar>
</ion-header>

<ion-content [fullscreen]="true">
  <ion-header collapse="condense">
    <ion-toolbar>
      <!-- CHANGE: Update title -->
      <ion-title size="large">Photo Gallery</ion-title>
    </ion-toolbar>
  </ion-header>

  <app-explore-container name="Tab 2 page"></app-explore-container>
</ion-content>
```

We put the visual aspects of our app into `<ion-content>`. In this case, it’s where we’ll add a button that opens the device’s camera as well as displays the image captured by the camera. Start by adding a [floating action button](https://ionicframework.com/docs/api/fab) (FAB) to the bottom of the page and set the camera image as the icon.

```html
<ion-header [translucent]="true">
  <ion-toolbar>
    <ion-title>Photo Gallery</ion-title>
  </ion-toolbar>
</ion-header>

<ion-content>
  <ion-header collapse="condense">
    <ion-toolbar>
      <ion-title size="large">Photo Gallery</ion-title>
    </ion-toolbar>
  </ion-header>

  <!-- CHANGE: Add the floating action button -->
  <ion-fab vertical="bottom" horizontal="center" slot="fixed">
    <ion-fab-button>
      <ion-icon name="camera"></ion-icon>
    </ion-fab-button>
  </ion-fab>

  <!-- CHANGE: Remove or comment out `app-explore-container` -->
  <!-- <app-explore-container name="Tab 2 page"></app-explore-container> -->
</ion-content>
```

Next, open `src/app/tabs/tabs.page.html`. Change the label to "Photos" and the `ellipse` icon to `images` for the middle tab button.

```html
<ion-tabs>
  <ion-tab-bar slot="bottom">
    <ion-tab-button tab="tab1" href="/tabs/tab1">
      <ion-icon aria-hidden="true" name="triangle"></ion-icon>
      <ion-label>Tab 1</ion-label>
    </ion-tab-button>

    <ion-tab-button tab="tab2" href="/tabs/tab2">
      <!-- CHANGE: Update icon -->
      <ion-icon aria-hidden="true" name="images"></ion-icon>
      <!-- CHANGE: Update label -->
      <ion-label>Photos</ion-label>
    </ion-tab-button>

    <ion-tab-button tab="tab3" href="/tabs/tab3">
      <ion-icon aria-hidden="true" name="square"></ion-icon>
      <ion-label>Tab 3</ion-label>
    </ion-tab-button>
  </ion-tab-bar>
</ion-tabs>
```

That’s just the start of all the cool things we can do with Ionic. Up next, implement camera taking functionality on the web, then build it for iOS and Android.
