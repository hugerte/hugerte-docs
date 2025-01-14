# HugeRTE docs

This repo contains documentation for the [HugeRTE](https://github.com/hugerte/hugerte) editor.

## Get started with HugeRTE

The simplest way to get started with HugeRTE is using a CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/hugerte@1/hugerte.min.js">
```

Or install it manually via `npm` or `yarn`:

```bash
npm i hugerte
```

or:

```bash
yarn add hugerte
```

You can also install it via composer:

```bash
composer require hugerte/hugerte
```

If you don't use an npm- or packagist-based package manager, you can also get the latest release as zip on the [hugerte-dist GitHub tags page](https://github.com/hugerte/hugerte-dist/tags).

In this repo, we want to provide docs for HugeRTE that are freely usable. The text of this docs is licensed under the MIT license, but code snippets are licensed under the BSD Zero Clause license so you can quickly copy them into your project without worrying about attribution.
These docs are stil in an Alpha stage. You'll mostly have to check the [TinyMCE 6 docs](https://tiny.cloud/docs/tinymce/6). We want to write the docs in our own words instead of forking the TinyMCE docs because the latter are licensed under a [CC BY-NC-SA license](https://github.com/tinymce/tinymce-docs/blob/main/LICENSE.txt) which we don't want to use. See [this informative line](https://github.com/hugerte/hugerte-website/blob/1eccf2841473af46b3aa995dfcea11925c272620/index.php#L25) also.
When referring to the TinyMCE docs, make sure to replace all occurrences of `tinymce` by `hugerte` in your code.

[See this guide also](https://www.tiny.cloud/docs/tinymce/6/npm-projects/), but replace `tinymce@^6` by `hugerte@^1` (and of course, all occurrences of `tinymce` by `hugerte`).

Important links:
- https://www.tiny.cloud/docs/tinymce/6/basic-setup/
- https://www.tiny.cloud/docs/tinymce/6/use-tinymce-classic/
- https://www.tiny.cloud/docs/tinymce/6/use-tinymce-inline/
- https://www.tiny.cloud/docs/tinymce/6/use-tinymce-distraction-free/

## Migrate from TinyMCE

If you have been using TinyMCE before, you have to brute-force replace `tinymce` by `hugerte` in your code. In your package.json, make sure you use `1.0.4` as `hugerte` version – not the one you used for `tinymce` before. HugeRTE is based on TinyMCE 6.8.4, but it is even later because it contains some code from TinyMCE 7 (all until the [commit which changed the license](https://github.com/tinymce/tinymce/commit/1cfe7f6817c68d713971a3e1dbe0c9775a40ce6d)). See the [Changelog](https://github.com/hugerte/hugerte/blob/main/modules/hugerte/CHANGELOG.md) for details.

## Integrations with Frameworks
- Vue integration: View the [docs](integrations/vue.md) or [repo](https://github.com/hugerte/hugerte-vue).
- React integration: View the [docs](integrations/react.md) or [repo](https://github.com/hugerte/hugerte-react).

Integrations for Svelte, Angular, Blazor, jQuery and Ruby on Rails are following.

## Bundling

You can bundle all required files from HugeRTE into your JavaScript bundle using ES6 module importing syntax and Vite. We're going to check support for other bundlers in the future, too. TinyMCE already [provides docs for bundling](https://www.tiny.cloud/docs/tinymce/6/introduction-to-bundling-tinymce/) but it has an issue with bundling skins that we [fixed](https://github.com/hugerte/hugerte/commit/d62ccbfb11583b5ebb4177986666039da2fe50de) in HugeRTE 1.0.7.

> [!WARNING]
> Make sure you're using HugeRTE 1.0.7 or later so everything works.

The following code snippet demonstrates how to bundle HugeRTE in your project.

```js
// Required parts

// The HugeRTE global. This must be before other HugeRTE imports.
import hugerte from 'hugerte';

// The following imports can be in any order.

// The DOM model
import 'hugerte/models/dom';

// The default icons. This is required, but you can import custom icons after it.
import 'hugerte/icons/default';

// The silver theme. Customization of the look and feel of HugeRTE should be done by custom skins while still using the silver theme.
import 'hugerte/themes/silver';

// The oxide skin (or you can use a custom one).
import 'hugerte/skins/ui/oxide';

// The content skin provided by oxide (or a different skin you're using).
import 'hugerte/skins/ui/oxide/content.js';

// The default content CSS. This can also be replaced by a custom file if needed.
import 'hugerte/skins/content/default/content.js';

// Plugins are optional
// This should correspond to your `plugins` config in the object passed to `hugerte.init()`.
import 'hugerte/plugins/accordion';
import 'hugerte/plugins/advlist';
// etc. for the plugins you're using.

// NOTE: For the emoticons plugin, you'll need two imports:
import 'hugerte/plugins/emoticons';
import 'hugerte/plugins/emoticons/js/emojis';

// NOTE: For the help plugin, you'll need to import the localized keyboard navigation help
// even if it's in english.
import 'hugerte/plugins/help';
import 'hugerte/plugins/help/js/i18n/keynav/en.js';
// Whichever languages you need...
import 'hugerte/plugins/help/js/i18n/keynav/de.js';

// In the `hugerte.init({})` call, set `skin_url` and `content_css` to `default` to make sure the bundled ones are used.
hugerte.init({
    selector: '#editor',
    plugins: 'accordion advlist emoticons help', // etc.
    skin_url: 'default',
    content_css: 'default',
});
```

## Localization
Download the [TinyMCE 6 language pack](https://download.tiny.cloud/tinymce/community/languagepacks/6/langs.zip), extract the languages you need, open all the files of the languages you need and replace the `tinymce` variable at the top by `hugerte`. Then, follow the [instructions by TinyMCE](https://www.tiny.cloud/docs/tinymce/6/ui-localization/#using-the-community-language-packs).

## Customization and Extension

Refer to the TinyMCE docs for now. Some links:
- https://www.tiny.cloud/docs/tinymce/6/customize-ui/
- https://www.tiny.cloud/docs/tinymce/6/apis/tinymce.root/
