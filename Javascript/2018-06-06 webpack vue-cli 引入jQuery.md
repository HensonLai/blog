## 1、引入jQuery
webpack.base.conf.js 添加
``` js
const webpack = require('webpack')
```
在module.exports 的后面追加，则在项目内部可以使用jquery了，但是浏览器的console用不了，需求将$ 暴露出来
``` js
  plugins: [
    new webpack.optimize.CommonsChunkPlugin('common.js'),
    new webpack.ProvidePlugin({
      $: 'jquery',
      jquery: 'jquery',
      'window.jQuery': 'jquery',
      jQuery: 'jquery'
    })
  ]
```
在moudle.rules里面添加
``` js
      {
        test: require.resolve('jquery'),
        use: [{
            loader: 'expose-loader',
            options: '$'
        }]
      }
```
