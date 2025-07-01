# HugeRTE React integration
This file provides documentation for the [HugeRTE React integration package](https://github.com/hugerte/hugerte-react).

## Get started with integrating HugeRTE into your React project
Add the HugeRTE React component to your project using npm (or an npm-based package manager like yarn):

```bash
npm install @hugerte/hugerte-react
```

or:

```bash
yarn add @hugerte/hugerte-react
```

## TinyMCE React integration docs
We're soon going to provide more extensive docs including code snippets here, but for now, please [visit this link which will redirect you to the TinyMCE docs which provide detailed reference](https://hugerte.org/docs/hugerte/1/react-ref). But, **note that we have changed some props**: Please view the [changelog](https://github.com/hugerte/hugerte-react/blob/main/CHANGELOG.md). Additionally, contrary to what this page says in regard to bundling TinyMCE, we explicitly recommend you to bundle HugeRTE following [our docs](../README.md#bundling).

## Migrating from the TinyMCE React component
1. Replace `tinymce` by `hugerte` (`@tinymce/tinymce-react` to `@hugerte/hugerte-react`).
2. Review the changed props in the [changelog](https://github.com/hugerte/hugerte-react/blob/main/CHANGELOG.md).

## Issues

Have you found an issue with `hugerte-react` or do you have a feature request? Open up an [issue](https://github.com/hugerte/hugerte-react/issues) and let us know or submit a [pull request](https://github.com/hugerte/hugerte-react/pulls). *Note: for issues related to HugeRTE itself please visit the [HugeRTE repository](https://github.com/hugerte/hugerte).*
