目录结构
========
前端目录结构如下
~~~
Mzshop
|-common                公共文件目录
|  |-util.js            助手函数文件
|-components            自定义组件
|  |-common             公共自定义组件目录
|  |-index              首页自定义组件目录
|  |-type               分类页自定义组件目录
|  |-cart               购物车页自定义组件目录
|  |-mine               个人中心页自定义组件目录
|-pages                 页面文件目录
|  |-tabs               tabbar页面目录
|     |-index.vue       首页
|     |-type.vue        分类页
|     |-cart.vue        购物车
|     |-mine.vue        个人中心页
|-static                静态资源文件目录
|-store                 全局状态管理文件目录
|-App.vue               应用生命周期文件
|-main.js               应用入口文件
|-manifest.json         配置文件
|-pages.json            页面配置文件
|-uni.scss              css预处理文件
├─LICENSE.txt           授权说明文件
├─README.md             README 文件
~~~
1. common/util.js  
`common`目录通常用来存放一些全局性文件，例如通用样式文件或者工具函数文件。  
其中，util.js就是官方书写的全局工具函数，并且各函数已经挂在到Vue.prototype下，可以在项目中的任何一个地方调用。具体使用方式可参阅[全局工具函数](tool.md)  
2. components目录
`components`目录存放自定义组件。本项目全部采用组件化开发，故自定义组件非常多，我们也同样推荐开发者采用这种方式进行开发，有利于代码维护。  
`components/common`目录存放公共自定义组件；  
`components/index`目录存放首页自定义组件； 
`components/type`目录存放分类页自定义组件； 
`components/cart`目录存放购物车页面自定义组件；
`components/mine`目录存放个人中心页面自定义组件；  
通过以上介绍不难看出，每一个页面，都在`components`目录里有一个对应的子目录用于存放其使用到的自定义组件，而对于各个页面公用的自定义组件，则存放到`components/common`目录里。  
**以上目录结构是我们在大量实践中总结出的精华，在做复杂项目时有利于管理及维护。我们强烈推荐开发者采用同样的目录结构模式。**
3. `pages`目录
`pages`目录存放页面文件。我们将`tabbar`管理的4个页面，全部放入了`pages/tabs`子目录下，目的是方便开发者二次开发时能够更快进行页面分类。
>`pages`目录下的所有页面，一定要在`pages.json`文件里进行注册，否则会出现路由找不到页面文件。虽然这是个常识性问题，但是我们觉得有必要强调一下，避免部分开发者掉坑。  
4. `static`目录
`static`目录存放静态资源，包括图片、字体文件等。值得注意的是，因为微信小程序对代码包大小有限制，我们建议除了一些基本的图标文件外，其余图片都采用网络加载方式。  
>`static`目录下同样建议按照页面设置子目录存放文件哟！
5. `store`目录
`store`目录下只有一个`index.js`文件，用于全局状态管理，建议开发者不要修改。
6. `App.vue`文件
会Vue.js的亲都懂的`App.vue`文件的作用。这里主要监听应用声明周期，同时也可以书写全局样式
7. `main.js`文件
这是最重要的应用入口文件，主要用于生成Vue实例，挂载全局方法和全局变量。高级开发者可以根据需要修改该文件。
8. `manifest.json`文件
这是应用配置文件,可对App及小程序常用参数进行配置，例如设置App图标、开屏图等。具体配置方法可参阅[manifest.json配置](https://uniapp.dcloud.io/collocation/manifest)
9. `pages.json`
这是页面管理文件，负责对所有文件进行注册，同时也可配置页面的窗口样式、导航栏等。具体配置方法可参阅[pages.json配置](https://uniapp.dcloud.io/collocation/pages)
10. `uni.scss`文件
该文件保留了UniAPP官方所有的scss变量，我们仅添加了主题色$theme-color,开发者可以修改该变量，从而让应用变成您想要的样子