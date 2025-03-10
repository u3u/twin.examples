<p><img src="https://i.imgur.com/NF4lbSx.png" alt="twin, gatsby, styled-components" width="500"></p>

**Download this example using [degit](https://github.com/Rich-Harris/degit)**

```shell
npx degit https://github.com/ben-rogerson/twin.examples/gatsby-styled-components folder-name
```

From within the new folder, run `npm install`, then `npm start` to start the dev server.

[](#table-of-contents)

## Table of contents

- [Getting started](#getting-started)
  - [Installation](#installation)
  - [Add the global styles](#add-the-global-styles)
  - [Add gatsby-plugin-styled-components](#add-gatsby-plugin-styled-components)
  - [Add the twin config](#add-the-twin-config)
- [Customization](#customization)
- [Next steps](#next-steps)

[](#getting-started)

## Getting started

### Installation

Install Gatsby

```bash
npx gatsby new gatsby-site
```

Install the dependencies

```bash
npm install --save twin.macro tailwindcss styled-components gatsby-plugin-styled-components
```

<details>
  <summary>Install with Yarn</summary>

Install Gatsby

```shell
yarn create gatsby-site
```

Install the dependencies

```shell
yarn add twin.macro styled-components gatsby-plugin-styled-components
```

</details>

### Add the global styles

Twin uses the same [preflight base styles](https://unpkg.com/tailwindcss/dist/base.css) as Tailwind to smooth over cross-browser inconsistencies.

The `GlobalStyles` import adds these base styles along with some @keyframes for the animation classes and some global css that makes the [ring classes](https://tailwindcss.com/docs/ring-width) and box-shadows work.

As we should only add the `GlobalStyles` import once in our project, it’s a good idea to put it in a layout file. You can add Twin’s `GlobalStyles` import in a new file called `src/components/Layout.js`:

```js
// src/components/Layout.js
import React from 'react'
import { GlobalStyles } from 'twin.macro'

const Layout = ({ children, ...rest }) => (
  <div {...rest}>
    <GlobalStyles />
    {children}
  </div>
)

export default Layout
```

Then in your pages, wrap your content with the layout:

```js
// src/pages/index.js
import Layout from './../components/Layout'

const App = () => <Layout>{/* ... */}</Layout>

export default App
```

### Add gatsby-plugin-styled-components

In `gatsby-config.js` register the plugin for styled-components:

```js
// gatsby-config.js
module.exports = {
  plugins: [`gatsby-plugin-styled-components`],
}
```

### Add the twin config

Twin’s config can be added in a couple of different files.

a) Either in `babel-plugin-macros.config.js`:

```js
// babel-plugin-macros.config.js
module.exports = {
  twin: {
    preset: 'styled-components',
  },
}
```

b) Or in `package.json`:

```js
// package.json
"babelMacros": {
  "twin": {
    "preset": "styled-components"
  }
},
```

[](#customization)

## Customization

- [View the config options →](https://github.com/ben-rogerson/twin.macro/blob/master/docs/options.md)
- [Customizing the tailwind config →](https://github.com/ben-rogerson/twin.macro/blob/master/docs/customizing-config.md)

[](#next-steps)

## Next steps

Learn how to work with twin

- [The prop styling guide](https://github.com/ben-rogerson/twin.macro/blob/master/docs/prop-styling-guide.md) - A must-read guide to level up on prop styling
- [The styled component guide](https://github.com/ben-rogerson/twin.macro/blob/master/docs/styled-component-guide.md) - A must-read guide on getting productive with styled-components

Learn more about styled-components

- [The css prop](https://styled-components.com/docs/api#css-prop)
- [The css import](https://styled-components.com/docs/api#css)
- [The styled import](https://styled-components.com/docs/api#styled)
