# HugeRTE React integration
This file provides documentation for the [HugeRTE React integration package](https://github.com/hugerte/hugerte-react).

## Storybook
The repo linked above comes with a storybook showing examples of integrating HugeRTE with React. To run the storybook, follow the following steps:
1. Clone the repo:
   ```bash
   git clone https://github.com/hugerte/hugerte-react
   ```
2. Install dependencies:
   ```bash
   yarn
   ```
3. Run the storybook:
   ```bash
   yarn storybook
   ```

[View the source code of the Storybook examples.](https://github.com/hugerte/hugerte-react/blob/main/src/stories/Editor.stories.tsx).

## Get started with integrating HugeRTE into your React project
Add the HugeRTE React component to your project using npm (or an npm-based package manager like yarn):

```bash
npm install @hugerte/hugerte-react
```

or:

```bash
yarn add @hugerte/hugerte-react
```

Then, you could copy an appropiate demo piece from the storybook file linked above into your project. **While the storybook file contains `import { Editor, IAllProps } from '../main/ts/components/Editor';`, you should import from `@hugerte/hugerte-react` instead.** If your code will contain non-trivial portions of demo code, add the text of the [LICENSE.txt](LICENSE.txt) file as a comment to your code or on some „Acknowledgements“ page to ensure legal compliance.

## TinyMCE React integration docs
Instead of looking at the Storybook and copying code from there, you can also [visit this link which will redirect you to the TinyMCE docs for now which provide detailed reference](https://hugerte.org/docs/hugerte/1/react-ref). But, **note that we have changed some props**: Please view the [changelog](https://github.com/hugerte/hugerte-react/blob/main/CHANGELOG.md). Additionally, contrary to what this page says in regard to bundling TinyMCE, we explicitly recommend you to bundle HugeRTE following [our docs](../README.md#bundling).

## Issues

Have you found an issue with `hugerte-react` or do you have a feature request? Open up an [issue](https://github.com/hugerte/hugerte-react/issues) and let us know or submit a [pull request](https://github.com/hugerte/hugerte-react/pulls). *Note: for issues related to HugeRTE itself please visit the [HugeRTE repository](https://github.com/hugerte/hugerte).*
