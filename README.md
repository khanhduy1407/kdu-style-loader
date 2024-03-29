# kdu-style-loader

This is a fork based on [style-loader](https://github.com/webpack/style-loader). Similar to `style-loader`, you can chain it after `css-loader` to dynamically inject CSS into the document as style tags. However, since this is included as a dependency and used by default in `kdu-loader`, in most cases you don't need to configure this loader yourself.

### Differences from `style-loader`

#### Server-Side Rendering Support

When bundling with `target: 'node'`, the styles in all rendered components are collected and exposed on the Kdu render context object as `context.styles`, which you can simply inline into your markup's `<head>`. If you are building a Kdu SSR app, you probably should use this loader for CSS imported from JavaScript files too.

#### Misc

- Does not support url mode and reference counting mode. Also removed `singleton` and `insertAt` query options. It always automatically pick the style insertion mechanism that makes most sense. If you need these capabilities you should probably use the original `style-loader` instead.

- Fixed the issue that root-relative URLs are interpreted against chrome:// urls and make source map URLs work for injected `<style>` tags in Chrome.
