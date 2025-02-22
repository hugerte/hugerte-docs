# HugeRTE Angular integration
This file provides documentation for the [HugeRTE Angular integration package](https://github.com/hugerte/hugerte-angular).

## Quick start
Add the HugeRTE Angular integration to your project using npm (or an npm-based package manager like yarn or pnpm):

```bash
npm install @hugerte/hugerte-angular
```

or:

```bash
yarn add @hugerte/hugerte-angular
```

or:

```bash
pnpm add @hugerte/hugerte-angular
```

The HugeRTE Angular integration package exports an `EditorModule` and an `EditorComponent`. Use the module in your module or the component in your component, whether approach better fits your needs. Add the one you decided to use to the `imports` array of your module or component, respectively.

Then, you can use `<editor></editor>` iin your template. The following options are available:

- `cdnVersion`: A string representing the version of HugeRTE to be loaded from the jsDelivr CDN. This is only applied if the `hugerte` global variable isn't already defined and the `HUGERTE_SCRIPT_SRC` injection token (see below for more info about it) isn't provided. By default, version 1 (that is, the latest minor and patch release of the major version 1) will be used. For more info about the possible version formats, see the [jsDelivr documentation](https://www.jsdelivr.com/documentation#id-npm). Note that loading by tag or `latest` will currently throw a type error.
- `disabled`: A boolean indicating whether the editor should be disabled. Default is `false`.
- `id`: A unique string identifier for the editor instance. If not provided, a unique id will be generated.
- `init`: An object of options to be passed to the `hugerte.init()` method.
- `initialValue`: A string representing the initial content to be loaded into the editor. If not provided, the editor will be empty.
- `outputFormat`: Specifies the format of the editor's output when using forms or plain data bindings. Can be either html or text. Default is html.
- `inline`: A boolean indicating if the editor should be rendered inline. Default is `false`.
- `tagName`: The HTML tag name to be used for the editor element if rendered in inline mode. Default is `div`. This has no effect when not rendering the editor in inline mode.
- `plugins`: An array or a string listing the plugins to be used by the editor. This will be added as the `plugins` option of object passed to the `hugerte.init()` method.
- `toolbar`: An array or a string defining the items to be included in the editor's toolbar. This will be added as the `toolbar` option of object passed to the `hugerte.init()` method.
- `modelEvents`: An array or a *space*-separated string specifying the events that should trigger an emit of the `NgModelChange`. Default is `change input undo redo`.
- `allowedEvents`: An array or a *comma*-separated string specifying the events that should be allowed to trigger from the editor to the `hugerte-angular` component. By default, all events [defined in this array](https://github.com/hugerte/framework-integration-shared/blob/265d022c7e35159aed84239a8353ac92ada50aa7/src/Utils.ts#L12), mapped to be `on`-prefixed, plus `onInitNgModel` and `onPreInit` will be allowed to trigger.
- `ignoreEvents`: An array or a *comma*-separated string specifying the events that should not be allowed to trigger from the editor to the `hugerte-angular` component, no matter if `allowedEvents` is set or not.

## Self-hosting HugeRTE
By default, if no `hugerte` global variable is already present on `globalThis` (`window`), the editor will be loaded from the jsDelivr CDN. However, you can also self-host the editor. You can either bundle the HugeRTE scripts or let Angular copy the `node_modules/hugerte` folder to an output `hugerte` folder. We recommend the first approach.

### Bundling HugeRTE
Please follow [the bundling guide](../README.md#bundling). Make sure to include the `hugerte` imports *before* the `@hugerte/hugerte-angular` import.

### Copying the HugeRTE folder

When using the `hugerte` npm package, add this to your `angular.json` file:

```json
"assets": [
  { "glob": "**/*", "input": "node_modules/hugerte", "output": "/hugerte/" }
]
```

This is not required when manually downloading HugeRTE distribution files from https://github.com/hugerte/hugerte-dist. (But we recommend using npm instead.)

### Lazy-loading HugeRTE on editor initialization

Import both the `EditorModule` or `EditorComponent` and the `HUGERTE_SCRIPT_SRC` injection token from `@hugerte/hugerte-angular`.

```ts
import { EditorModule, HUGERTE_SCRIPT_SRC } from '@hugerte/hugerte-angular';
// or:
import { EditorComponent, HUGERTE_SCRIPT_SRC } from '@hugerte/hugerte-angular';
```

Then, add this object as an item to your `providers` array in your module/component:

```ts
{ provide: HUGERTE_SCRIPT_SRC, useValue: 'hugerte/hugerte.min.js' }
```

### Loading HugeRTE on page/application load

Add this to your global scripts in your `angular.json` file:

```json
"scripts": [
  "node_modules/tinymce/tinymce.min.js"
]
```

Then in the `init` option passed to the editor component, add the `base_url` and `suffix` options:

```html
<editor [init]="{base_url: '/hugerte', suffix: '.min'}"></editor>
```

## Using the editor in a form

Use the `ngModel` directive:

```html
<editor [(ngModel)]="yourDataModel"></editor>
```

Consult the [Angular documentation on NgModel in forms](https://angular.io/api/forms/NgModel) for more information.

## Using the editor in reactive forms

Include the `<editor>` within a form group, then use the `formControlName` directive:

```html
<editor [formControlName]="schema.key"></editor>
```

Consult the [Angular documentation on reactive forms](https://angular.io/guide/reactive-forms) for more information.

## Event binding

You can bind to any event in [the events list](https://github.com/hugerte/framework-integration-shared/blob/265d022c7e35159aed84239a8353ac92ada50aa7/src/Utils.ts#L12) (except those you exclude by the `ignoreEvents` option and/or don't set in the `allowedEvents` option, if you include it), but **you'll have to prefix each one with `on`**. Plus, the `onInitNgModel` and `onPreInit` events, which aren't included in the list linked above, are also supported.

```html
<editor (onSelectionChange)="handleEvent($event)"></editor>
```

The $event variable will have the `event` (HugeRTE event object) and `editor` properties.

## Migrating from the TinyMCE Angular component
1. Replace `tinymce` by `hugerte` (`@tinymce/tinymce-angular` to `@hugerte/hugerte-angular`).
2. Review the [changelog](https://github.com/hugerte/hugerte-angular/blob/main/CHANGELOG.md).

## Storybook
The [hugerte/hugerte-angular](https://github.com/hugerte/hugerte-angular) repo comes with a storybook showing examples of integrating HugeRTE with Angular. To run the storybook, follow the following steps:
1. Clone the repo:
   ```bash
   git clone https://github.com/hugerte/hugerte-angular
   ```
2. Install dependencies:
   ```bash
   yarn
   ```
3. Run the storybook:
   ```bash
   yarn storybook
   ```

## Support

This component requires Angular 17+.

## Issues

Have you found an issue with hugerte-angular or do you have a feature request? Open up an [issue](https://github.com/hugerte/hugerte-angular/issues) and let us know or submit a pull request by [forking this repo](https://github.com/hugerte/hugerte-angular/fork), making the appropiate changes,then going to the pull request tab in your fork and creating one. *Note: for issues concerning HugeRTE itself please visit the [HugeRTE repository](https://github.com/hugerte/hugerte).*
