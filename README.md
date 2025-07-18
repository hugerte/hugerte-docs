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
These docs are stil in an Alpha stage. You'll mostly have to check the [TinyMCE 6 docs](https://tiny.cloud/docs/tinymce/6). We want to write the docs in our own words instead of forking the TinyMCE docs because the latter are licensed under a [CC BY-NC-SA license](https://github.com/tinymce/tinymce-docs/blob/main/LICENSE.txt) which we don't want to use. See [this informative line](https://github.com/hugerte/hugerte-website/blob/04a9373b099a0acc1c29929e215214a8f775d7aa/index.php#L34) also.
When referring to the TinyMCE docs, make sure to replace all occurrences of `tinymce` by `hugerte` in your code.

[See this guide also](https://www.tiny.cloud/docs/tinymce/6/npm-projects/), but replace `tinymce@^6` by `hugerte@^1` (and of course, all occurrences of `tinymce` by `hugerte`).

Important links:
- https://www.tiny.cloud/docs/tinymce/6/basic-setup/
- https://www.tiny.cloud/docs/tinymce/6/use-tinymce-classic/
- https://www.tiny.cloud/docs/tinymce/6/use-tinymce-inline/
- https://www.tiny.cloud/docs/tinymce/6/use-tinymce-distraction-free/

## Migrate from TinyMCE

If you have been using TinyMCE before, you have to globally replace `tinymce` by `hugerte` in your code. In your package.json, make sure you use `1.0.4` as `hugerte` version – not the one you used for `tinymce` before. HugeRTE is based on TinyMCE 6.8.4, but it is even later because it contains some code from TinyMCE 7 (all until the [commit which changed the license](https://github.com/tinymce/tinymce/commit/1cfe7f6817c68d713971a3e1dbe0c9775a40ce6d)). See the [Changelog](https://github.com/hugerte/hugerte/blob/main/modules/hugerte/CHANGELOG.md) for details.

## Integrations with Frameworks and Other Tools
### Official integrations
- Vue integration: View the [docs](integrations/vue.md) or [repo](https://github.com/hugerte/hugerte-vue).
- React integration: View the [docs](integrations/react.md) or [repo](https://github.com/hugerte/hugerte-react).
- Angular integration: View the [docs](integrations/angular.md) or [repo](https://github.com/hugerte/hugerte-angular).

### Inofficial community integrations
These are maintained by the community – thank you!
- [Ruby on Rails integration](https://github.com/liberaldev/hugerte-rails).
- [Laravel Nova field](https://github.com/pekhota/nova-hugerte)

Integrations for Svelte, jQuery and Blazor will get published (forked from their TinyMCE counterparts) if there's demand for them – please [open a discussion](https://github.com/orgs/hugerte/discussions/new/choose) in case they'd be nice for you. Or just ask for them anonymously in the survey at https://hugerte.org. It doesn't matter if only one person needs them or if it's for production or testing use. Just ask and we'll start providing and maintaining. An integration for Alpine.js may also be created if there's demand for it.

## Bundling

You can bundle all required files from HugeRTE into your JavaScript bundle using ES6 module importing syntax and Vite. We're going to check support for other bundlers in the future, too. TinyMCE already [provides docs for bundling](https://www.tiny.cloud/docs/tinymce/6/introduction-to-bundling-tinymce/) but it has an issue with bundling skins that we [fixed](https://github.com/hugerte/hugerte/commit/d62ccbfb11583b5ebb4177986666039da2fe50de) in HugeRTE 1.0.7. Going forward, bundling is the recommended way to include HugeRTE into your project. Make sure to outsource the HugeRTE imports into a separate chunk if you don't need HugeRTE on every page where you include your main bundled JS chunk.

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
import 'hugerte/skins/ui/oxide/skin.js';

// The content skin provided by oxide (or a different skin you're using).
import 'hugerte/skins/ui/oxide/content.js';

// The default content CSS. This can also be replaced by a custom file if needed.
import 'hugerte/skins/content/default/content.js';

// Plugins are optional
// This should correspond to your `plugins` config in the object passed to `hugerte.init()`.
import 'hugerte/plugins/accordion';
import 'hugerte/plugins/advlist';
import 'hugerte/plugins/anchor';
import 'hugerte/plugins/autolink';
import 'hugerte/plugins/autoresize';
import 'hugerte/plugins/autosave';
import 'hugerte/plugins/charmap';
import 'hugerte/plugins/code';
import 'hugerte/plugins/codesample';
import 'hugerte/plugins/directionality';
import 'hugerte/plugins/fullscreen';
import 'hugerte/plugins/image';
// We'll have to investigate before recommending to use this one: https://github.com/hugerte/hugerte/issues/24
// import 'hugerte/plugins/importcss';
import 'hugerte/plugins/insertdatetime';
import 'hugerte/plugins/link';
import 'hugerte/plugins/lists';
import 'hugerte/plugins/media';
import 'hugerte/plugins/nonbreaking';
import 'hugerte/plugins/pagebreak';
import 'hugerte/plugins/preview';
import 'hugerte/plugins/quickbars';
import 'hugerte/plugins/save';
import 'hugerte/plugins/searchreplace';
import 'hugerte/plugins/table';
import 'hugerte/plugins/template';
import 'hugerte/plugins/visualblocks';
import 'hugerte/plugins/visualchars';
import 'hugerte/plugins/wordcount';

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
    // Adjust this as needed
    plugins: 'accordion advlist anchor autolink autoresize autosave charmap code codesample directionality fullscreen image insertdatetime link lists media nonbreaking pagebreak preview quickbars save searchreplace table template visualblocks visualchars wordcount emoticons help',
    skin_url: 'default',
    content_css: 'default',
});
```

## Localization
Download the [TinyMCE 6 language pack](https://download.tiny.cloud/tinymce/community/languagepacks/6/langs.zip), extract the languages you need, open all the files of the languages you need and replace the `tinymce` variable at the top by `hugerte`. Then, follow the [instructions by TinyMCE](https://www.tiny.cloud/docs/tinymce/6/ui-localization/#using-the-community-language-packs).
If you're bundling all HugeRTE assets into one file (as the section above demonstrates), you can import the languge file too.

## Customization and Extension

Refer to the TinyMCE docs for now. Some links:
- https://www.tiny.cloud/docs/tinymce/6/customize-ui/
- https://www.tiny.cloud/docs/tinymce/6/apis/tinymce.root/

## Plugins
HugeRTE comes with various plugins that can enhance your editing experience. These can be activated by adding their IDs to the `plugins` option in the configuration object passed to the `hugerte.init` method. Providing instructions on using these plugins without referring to the TinyMCE docs is a work in progress.
- accordion: Allows you to insert accordions into the editor via `Insert > Accordion`. See https://hugerte.org/docs/hugerte/1/advlist for more information.
- advlist: https://hugerte.org/docs/hugerte/1/advlist
- anchor: https://hugerte.org/docs/hugerte/1/anchor
- autolink: https://hugerte.org/docs/hugerte/1/advlist
- autoresize: https://hugerte.org/docs/hugerte/1/advlist
- autosave: https://hugerte.org/docs/hugerte/1/autosave
- charmap: https://hugerte.org/docs/hugerte/1/charmap
- code: https://hugerte.org/docs/hugerte/1/code
- codesample: https://hugerte.org/docs/hugerte/1/codesample
- directionality: https://hugerte.org/docs/hugerte/1/directionality
- emoticons: https://hugerte.org/docs/hugerte/1/emoticons
- fullscreen: https://hugerte.org/docs/hugerte/1/fullscreen
- help: https://hugerte.org/docs/hugerte/1/help
- image: https://hugerte.org/docs/hugerte/1/image
- importcss: https://hugerte.org/docs/hugerte/1/importcss. Warning: This plugin is affected by [a bug](https://github.com/hugerte/hugerte/issues/24).
- TODO: Continue list and elaborate descriptions and instructions. For now, see https://hugerte.org/docs/hugerte/1/plugins/#open-source-plugins

## Themes
Themes allow you to fully customize the layout of the editor. They're pretty low-level. Unless you want to create a completely new layout for HugeRTE, you should create skins instead. The only official theme available in HugeRTE is the silver theme. If you'd like to get an impression of what it takes to build a new theme, you can [browse the silver theme codebase](https://github.com/hugerte/hugerte/blob/main/modules/hugerte/src/themes/silver).

## Skins
TODO

## Help shape the future of this project!
After you have integrated HugeRTE into your project and tested it, we'd like to kindly ask you to spend two minutes on completing the survey available at the [HugeRTE homepage](https://hugerte.org). You don't need to answer in full sentences. Your feedback is very important for us because it shows us the engagement of the community and tells us how we can improve this project and what's most important for you.

## Support us
HugeRTE is currently not company-funded and maintained by a single person. We appreciate both donations and help with development. If you'd like to support us financially, you can sponsor on [our OpenCollective profile](https://opencollective.com/hugerte). If you'd like to get something out of a sponsorship, like personal support or custom development, please contact us beforehand by sending a mail to admin AT hugerte DOT org.
