---
name: ionic-docs
description: Offline copy of the official Ionic Framework v8 documentation (component API reference for ion-* components, Ionic Angular guides, the Angular "first app" tutorial, the Ionic 7 migration guide). Use this whenever the task touches Ionic - writing, reviewing, fixing or explaining code that uses ion-* components (ion-modal, ion-item, ion-datetime, ion-input, ion-grid, ion-menu, ion-popover, ...), @ionic/angular, IonicModule or standalone imports, Ionic navigation/routing, page lifecycle hooks (ionViewWillEnter etc.), the Platform service, Ionic CSS custom properties and shadow parts, or Capacitor-based Ionic apps - even if the user never says "docs". Look the component up here before answering from memory, because property names, events, slots and defaults are easy to get subtly wrong.
---

# Ionic Framework docs (v8)

This skill bundles the official Ionic documentation, split into one markdown file per docs page under `references/`. Treat it as the source of truth for Ionic APIs: memory of Ionic is often a blend of several major versions (v4-v8 changed a lot - form control syntax, overlays, standalone components, `ion-slides` and `ion-virtual-scroll` removal), so checking the actual page is cheap insurance against writing code for the wrong version.

## How to look things up

1. **Know the component or topic?** Go straight to the file. Paths mirror the docs URLs:
   - `references/api/<component>.md` - one per component, name without the `ion-` prefix (`ion-item-sliding` -> `references/api/item-sliding.md`)
   - `references/angular/<topic>.md` - Ionic Angular guides
   - `references/angular/your-first-app/*.md` - the photo gallery tutorial (Capacitor Camera, Filesystem, Preferences, live reload, deploying)
2. **Not sure where it lives?** Read `references/INDEX.md` - a table of every page with a one-line summary and line count.
3. **Looking for a specific property, event, CSS variable or phrase?** Grep across `references/` instead of reading whole files, e.g. `grep -rn "canDismiss" references/` or `grep -rln "\-\-border-radius" references/api/`.

Read only what the task needs. Several pages are long (`modal` ~2500 lines, `datetime` ~1800, `item` ~1600, `input` ~1100). Each file starts with a `Sections:` line listing its headings; grep for the heading (`grep -n "^## \|^### " references/api/modal.md`) and read that range rather than the full file.

## How component pages are laid out

Every `references/api/*.md` page follows the same shape, which makes targeted reading easy:

- Intro and usage sections with code examples (e.g. "Basic Usage", "Sheet Modal", "Theming")
- `## Interfaces` - TypeScript types for options and event details, when the component has them
- `## Accessibility` - keyboard interactions, ARIA guidance
- `## Properties` - one `###` per property with Description / Attribute / Type / Default
- `## Events`, `## Methods`, `## CSS Shadow Parts`, `## CSS Custom Properties`, `## Slots`

So "what events does ion-range emit?" is answered by the `## Events` section of `references/api/range.md`, and "how do I restyle the modal handle?" by `## CSS Shadow Parts` and `## CSS Custom Properties` in `references/api/modal.md`.

## Things to keep in mind

- **Examples are Angular.** The docs site has Angular / JavaScript / React / Vue tabs, but this copy captured only the Angular tab (standalone components, imports from `@ionic/angular/standalone`). The Properties, Events, Methods, CSS and Slots tables are framework-agnostic. When the user works in React or Vue, use the tables as-is and translate the example: `IonModal` etc. from `@ionic/react` / `@ionic/vue`, camelCase props, `onIonChange`-style event handlers in React and `@ionChange` / `@ion-change` in Vue.
- **Match the project's setup.** In Angular projects check whether the app uses standalone components or `IonicModule` before writing imports; `references/angular/build-options.md` explains both and how to migrate.
- **Coverage is partial.** The source dump ended partway through the alphabet, so some pages are missing. Covered: components from `accordion` through `searchbar`, the Angular guides, Web View concepts, and the v7 upgrade guide. Not covered: components after `searchbar` (segment, select, skeleton-text, spinner, split-pane, tab-bar, tabs, text, textarea, thumbnail, title, toast, toggle, toolbar, ...), React and Vue guides, theming, utilities (animations, gestures), CLI, layout and the v8 upgrade guide. For those, say that the local copy does not include the page and fetch `https://ionicframework.com/docs/api/<component>` (or the matching docs URL) if web access is available; otherwise answer from memory and flag that it is unverified.
- **Cite the source.** Each file has a `Source:` URL on its third line. Mention it when the answer leans on a specific page so the user can open the live docs.
