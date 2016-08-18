# webpack-cleanup-plugin

This [webpack](http://webpack.github.io) plugin cleans up the extraneous files
from the webpack's output path.

Since it runs when the compile process is finished, it is useful when you build
on production and you want to remove the assets generated by a previous build.

```
npm install webpack-cleanup-plugin --save-dev
```

**Beware!** This plugins actually delete files. Make sure it's safe for your app
to delete files not generated by webpack. Use the `exclude` option if you want to
keep files that are not webpack assets.


## Usage

Add the plugin to the `plugins` array in your webpack's config, e.g.:

```js
{
  output: {
    path: "/my/output/path"
  },
  plugins: [
    // Remove all the files from /my/output/path that are not generated by the
    // the current instance of the webpack compiler
    new WebpackCleanupPlugin()
  ]
}
```

If you want to keep some files, e.g. a stats.json file generated from some other
plugins, use the `exclude` option:

```js
plugins: [
  // Remove all but stats.json and important.json
  new WebpackCleanupPlugin({
    exclude: ["stats.json", "important.js"]
  })
]
```

You can mute console.log output with `quiet` option

```js
  new WebpackCleanupPlugin({
    quiet: true
  })
```
