[whoami代码论坛(码谈)](http://106.52.166.52)
===============
### 资料
[Spring 文档](https://spring.io/guides)    
[Spring Web](https://spring.io/guides/gs/serving-web-content/)  
[菜鸟教程](https://www.runoob.com/mysql/mysql-insert-query.html)    
[Thymeleaf](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#setting-attribute-values)    
[Spring Dev Tool](https://docs.spring.io/spring-boot/docs/2.0.0.RC1/reference/htmlsingle/#using-boot-devtools)  
[Spring MVC官网](https://docs.spring.io/spring/docs/5.0.3.RELEASE/spring-framework-reference/web.html#mvc-handlermapping-interceptor)  
 
#### BootStrap


#### 工具
[lombok的安装和使用](https://blog.csdn.net/motui/article/details/79012846)    
[Markdown 插件](http://editor.md.ipandao.com/)  
[REST API测试 Chrome插件](http://www.cnplugins.com/devtool/restlet-client-rest-api-t/)

码谈介绍(完善中...)
----------------------
#### 界面设计模块
1. 使用bootstrap设计简单的响应式页面
    + 下载bootstrap官方资源包
    + 引入项目所需资源
    + 根据官方文档使用相应的组件
    + [BootStrap](https://v3.bootcss.com/components/)     
    + [栅格系统](https://v3.bootcss.com/css/#grid)
#### 登录功能模块
[github官网](https://github.com/)     
[github OAuth](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/)
1. 用户点击登录按钮     
    使用github的登录授权，发送请求，请求调用authorize接口，需要提供的参数
    + client_id：github自动生成
    + redirect_uri：回调接口地址
    + state=1
    + scope=user
1. github自动跳转到设置的callback接口中，并携带参数code
1. 然后调用github提供的access_token接口，需要提供参数，将数据传的参数封装成AccessTokenDTO
    + client_id：github生成
    + client_secret：github生成
    + code: github回调返回的参数
    + redirect_uri：回调接口地址
    + state=1
1. 使用OkHttp所提供的类将请求设为post请求
    + https://github.com/login/oauth/access_token
    ``` java
   Request request = new Request.Builder()
                   .url("https://github.com/login/oauth/access_token")
                   .post(body)
                   .build(); 
   ```
1. 再次将返回的access_token使用get方式请求github提供的user接口
    + https://api.github.com/user?access_token=xxx
    ``` java
   Request request = new Request.Builder()
                   .url("https://api.github.com/user?access_token="+accessToken)
                   .build(); 
   ```
   注：该方法即将弃用，后续更新使用方法
1. 最后返回github用户参数，存入数据库，更新登录状态。
### 发布问题
1. 前提条件：已登录用户
### 首页分页展示
### ......


------------------------------------
##### 开发日志  
1. 2020/02/15 完成部署    
1. 2020/02/18 添加动态导航栏    
1. 2020/02/20 完善登录用户名为null的情况   
1. 2020/02/24 添加使用Redis实现点赞功能   
1. ......