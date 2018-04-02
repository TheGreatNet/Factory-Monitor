# Factory-Monitor
## 产品功能
![Function mind map](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/product_functions.png)

## 产品架构
![product framework](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/product_framework.png)

工厂模拟程序产生模拟数据，写入Mysql数据库.同时检测数据，若超过阈值，则向Django发送HTTP请求（途径Nginx），告知Django发送邮件给管理人士。

后端使用Django框架，加上Django Rest framework为前端提供API。收到用户修改阈值的请求后，通过socket告知Factory程序修改阈值（可使用HTTP协议或TCP协议）。

uwsgi为应用服务器，Nginx为反向代理服务器。

前端通过轮训的方式，以10秒一次的频率访问数据。

## 网站原型
#### 登录界面
![login](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/login.png)

**1.** 考虑到应用场景，本系统是由工厂员工内部使用，外人无法进入本系统，所以使用本系统需要提前在数据库中录入员工工号，员工注册时需填写自己工号。

#### 注册界面
![register](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/register.png)

**2.** 60s未收到验证码可重新发送邮件

#### 忘记密码
![changepassword](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/changepassword.png)

用户忘记密码后，验证邮箱，直接设置新密码（不管旧密码）。

#### 主页（数据总览）
![overview](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/overview.png)

**3.** 搜索仪器后，直接跳转到仪器详情页面

**4.** 注销后，返回登录界面

#### 仪器详情
![detail](https://raw.githubusercontent.com/TheGreatNet/Factory-Monitor/master/pic/detail.png)

**5.** 点开一个仪器就在侧边栏处产生一个标签，方面在不同仪器详情界面切换。点击“×”关闭


### 补充
用户信息界面和管理界面及其相应的功能暂时不管，先实现主要功能。产品原型给出了大概，前端可以按需自行修改。

功能上有什么建议可以联系我。

原型文件在prototype文件夹中。
