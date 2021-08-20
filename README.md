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
