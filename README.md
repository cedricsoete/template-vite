# Setup React

## VITE template

npm init vite@latest vitejs -- --templace react

## React JSX

npm i -D vite-react-jsx

edit vite.config.js

```js
import { defineConfig } from "vite";
import reactRefresh from "@vitejs/plugin-react-refresh";
// NEW
import reactJsx from "vite-react-jsx";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    reactRefresh(),
    // NEW
    reactJsx(),
  ],
});
```

remove 'import React from 'react'

## alias

edit vite.config.js

```js
import { defineConfig } from "vite";
import reactRefresh from "@vitejs/plugin-react-refresh";
import reactJsx from "vite-react-jsx";
// NEW
import { resolve } from "path";

export default defineConfig({
  plugins: [reactRefresh(), reactJsx()],
  // new
  resolve: {
    alias: {
      "~": resolve(__dirname, "src"),
    },
  },
});
```

jsconfig.json

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "~/*": ["./src/*"]
    }
  }
}
```

## SCSS

```sh
npm i -D sass
```

## Storybook

```sh
npx sb init
npm i -D storybook-builder-vite
```

edit .storybook/main.js

```js
// NEW
const reactJsx = require("vite-react-jsx");

module.exports = {
  stories: ["../src/**/*.stories.mdx", "../src/**/*.stories.@(js|jsx|ts|tsx)"],
  addons: ["@storybook/addon-links", "@storybook/addon-essentials"],
  // NEW
  core: {
    builder: "storybook-builder-vite",
  },
  // NEW
  async viteFinal(config, { configType }) {
    config.plugins.push(reactJsx.default());
    return config;
  },
};
```
