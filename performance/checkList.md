## Javascript
- Dynamic import

- Tree shaking
  - use `import` 
  - `@babel/preset-env` `modules: false`

- Html `preload`

- Ployfills
  - `@babel/preset-env` `useBuiltIns` `targets`
  
- code splitting

- webpack bundle analyser
- monent.js -> date-fns which support tree shaking and smaller
- 3rd lib, dynamic loading
- performance budget


## Image
https://youtu.be/reztLS3vomE

#### Compression
- npm `imagemin`

#### Format
- Use .mp4 instead of gif
- WebP


#### Size
- Toolin `sharp`, `jimp` 
- Multiple images size
- Html tag `srcset`

#### Lazy loading

## Font
- Flash Of Unstyled Text (FOUT) `font-display: swap`

## CSS
#### Size
- https://medium.freecodecamp.org/reducing-css-bundle-size-70-by-cutting-the-class-names-and-using-scope-isolation-625440de600b
- Renaming CSS class names at the compilation time

## Webpack
#### Long term caching with content hash
- the best option is to use contenthash, which will generate a hash based on its content.
- https://webpack.js.org/guides/caching/
