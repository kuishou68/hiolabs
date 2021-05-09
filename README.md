## 很润，很丝滑，搭建一款开源的微信商城小程序：海风小店 

**准备工作**

- 申请小程序账号

申请小程序账号只需要按照官网文档说明操作即可，这里我就不展开说了，地址：https://developers.weixin.qq.com/miniprogram/introduction/

- 官网下载GitHub三个文件 

  服务端： https://github.com/iamdarcy/hioshop-server  
  微信小程序：https://github.com/iamdarcy/hioshop-miniprogram

  管理端：GitHub: https://github.com/iamdarcy/hioshop-admin

![image-20210509222627644](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509222627644.png)

- 安装顺序：  

  服务端  ==>  小程序  ==>  管理端    

  server  ==>  miniprogram  ==>  admin



**服务端 ：本地开发环境配置**

- 创建数据库hiolabsDB（注意数据库字符编码为utf8mb4），并导入项目根目录下的hioshop.sql  

  注意数据库版本一定要是 **MySql 5.7**  一定要是 **MySql 5.7**   一定要是 **MySql 5.7**

![image-20210509223741438](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509223741438.png)

- 更改数据库配置  src/common/config/database.js

![image-20210509224232810](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509224232810.png)

- 填写微信配置和其他设置，打开 src/common/config/config.js文件，如果微信支付、oss服务什么的你都还没申请，都可以先不填写，但是微信的appid 和secret 是必填的。

  ![image-20210509231024786](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509231024786.png)

- 微信的appid 和secret 在微信小程序官网登录以后，在控制台页面的开发->开发设置->开发者ID中

  ![image-20210509231238114](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509231238114.png)

- 填写七牛云地址  src/common/config/config.js

  ![image-20210509224442923](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509224442923.png)

  

- 安装依赖``npm install``

- 启动  ``npm start``

  没报错的话，会在控制台显示200 

![image-20210509224618728](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509224618728.png)

​	浏览器测试   http://127.0.0.1:8360/  

![image-20210509224551447](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509224551447.png)

------------------------------------------------------------------------------------------------------------------

**小程序端 ：本地开发环境配置**

- 打开微信开发者工具

![image-20210509230236475](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509230236475.png)

- 默认API改成本地地址

  ![image-20210509224825777](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509224825777.png)

​	小程序预览显示数据表示数据库连接成功



--------------------------------

**服务端 ：本地开发环境配置**

- 安装依赖后启动后会出现一个问题，这个问题是Element-ui自带的。

<img width="600" src="http://git.hiolabs.com/github/error.jpg"/>

- 解决方法：在node_modules 搜索:  div class="el-form-item__label-wrap" 

![image-20210505000052259](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210505000052259.png)

- ​	在语句中加上单引号就可以了

<img width="600" src="http://git.hiolabs.com/github/before.jpg"/>

<img width="600" src="http://git.hiolabs.com/github/after.jpg"/>

- 启动 ``npm run dev``

![image-20210509225447399](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509225447399.png)

- build 打包成静态文件  ``npm run build:web``

- 此时代表项目启动成功，桌面上会出现下图这个程序界面，输入默认的管理员账号密码：

  用户名：hiolabs，密码：hiolabs

![image-20210509225845170](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210509225845170.png)



参考：https://mp.weixin.qq.com/s/2lDVMnUJqfenO6MkiL132Q

​		   https://blog.csdn.net/GZLEO77/article/details/108627277

​		   https://www.bilibili.com/video/av89567916