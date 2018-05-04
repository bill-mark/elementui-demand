# elementui-demand
vue 2.X和elementui 2.X搭配使用时,按需引入.

# 按需引入前elementUI大小是超过1M,按需引入后500K左右,可以直接demo看看 

# 按需引入流程
# 第一步
项目目录执行  npm install babel-plugin-component –D

# 第二步
修改babelrc配置,
这里elementUi官网是说把babelrc修改为他们推荐的,注意了如果直接修改就报错了,
哪怕不报错如果你的路由是懒加载的就回报语法错误
所以,babelrc应该修改为

```
{
  "presets": [
    ["env", { "modules": false }],
    ["es2015", { "modules": false }],
    "stage-2"
  ],
  "plugins": [["component", [
    {
      "libraryName": "element-ui",
      "styleLibraryName": "theme-chalk"
    }
  ]],"transform-runtime"],
  "comments": false,
  "env": {
    "test": {
      "presets": ["env", "stage-2"],
      "plugins": [ "istanbul" ]
    }
  }
}
```

如果elementui版本是1.X,则styleLibraryName的值要修改为theme-default

# 第三步
在main.js中按需引入组件

比如要按需引入button,则为

```
import Vue from 'vue'

import App from './App'

import router from './router'

import 'element-ui/lib/theme-chalk/index.css'

import { Button } from 'element-ui'

Vue.use(Button)

Vue.config.productionTip = false

/* eslint-disable no-new */

new Vue({
  el: '#app',
  router,
  components: { App },
  template: '<App/>'
})
```

# 报错
如果报错Module build failed: Error: Couldn't find preset "es2015" relative to directory 

则执行npm install babel-preset-es2015 --save-dev
