# Underscores & TailwindCSS

## 1. Create Unscores theme

- https://underscores.me/
- Ensure `Sassify` is clicked

## 2. Install TailwindCSS

```bash
# Using npm
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest

# Using Yarn
yarn add tailwindcss
```

## 3. Setup your `style.scss` file

- https://tailwindcss.com/docs/installation#2-add-tailwind-to-your-css
- Navigate to the `sass` directory
- Open the `style.scss` file
- Add the tailwind directives after the commented table of contents
- This will ensure your tailwind classes are generated before the included CSS, which allows you to use the `@apply` tailwind directive and use your utility classes in your WordPress styles

```scss
@tailwind base;

@tailwind components;

@tailwind utilities;
```

## 4. Publish the TailwindCSS config file

```bash
npx tailwindcss init
```

## 5. Install Laravel Mix

```bash
# Using npm
npm install laravel-mix --save-dev

# Using yarn
yarn add laravel-mix --dev
```

## 6. Publish the Laravel Mix config file

```bash
touch webpack.mix.js
```

## 7. Update the default Laravel Mix file for Tailwind

```js
let mix = require('laravel-mix');
let tailwindcss = require('tailwindcss')

mix.sass('sass/style.scss', 'style.css')
  .options({
    processCssUrls: false,
    postCss: [ tailwindcss('tailwind.config.js') ],
  });
```

## 8. Add the Laravel Mix scripts to your `package.json` file

- https://laravel-mix.com/docs/5.0/installation#npm-scripts
- You will need to rename the Laravel Mix  `watch` command because underscores also defines a `watch` command
- You will probably need to install `cross-env` as well

```bash
# Using npm
npm install cross-env --save-dev

# Using yarn
yarn add cross-env --dev
```

```json
"scripts": {
    "dev": "npm run development",
    "development": "mix",
    "mix-watch": "mix watch",
    "watch-poll": "mix watch -- --watch-options-poll=1000",
    "hot": "mix watch --hot",
    "prod": "npm run production",
    "production": "mix --production",    
}
```

## 9. Trying compiling your assets

```bash
npm run dev
```

## 10. Update your Tailwind config to purge your unused CSS

- This is an example config, please edit to match your needs

```js
module.exports = {
    purge: [
        './inc/**/*.php',
        './js/**/*.js',
        './sass/**/*.scss',
        './template-parts/**/*.php',
    ],
    theme: {
        extend: {},
    },
    variants: {},
    plugins: [],
}
```
