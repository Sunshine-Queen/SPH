1：vue-cli脚手架初始化项目
node + webpack +淘宝镜像

node_modules文件夹：项目依赖文件夹

public文件夹：一般放置一些静态资源（图片），需要注意，放在Public文件夹中的静态资源，webpack进行打包的时候，会原封不动打包到dist文件夹中。

src文件夹（程序员源代码文件夹）：

    assets文件夹：一般也是放置静态资源（一般放置多个组件共用的静态资源），需要注意，放置在assets文件夹里面静态资源，在webpack打包的时候，webpack会把静态资源当做一个模块，打包JS文件里面。

    components文件夹：一般放置的是非路由组件（全局组件）

    App.vue:唯一的跟组件，Vue当中的组件（.vue）

    main.js:程序入口文件，也是整个程序当中最先执行的文件

bable.config.js:配置文件（bable相关）

package.json文件: 认为是项目的身份证，记录项目叫做什么，项目当中有哪些依赖、项目怎么运行。

package-lock.json:缓存性文件

README.md:说明性文件

2：项目的其他配置

    2.1 项目运行起来的时候，让浏览器自动打开
    ---package.json
    "scripts": {
        "serve": "vue-cli-service serve --open",
        "build": "vue-cli-service build",
        "lint": "vue-cli-service lint"
    },

    2.2 eslint校验功能关闭
    ---在根目录下，创建一个vue.config.js文件
    比如：声明变量没有使用eslint会报错

    2.3 Src文件夹简写方法，配置别名。@代表的是src文件夹

    jsconfig.json配置别名@提示
    {
        "compilerOptions":{
            "baseUrl":"./",
            "paths":{
                "@/*":["src/*"]
            }
        },
        "exclude":["node_modules","dist"]
    }



3：项目路由
vue-router
前端所谓路由：KV键值对
key:URL(地址栏中的路径)
value:相应的路由组件
注意： 项目 上中下结构

    路由组件：
    Home首页路由组件、Search路由组件 、Login登录路由、Register注册路由

    非路由组件：
    Header【首页，搜索页有】等都有
    Footer【首页、搜索页有】，但是在登录，注册页面没有

4：完成非路由组件Header与Footer业务
    在项目中，不以HTML+CSS为主，主要高业务，逻辑
    正在开发项目的时候：
    １：书写静态页面（HTML+CSS）
    2： 拆分组件
    3：获取服务器的数据动态展示
    4：完成相应的动态业务逻辑

    注意1：创建组件的时候，组件结构 + 组件的样式 + 图片资源

    注意2： 咱们项目采用的是less样式，浏览器不识别less样式，需要通过less、less-loader【5版本】进行处理less，把less样式变为css样式，浏览器才可以识别。

    注意3：如果想让组件识别less样式，需要在style标签身上加上lang=less

    4.1使用组件的步骤（非路由组件）
    -创建或者定义
    -引入
    -注册
    -使用

5：路由组件的搭建
vue-router
在上面分析的时候，路由组件应该有四个：Home、Search、Login、Register
-components文件夹：经常放置的非路由组件（共用全局组件）
-pages|views文件夹：经常放置路由组件

    5.1配置路由
    项目当中配置的路由一般放置在router文件夹中
