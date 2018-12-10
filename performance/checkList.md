## Javascript
- Dynamic import - React.lazy

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

#### Tree shaking
- only load needed icon
- react-icons

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

#### Common Bundle
- NPM packages change less often than our app code, so we don’t need to force users to download all your NPM packages if nothing has changed. This is usually called the vendor bundle.

- What about your own code that also change less often? Maybe you have a few basic components like Button, Grid, Toggle, etc. that have been created some time ago and haven't changed in a while. This is a good candidate for a common bundle

#### Credit
- https://dev.to/goenning/how-we-reduced-our-initial-jscss-size-by-67-3ac0?fbclid=IwAR0S5CwGF3B9Fk3h3MlPXMdyCMVsICYoNh8p5oUO33MokQbTjTfJ7nxkT7w
