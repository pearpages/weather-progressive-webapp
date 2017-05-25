# SW Precache

## Gulp

```js
gulp.task('generate-sw', function () {
    var swOptions = {
        staticFileGlobs: [
            './index.html'
        ],
        stripPrefix: '.',
        runtimeCaching: [{
            urlPattern: /^https:\/\/yourserver\.com/,
            handler: 'networkFirst',
            options: {
                cache: {
                    name: 'cacheDataId'
                }
            }
        }]
    }
    return swPrecache.write('./service-worker.js',swOptions);
});
```

## Webpack

[sw-precache-webpack-plugin](https://www.npmjs.com/package/sw-precache-webpack-plugin)

```js
var path = require('path');
var SWPrecacheWebpackPlugin = require('sw-precache-webpack-plugin');


module.exports = {
  context: __dirname,

  entry: {
    main: path.resolve(__dirname, 'src/index'),
  },

  output: {
    path: path.resolve(__dirname, 'src/bundles/'),
    filename: '[name]-[hash].js',
  },

  plugins: [
    new SWPrecacheWebpackPlugin(
      {
        cacheId: 'my-project-name',
        filename: 'my-service-worker.js',
        maximumFileSizeToCacheInBytes: 4194304,
        minify: true,
        runtimeCaching: [{
          handler: 'cacheFirst',
          urlPattern: /[.]mp3$/,
        }],
      }
    ),
  ]
}
```