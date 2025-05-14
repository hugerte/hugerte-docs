# HugeRTE Vue integration
This file provides documentation for the [HugeRTE Vue integration package](https://github.com/hugerte/hugerte-vue).

## Demos
The repo linked above comes with various demos to show various ways of integrating HugeRTE with Vue. To run the demos, follow the following steps:
1. Clone the repo:
   ```bash
   git clone https://github.com/hugerte/hugerte-vue
   ```
2. Install dependencies:
   ```bash
   yarn
   ```
3. Run the demos:
   ```bash
   yarn demo
   ```

## Quick start
Add the HugeRTE Vue component to your project using npm (or an npm-based package manager like yarn):

```bash
npm install @hugerte/hugerte-vue
```

or:

```bash
yarn add @hugerte/hugerte-vue
```

Then, copy the demo that is appropriate for you from the repo linked above. **Replace `import Editor from "/@/main/ts/index"` by `import Editor from '@hugerte/hugerte-vue'`.** If your code will contain non-trivial portions of demo code, add the text of the [LICENSE.txt](LICENSE.txt) file as a comment to your code or on some „Acknowledgements“ page to ensure legal compliance.

## Migrating from the TinyMCE Vue component
1. Replace `tinymce` by `hugerte` (`@tinymce/tinymce-vue` to `@hugerte/hugerte-vue`).
2. Review the changes in the [changelog](https://github.com/hugerte/hugerte-vue/blob/main/CHANGELOG.md).

## Storybook
The repo also comes with a storybook. The storybook does not contain as many demos as the demos above, but it does show the basic abilities to use HugeRTE in an iframe, in inline mode, with synchronization between the editor and a textarea containing its HTML content output, and in disabled mode.

## Reference on the supported options on the HugeRTE Vue component
- `cdn-version`: A string representing the version of HugeRTE to be loaded from the jsDelivr CDN. This is only applied if the `hugerteScriptSrc` prop is not set. By default, version 1 (that is, the latest minor and patch release of the major version 1) will be used. For more info about the possible version formats, see the [jsDelivr documentation](https://www.jsdelivr.com/documentation#id-npm).
- `id`: A unique string identifier for the editor instance. If not provided, a unique id will be generated.
- `init`: An object of options to be passed to the `hugerte.init()` method.
- `initial-value`: A string representing the initial content to be loaded into the editor. If not provided, the editor will be empty.
- `output-format`: Specifies the format of the editor's output. Can be either `html` or `text`. Default is `html`.
- `inline`: A boolean indicating if the editor should be rendered inline. Default is `false`.
- `model-events`: An array or a string specifying the events that should trigger updates to the editor's `v-model`. Default is `change keyup undo redo`.
- `plugins`: An array or a string listing the plugins to be used by the editor. This will be added as the `plugins` option of object passed to the `hugerte.init()` method.
- `tag-name`: A string specifying the HTML tag to be used for the editor element if rendered in inline mode. Default is `div`. This is only used if `inline` is set to `true`.
- `toolbar`: An array or a string defining the items to be included in the editor's toolbar. This will be added as the `toolbar` option of object passed to the `hugerte.init()` method.
- `disabled`: A boolean indicating whether the editor is disabled. Default is `false`.
- `hugerte-script-src`: A string URL that specifies the source of the HugeRTE script to be loaded. If this is not specified, the script will be loaded from the jsDelivr CDN.

## Support

The HugeRTE Vue component version 1.x only supports Vue 3. The HugeRTE Vue component version 2.x supports both Vue 3 and Vue 2, but if you'd like to use this library in a Vue 2 project, add `/vue2` to the package name when importing: `import Editor from '@hugerte/hugerte-vue/vue2'`.
The HugeRTE Vue component version 1.x is not supported anymore. Please upgrade to 2.x. If you use the wrapper normally and with a bundler, there should be no breaking change for you, but please review the [changelog](https://github.com/hugerte/hugerte-vue/blob/main/CHANGELOG.md) as there is a possibility of breaking changes if you have been doing certain things.

## Issues

Have you found an issue with `hugerte-vue` or do you have a feature request? Open up an [issue](https://github.com/hugerte/hugerte-vue/issues) and let us know or submit a [pull request](https://github.com/hugerte/hugerte-vue/pulls). *Note: for issues related to HugeRTE itself please visit the [HugeRTE repository](https://github.com/hugerte/hugerte).*
