# 微人事管理系统

#### 项目介绍
SpringBoot+Vue前后端分离开发的后台管理系统  
本系统主要是针对企业端的人事管理，功能上有员工资料管理、人事管理、薪资管理、统计管理和系统管理，针对不同的用户角色有相应的权限来访问系统功能。

#### 开发环境
|工具 | 版本或描述|
|-----|----------|
|OS   | Windows11|
|JDK | 1.8+|
|IDE|IDEA/VS code|
|Maven|3.6.3|
|MySQL|5.6.4|
|node.js|10.24.1|
|npm|6.4.1|

#### 模块划分
|模块|功能|
|----|----|
|vhrserver|后台管理模块|
|mailserver|邮件发送服务|

#### 系统架构图
本项目前端表示层主要使用Vue.js和ElementUI。用Spring Security进行用户认证，Axio前后端通信，WebSocket实现用户实时通信，RabbitMQ消息队列，每新增一位员工就将信息提交到消息队列中。  
![架构图](https://gitee.com/tao0007/vhr1.0/raw/bba83d99fd756a4d6f7b1de4417720e26a08f484/imgs/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202023-05-26%20163938.png)  


#### 安装步骤

1.  使用IDEA导入本项目
2.  提前准备Redis、RabbitMQ、MySQL数据库
3.  创建空的vhr数据库
4.  根据实际情况修改以下两个配置文件相关信息
    1.  vhrserver/vhr-web/src/main/resources/application.yml
    2.  mailserver/src/main/resources/application.properties
5.  本地开启Redis和RabbitMQ服务，在IDEA运行VhrApplication和MailserverApplication
6.  浏览器访问：http://127.0.0.1/8081/index.html   
登录后台系统（*管理员账号：用户名：admin,密码:123*）
7.  如果想要二次开发可下载前端源码：https://gitee.com/tao0007/vhr-vue  
前端开发完毕后可执行`npm run build`  将生成的dist文件夹内容替换vhrserver/vhr-web/src/main/resources/static内的文件即可

#### 项目部署
1.  利用Maven工具对项目进行打包：mailserver-0.0.1-SNAPSHOT.jar和vhr-web-0.0.1-SNAPSHOT.jar
2.  也可将jar包上传至云服务器或虚拟机上运行命令  
例如 `nohup java -jar mailserver-0.0.1-SNAPSHOT.jar & mail.log`,即开启了邮件发送服务
3.  前端代码开发完成后通过`npm run build`生成dist文件夹，可选择将其部署到Nginx服务器上：
    1.  安装Nginx
    2.  配置Nginx，一般路径为/usr/local/nginx/conf,对nginx.conf进行配置上游服务器和访问静态资源直接过滤
    3.  进入安装的sbin目录下，启动Nginx：`./nginx`
    4.  重新加载Nginx配置文件：`./nginx -s reload`

#### 成果预览
系统首页
![首页](https://gitee.com/tao0007/vhr1.0/raw/master/imgs/t1.png)  
若无法显示图片请点击：https://gitee.com/tao0007/vhr1.0/raw/master/imgs/t1.png

用户管理  
![用户管理](https://gitee.com/tao0007/vhr1.0/raw/master/imgs/t2.png)
若无法显示图片请点击：https://gitee.com/tao0007/vhr1.0/raw/master/imgs/t2.png  

#### 系统体验
我已将项目部署到阿里云服务器上，浏览器访问：http://121.199.32.6/index.html#/

|用户名|密码|备注|
|----|----|-----|
|admin|123|系统管理员|
|libai|123|其他用户|  

备注：6月中旬后服务器到期，系统可能无法访问


