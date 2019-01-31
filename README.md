# Awesome-Frontend-Libs
🎉 整理平时常用的前端库~~~

## 构建工具

*   [bower](https://github.com/bower/bower) - 软件包管理器
*   [yarn](https://yarnpkg.com/lang/zh-hans) - 依赖管理
*   [npm](https://www.npmjs.cn) - 依赖管理
*   [nrm](https://github.com/Pana/nrm) - npm镜像管理
*   [nvm](https://github.com/Pana/nrm) - node 版本管理
*   [browser-sync](http://browsersync.cn/) - 省时的浏览器同步测试工具

## 打包工具

*   [webpack](https://webpack.docschina.org) - 现代 JavaScript 应用程序的静态模块打包器
*   [rollup](https://www.rollupjs.com/guide/zh) - 更加适合用于构建 Library
*   [parcel](https://zh.parceljs.org) - 极速零配置Web应用打包工具
*   [systemjs](https://github.com/systemjs/systemjs) - 通用模块加载器，支持AMD、CommonJS、ES6等各种格式的JS模块加载，也是Angular2官推的加载器
*   [microbundle](https://github.com/developit/microbundle) - 由Rollup提供支持的小型模块零配置打包程序

### webpack插件

*   [add-asset-html-webpack-plugin](https://github.com/SimenB/add-asset-html-webpack-plugin) - 将打包后的文件，加入html中
*   [clean-webpack-plugin](https://github.com/johnagan/clean-webpack-plugin) - 目录清空
*   [compression-webpack-plugin](https://github.com/webpack-contrib/compression-webpack-plugin) - gzip 压缩
*   [copy-webpack-plugin](https://github.com/webpack-contrib/copy-webpack-plugin) - 对资源文件进行拷贝粘贴
*   [extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin) - 分离项目中的css文件
*   [friendly-errors-webpack-plugin](https://github.com/geowarin/friendly-errors-webpack-plugin) - 错误友好提示
*   [webpack-merge](https://github.com/survivejs/webpack-merge) - 合并 webpack 配置
*   [webpack-chain](https://github.com/neutrinojs/webpack-chain) - 通过 chain 风格 api 的方式修改 webpack 配置
*   [webpack-dev-server](https://github.com/webpack/webpack-dev-server) - webpack 开发服务器
*   [webpack-dev-middleware](https://github.com/webpack/webpack-dev-middleware) - webpack 中间件
*   [hard-source-webpack-plugin](https://github.com/mzgoddard/hard-source-webpack-plugin) - 开启 webpack 缓存，二次启动时间减少 80% -
*   [svgr](https://github.com/smooth-code/svgr) - 将SVG转换为React组件🦁
*   [postcss](https://github.com/postcss/postcss) - 提供了一种方式用 JavaScript 代码来处理 CSS
*   [autoprefixer](https://github.com/postcss/autoprefixer) - 处理CSS前缀问题
*   [cssnano](https://github.com/cssnano/cssnano) - 压缩和优化你的css
*   [webpackbar](https://github.com/nuxt/webpackbar) - 终端输出进度条
*   [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) - webpack打包性能分析
*   [terser-webpack-plugin](https://github.com/webpack-contrib/terser-webpack-plugin) - JS压缩(ES6)
*   [uglifyjs-webpack-plugin](https://github.com/webpack-contrib/uglifyjs-webpack-plugin) - JS压缩(ES5)
*   [webpack-manifest-plugin](https://github.com/danethurber/webpack-manifest-plugin) - Webpack 的静态资源持久缓存
*   [case-sensitive-paths-webpack-plugin](https://github.com/Urthen/case-sensitive-paths-webpack-plugin) - 路径大小写敏感问题
*   [css-hot-loader](https://github.com/shepherdwind/css-hot-loader) - 模块热替换
*   [duplicate-package-checker-webpack-plugin](https://github.com/darrenscerri/duplicate-package-checker-webpack-plugin) - 对项目中的重复包进行检测，以便于对项目进行引用优化
*   [fork-ts-checker-webpack-plugin](https://github.com/Realytics/fork-ts-checker-webpack-plugin) - 类型检查

## babel

*   [babel](https://www.babeljs.cn) - 用于编写下一代JavaScript 的编译器
*   [babel-cli](https://github.com/babel/babel/tree/master/packages/babel-cli) - 自带一个 babel-node 命令，提供一个支持ES6的REPL环境
*   [babel-core](https://github.com/babel/babel/tree/master/packages/babel-core) - 把js代码分析成ast，方便各个插件分析语法进行相应的处理
*   [babel-eslint](https://github.com/babel/babel-eslint) - 围绕Babel解析器的包装器，使其与ESLint兼容
*   [babel-helper-vue-jsx-merge-props](https://github.com/vuejs/babel-helper-vue-jsx-merge-props) - 让Vue支持JSX语法
*   [babel-loader](https://github.com/babel/babel-loader) - 用来处理ES6语法，将其编译为浏览器可以执行的js语法
*   [babel-plugin-syntax-dynamic-import](https://github.com/babel/babel/tree/master/packages/babel-plugin-syntax-dynamic-import) - 动态import
*   [babel-plugin-transform-class-properties](https://babel.bootcss.com/docs/plugins/transform-class-properties) - class 属性转换
*   [babel-plugin-transform-decorators-legacy](https://github.com/loganfsmyth/babel-plugin-transform-decorators-legacy) - 支持装饰器语法
*   [babel-plugin-transform-object-rest-spread](https://babeljs.io/docs/en/babel-plugin-proposal-object-rest-spread) - 支持Object的spread操作符
*   [babel-plugin-transform-runtime](https://www.babeljs.cn/docs/plugins/transform-runtime) - 避免了重复打包代码和手动引入模块的痛苦
*   [babel-plugin-rawest](https://github.com/sokra/rawact) - React 的 DOM 直出方案
*   [babel-plugin-macros](https://github.com/kentcdodds/babel-plugin-macros) - 使环境变量的设置更加简单
*   [babel-plugin-dynamic-import-node](https://github.com/airbnb/babel-plugin-dynamic-import-node) - 有些场景下会需要禁用`import()`语法
*   [babel-plugin-react-require](https://github.com/vslinko/babel-plugin-react-require) - 自动为 jsx 语法加 react 引用
*   [babel-plugin-transform-react-remove-prop-types](https://github.com/oliviertassinari/babel-plugin-transform-react-remove-prop-types) - 删除 prop-types，生产环境用
*   [babel-polyfill](https://babeljs.io/docs/en/babel-polyfill) - 通过改变全局来兼容 es2015 所有方法
*   [babel-preset-env](https://babeljs.io/docs/en/babel-preset-env) - 根据你支持的环境自动决定适合你的 Babel 插件的 Babel preset

## 测试

*   [Mocha](https://github.com/mochajs/mocha) - 能够运行在Node和浏览器中的多功能的JavaScript测试框架，它让异步测试简单且有趣
*   [jest](https://github.com/facebook/jest) - facebook出品的JavaScript单元测试软件
*   [ts-jest](https://github.com/kulshekhar/ts-jest) - 对原生TypeScript 项目进行UI测试
*   [enzyme](https://github.com/airbnb/enzyme) - Airbnb开源的 React 测试类库
*   [jsdom](https://github.com/jsdom/jsdom) - 纯粹由javascript 实现的一系列web标准，用于在nodejs 中使用
*   [puppeteer](https://github.com/GoogleChrome/puppeteer) - Google Chrome 团队官方的无界面Chrome 工具
*   [react-test-renderer](https://github.com/facebook/react/tree/master/packages/react-test-renderer) - 测试渲染
*   [react-testing-library](https://github.com/kentcdodds/react-testing-library) - 测试实用程序

## 框架

*   [vue](https://cn.vuejs.org) - 渐进式 JavaScript 框架
*   [nuxt.js](https://zh.nuxtjs.org) - 基于Vue.js 的轻量级应用框架，可用来创建服务端渲染(SSR) 应用，也可充当静态站点引擎生成静态站点应用
*   [react](https://react.docschina.org) - 用于构建用户界面的 JavaScript 库
*   [next.js](https://github.com/zeit/next.js) - 构建React服务端渲染应用
*   [gastby](https://github.com/gatsbyjs/gatsby) - 静态站点生成器
*   [umi](https://umijs.org/zh) - 🌋 可插拔的企业级 react 应用框架
*   [taro](https://nervjs.github.io/taro) - 多端统一开发框架，支持用React 的开发方式编写一次代码，生成能运行在微信小程序、H5、React Native 等的应用

## vue 相关库

*   [Vue CLI](https://cli.vuejs.org/zh) - Vue.js 开发的标准工具
*   [Vue Loader](https://vue-loader.vuejs.org/zh/) - 是一个 webpack 的 loader，它允许你以一种名为单文件组件 (SFCs)的格式撰写 Vue 组件
*   [Vue Router](https://router.vuejs.org/zh) - 官方的路由管理器
*   [Vuex](https://vuex.vuejs.org/zh) - 状态管理
*   [vue-devtools](https://github.com/vuejs/vue-devtools) - Vue调试神器
*   [element-ui](http://element-cn.eleme.io/#/zh-CN) - 基于Vue 2.0 的组件库
*   [iview](https://www.iviewui.com) - UI组件库

## react 相关库

*   [create-react-app](https://github.com/facebook/create-react-app) - 业界最优秀的 React 应用开发工具之一
*   [react-router](http://react-guide.github.io/react-router-cn/) - React 路由解决方案
*   [Ant Design](https://ant.design/index-cn) - 蚂蚁金服的 React UI 库
*   [material-ui](https://www.mdui.org/design/) - UI 库
*   [react-intl](https://github.com/yahoo/react-intl) - React 国际化多语言
*   [react-dnd](https://github.com/react-dnd/react-dnd) - 拖拽实现
*   [react-helmet](https://github.com/nfl/react-helmet) - 修改 html 的 header 内容

## 工具类

*   [lodash](https://www.lodashjs.com) - 实用工具库
*   [moment](http://momentjs.cn) - 日期处理类库
*   [dayjs](https://github.com/iamkun/dayjs) - Moment.js轻量化方案，拥有同样强大的API
*   [fastclick](https://github.com/ftlabs/fastclick) - 解决移动端click事件300ms延迟
*   [lib-flexible](https://github.com/amfe/lib-flexible) - 可伸缩布局方案

## 命令行

*   [shelljs](https://github.com/shelljs/shelljs) - 重新包装了 child_process，调用系统命令更加方便
*   [yargs](https://github.com/yargs/yargs) - 命令行解析器
*   [chalk](https://github.com/chalk/chalk) - 终端字符串美化
*   [cheerio](https://github.com/cheeriojs/cheerio) - 用类似jQuery语法操作Dom结构
*   [chokidar](https://github.com/paulmillr/chokidar) - 监听文件夹改变
*   [clipboardy](https://github.com/sindresorhus/clipboardy) - 复制到Node.js中的剪贴板
*   [debug](https://github.com/visionmedia/debug) - 打印调试
*   [deprecate](https://github.com/brianc/node-deprecate) - 给过期警告
*   [glob](https://github.com/isaacs/node-glob) - 路径模式匹配
*   [tiny-glob](https://github.com/terkelg/tiny-glob) - 一个超级微小和更快〜350％ 的node-glob替代品
*   [signale](https://github.com/klaussinani/signale) - 漂亮的日志打印
*   [semver](https://github.com/npm/node-semver) - 处理版本相关的工作
*   [update-notifier](https://github.com/yeoman/update-notifier) - 更新提醒
*   [rimraf](https://github.com/isaacs/rimraf) - 删除文件和文件夹
*   [depd](https://github.com/dougwilson/nodejs-depd) - 标记出模块已经废弃的方法或者属性，方便模块更新并且不影响用户使用
*   [execa](https://github.com/sindresorhus/execa) - 可以调用shell和本地外部程序的javascript封装
*   [ora](https://github.com/sindresorhus/ora) - 要用来实现 node.js 命令行环境的loading效果，和显示各种状态的图标等
*   [inquirer](https://github.com/SBoudrias/Inquirer.js) - 试图为NodeJs做一个可嵌入式的美观的命令行界面

## 请求处理

*   [whatwg-fetch](https://github.com/whatwg/fetch) - XMLHttpRequest的最新替代技术
*   [got](https://github.com/sindresorhus/got) - 简化了的HTTP请求，比内置的http模块有更好的接口
*   [axios](https://github.com/axios/axios) - 一个基于promise 的HTTP 库，可以用在浏览器和node.js 中
*   [request](https://github.com/request/request) - nodejs request模块
*   [reqwest](https://github.com/ded/reqwest) - 浏览器异步HTTP请求

## 语言

*   [TypeScript](https://www.tslang.cn/docs/home.html) - 静态类型检查，微软开发
*   [FLOW](https://flow.org) - facebook 出品的JavaScript 静态类型检查工具，Vue.js 源码使用
*   [GraphQL](https://graphql.cn) - 一种用于 API 的查询语言
