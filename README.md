# Create-React-App with TailwindUI

This repo is a template to show how to intergrate TailWindUI with the Create-React-App repo.

You can either fork this repo or follow the following instuctions on your own Create-React-App.

## Setup

Install the required libraries and create the two config files by running the following commands:

```
npm install tailwindcss@npm:@tailwindcss/postcss7-compat @tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9
npm install @craco/craco
npm install @headlessui/react
npx tailwindcss init
touch craco.config.js
```

Populate `craco.congif.js` with the following:

```
module.exports = {
  style: {
    postcss: {
      plugins: [
        require('tailwindcss'),
        require('autoprefixer'),
      ],
    },
  },
}
```

Populate `tailwind.config.js` with the following:

```
module.exports = {
  purge: ['./src/**/*.{js,jsx,ts,tsx}', './public/index.html'],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```

Alter `package.json` with the following:

```
"scripts": {
    "start": "craco start",
    "build": "craco build",
    "test": "craco test",
    "eject": "react-scripts eject"
  },
```

Change the contents of `index.css` with the following:

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Now you should be able to add any TailwindUI componenets - be sure to check out [this extension](https://chrome.google.com/webstore/detail/tailwind-ui-react/binfindfddkgfibeajgkmjioklcgigjn) to auto generate react components from the html snippets.

### Optional - Fonts

All TailwindUI previews use the Inter var font. To do the same add the following to `public/index.html`:

```
<link rel="stylesheet" href="https://rsms.me/inter/inter.css">
```

Then replace `tailwind.config.js` with the following:

```
const defaultTheme = require('tailwindcss/defaultTheme')

module.exports = {
  purge: ['./src/**/*.{js,jsx,ts,tsx}', './public/index.html'],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter var', ...defaultTheme.fontFamily.sans],
      },
    },
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```
