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

    5.2总结
    路由组件与非路由组件的区别？
    1：路由组件一般放置在pages|views 文件夹，非路由组件一般放置在components文件夹中
    2：路由组件一般需要在router文件夹进行注册（使用的即为组件的名字），非路由组件在使用到的时候，一般都是以标签的形式使用
    3：注册完路由，不管是路由组件、还是非路由组件身上都有$route,$router属性

    $route：一般获取路由信息【路径、确认样、params等等】
    $router:一般进行编程式导航进行路由跳转【push|replace】

    5.3路由的跳转
    路由的跳转有两种形式：
    声明式导航route-link，可以进行路由到的跳转
    编程式导航push|replace，可以进行路由跳转

    编程式导航：声明式导航能做的，编程式导航都能做
    编程式导航除了可以进行路由跳转，还可以做一些其他的业务逻辑


6：Footer组件的显示和隐藏
显示或隐藏组件：v-if|v-show
Footer组件：在Home、Search显示Footer组件
Footer组件：在登录、注册时候隐藏

    6.1我们可以根据组件身上的$route获取当前路由的信息，通过路由路径判断Footer显示与隐藏
    6.2配置路由的时候，可以给路由添加路由元信息【meta】,它的key不能瞎写、乱写、胡写

8：路由传参

    8.1路由跳转有几种方式？
    比如：A-》B
    声明式导航：router-link（务必要有to属性），可以实现路由的跳转
    编程式导航：利用的是组件实例的$router.push|replace方法，可以实现路由的跳转。（可以书写一些自己的业务）

    8.2路由传参，参数有几种写法？
    params参数：属于路径当中的一部分，需要注意的是，在配置路由的时候，需要占位
    query参数：不属于路径当中的一部分，类似于ajax中的queryString /home?k=v$kv= ,不需要占位

注意几点：
（1）路由传递参数（对象写法）path是否可以结合params参数一起使用？
答：路由跳转传参的时候，对象的写法可以是name、path形式，但是需要注意的是，path这种写方法不能与params参数一起使用。
（2）如果指定paraams参数可传不可传？
