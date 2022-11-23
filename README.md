### 人人开源renren-fast-vue项目

<br>

## renren-fast-vue

- renren-fast-vue基于vue、element-ui构建开发，实现[renren-fast]
  (https://gitee.com/renrenio/renren-fast)后台管理前端功能，提供一套更优的前端解决方案
- 前后端分离，通过token进行数据交互，可独立部署
- 主题定制，通过scss变量统一一站式定制
- 动态菜单，通过菜单管理统一管理访问路由
- 数据切换，通过mock配置对接口数据／mock模拟数据进行切换
- 发布时，可动态配置CDN静态资源／切换新旧版本

![输入图片说明](https://images.gitee.com/uploads/images/2019/0305/133529_ff15f192_63154.png "01.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0305/133537_7a1b2d85_63154.png "02.png")

### node.js版本

关于前端VUE的node-sass版本问题,如果你的是最新的node16版本
如果已经终端运行过npm install的话删除掉node_moduls文件
找到package-lock.json文件ctrl+F 查找sass
改掉node-sass的version版本号和resolved路径后的版本号
以及改掉sass-loader的version和resolved路径后的版本号
根据你的node版本去找对应的sass版本
我的是最新的16版本，那么node-sass改为6.0.1，sass-loader为7.0.3
终端执行删除当前依赖包命令：
`npm uninstall node-sass sass-loader`
下载对应版本命令：
`npm i node-sass@6.0.1 sass-loader@7.0.3`
重新
`npm install`
OK
`npm run dev`

chromedriver 报错 Only Mac 64 bits supported.
`npm install --ignore-scripts`

