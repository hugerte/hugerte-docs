# HugeRTE docs

This repo contains documentation for the [HugeRTE](https://github.com/hugerte/hugerte) editor.

## Get started with HugeRTE

The simplest way to get started with HugeRTE is using a CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/hugerte@1.0.4/hugerte.min.js">
```

Or install it manually via `npm`:

```bash
npm i hugerte
```

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

Integrations for Svelte, React, Angular, Blazor, jQuery and Ruby on Rails are following.

## Bundling: Not supported yet
You might want to bundle HugeRTE into your JavaScript output build using a bundler like Webpack or Vite. This procedure, however, is complex and error-prone at the time and therefore not recommended or supported by us. We're going to, however, work on fixing the issues that occur when bundling and providing appropiate documentation for it after that. For now, if using a bundler, you should use a plugin like [vite-plugin-static-copy](https://www.npmjs.com/package/vite-plugin-static-copy) or [copy-webpack-plugin](npmjs.com/package/copy-webpack-plugin) to copy the whole `ǹode_modules/hugerte` folder to your public directory without modifying its contents (while adding a hash to the copied `hugerte` folder itself is recommended).

## Localization
Download the [TinyMCE 6 language pack](https://download.tiny.cloud/tinymce/community/languagepacks/6/langs.zip), extract the languages you need, open all the files of the languages you need and replace the `tinymce` variable at the top by `hugerte`. Then, follow the [instructions by TinyMCE](https://www.tiny.cloud/docs/tinymce/6/ui-localization/#using-the-community-language-packs).

## Customization and Extension

Refer to the TinyMCE docs for now. Some links:
- https://www.tiny.cloud/docs/tinymce/6/customize-ui/
- https://www.tiny.cloud/docs/tinymce/6/apis/tinymce.root/
