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

## 2、
在src目录下添加lib文件夹，并分别建立css.js和script.js
``` js
    src
    |--lib
    |--|--css.js
    |--|--script.js
```
``` js
//css.js
import 'bootstrap/dist/css/bootstrap.min.css'
import 'admin-lte/dist/css/AdminLTE.min.css'
import 'admin-lte/dist/css/skins/_all-skins.min.css'
import 'font-awesome/css/font-awesome.min.css'
```

``` js
// script.js

import 'bootstrap'
import 'admin-lte'


```
