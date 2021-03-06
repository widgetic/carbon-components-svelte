# carbon-components-svelte

[![NPM][npm]][npm-url]
[![Build][build]][build-badge]

> Svelte implementation of the [Carbon Design System](https://github.com/carbon-design-system)

## Getting started

Install `carbon-components-svelte` as a development dependency.

```bash
yarn add -D carbon-components-svelte
# OR
npm -i -D carbon-components-svelte
```

## Usage

The quickest way to get started is to customize a template from the [examples](examples/) folder.

Example set-ups demonstrate usage with popular application bundlers and frameworks. They feature a mix of Singe-page Applications (SPA), Server-side rendering (SSR) and statically exported approaches.

- **[examples/rollup](examples/rollup/)**: SPA bundled using [Rollup](https://github.com/rollup/rollup)
- **[examples/rollup-typescript](examples/rollup-typescript/)**: SPA bundled using [Rollup](https://github.com/rollup/rollup) with TypeScript support
- **[examples/routify](examples/routify/)**: SPA + static export using [Routify](https://github.com/roxiness/routify)
- **[examples/sapper](examples/sapper/)**: SSR + static export using [Sapper](https://github.com/sveltejs/sapper)
- **[examples/svite](examples/svite/)**: SPA developed with Svite, bundled with [Rollup](https://github.com/rollup/rollup)
- **[examples/webpack](examples/webpack/)**: SPA bundled with [webpack](https://github.com/webpack/webpack)

### Scaffolding

Each example is published in a dedicated branch of the same name.

Use [degit](https://github.com/Rich-Harris/degit) to scaffold a new project:

For example, to use the `svite` template, run the following commands:

```sh
npx degit ibm/carbon-components-svelte#svite svelte-app
cd svelte-app
yarn install
```

### Importing components

Import components from `carbon-components-svelte` in the `script` tag of your Svelte file.

```html
<!-- App.svelte -->
<script>
  import { Accordion, AccordionItem } from "carbon-components-svelte";
</script>

<Accordion>
  <AccordionItem title="Section 1" open> Content 1 </AccordionItem>
  <AccordionItem title="Section 2"> Content 2 </AccordionItem>
  <AccordionItem title="Section 3"> Content 3 </AccordionItem>
</Accordion>
```

**Refer to [COMPONENT_INDEX.md](COMPONENT_INDEX.md) for component API documentation.**

### Precompiled CSS StyleSheets

`carbon-components-svelte` includes precompiled CSS StyleSheets for each Carbon theme:

- **white.css**: Default Carbon theme (light)
- **g10.css**: Gray 10 theme (light)
- **g90.css**: Gray 90 theme (dark)
- **g100.css**: Gray 100 theme (dark)
- **all.css**: All themes (White, Gray 10, Gray 90, Gray 100) using CSS variables

Each StyleSheet is [generated](scripts/build-css.js) from the flagship [carbon-components](https://github.com/carbon-design-system/carbon/tree/master/packages/components) library.

The [examples](examples/) use `all.css` for dynamic theming through CSS variables.

Because the CSS is precompiled, it includes all Carbon design styles. One method to optimize the CSS is to ship only the CSS that is used. This can be accomplished using [PurgeCSS](https://github.com/FullHuman/purgecss) with a Carbon style extractor (WIP).

#### Usage

##### `svelte-preprocess`

The easiest way to import a StyleSheet is with [svelte-preprocess](https://github.com/sveltejs/svelte-preprocess).

```js
const svelteOptions = {
  preprocess: require("svelte-preprocess")(),
};
```

```html
<!-- App.svelte -->
<style lang="scss" global>
  /** Gray 10 theme **/
  @import "carbon-components-svelte/css/g10";
</style>
```

##### JavaScript import

Importing a CSS file in a JavaScript file will require the appropriate file loader(s).

```js
import "carbon-components-svelte/css/all.css";
import App from "./App.svelte";

const app = new App({ target: document.body });

export default app;
```

See [webpack.config.js](examples/webpack/webpack.config.js) in [examples/webpack](examples/webpack).

### TypeScript support

The component library ships with TypeScript definitions ([types/index.d.ts](types/index.d.ts)).

## Contributing

Refer to the [Contributing guidelines](CONTRIBUTING.md).

## [Changelog](CHANGELOG.md)

## License

[Apache 2.0](LICENSE)

[npm]: https://img.shields.io/npm/v/carbon-components-svelte.svg?color=blue
[npm-url]: https://npmjs.com/package/carbon-components-svelte
[build]: https://travis-ci.com/ibm/carbon-components-svelte.svg?branch=master
[build-badge]: https://travis-ci.com/ibm/carbon-components-svelte
