# 关于GodKing

这是一个采用Go+Vue3+Socks5+K8s实现的前后端分离式并基于虚拟化容器技术实现的网络安全攻防演练平台。

工程体量较大，且仅由我一人独立实现，对于容器的回收机制仍然存在一些稳定性问题。

大体分为以下3个部分：

1.awd后端

负责响应所有前端发起的请求处理，以及对虚拟化容器进行定时化管理操作。

2.awd-vue前端

提供友好的UI给予用户。

3.awd-vue-admin后端

提供简易的后台给予管理员。



# 目前平台的特色

前沿技术语言（go+Vue3）

拥有队伍创建与加入队伍功能

允许预约比赛

允许比赛非公开设为邀请制

允许自定义flag格式与flag路径

比赛容器网络隔离制，只允许一场比赛的内容相互访问，保证安全性与稳定性

# 安装

强烈建立在一台init的Ubuntu machine上进行部署，避免影响到其他业务进行。

平台提供自动化与手动安装，当自动化安装脚本无法完成时请根据目录下的GodKingDoc/docs文件夹内的md文档进行手动配置与安装。

自动化安装请直接执行

```
sudo ./init.sh
```

执行完成后安如下步骤启动

1.进入awd目录执行

```
sudo ./awd
```

2.进入awd-vue目录执行

```
sudo npm run dev
```

3.进入awd-vue-admin目录执行

```
sudo npm run dev
```

Tips:可以配合screen进行进程后台悬挂保证前后端持续化运行，脱离终端。

# 使用教程

访问80端口，访问主页面

![](https://github.com/user-attachments/assets/39901f9c-f583-4c0c-8bb2-e8bc68d6c93e)

点击上方登录/注册进行登录/注册

登录

![image](https://github.com/user-attachments/assets/de00de0c-10cd-4650-93b5-f6c434cf18ae)

注册

验证码为可选功能，取决于部署者在部署时是否开启并配置相关SMTP参数。

![image](https://github.com/user-attachments/assets/22b603f9-e54a-43c8-8fee-7aabefc01b73)

个人中心

查阅简单信息与密码修改

![image](https://github.com/user-attachments/assets/e8c88968-c1cf-4aba-a772-78fa3209d78e)

![image-20241227214240469](C:\Users\LEGION\AppData\Roaming\Typora\typora-user-images\image-20241227214240469.png)

创建队伍

输入队伍名称创建，不可重复队伍名。

![](https://github.com/user-attachments/assets/547f6eb2-9ca8-4ea8-af02-371722e28dd6)

加入队伍

可由队内人员提供token，输入后可加入到对应队伍。

![image](https://github.com/user-attachments/assets/50f5a544-6889-419b-837e-bbb703c6de6e)

队伍界面

队长可以剔除队员，队员可以主动退出，但队长不能解散队伍。

![image](https://github.com/user-attachments/assets/d5d6e3b4-36ef-4f66-a022-5244576dfbd9)

![image](https://github.com/user-attachments/assets/4e9030bc-1d4d-4873-8b5c-48c7678426d3)

赛事创建

高度自定义，提供题目容器选择，自定义flag格式与路径，自定义时间，自定义是否开放比赛。

![image](https://github.com/user-attachments/assets/4daf3de4-6f20-4046-998c-650589d27b79)

赛事中心

可以进行报名

![image](https://github.com/user-attachments/assets/5fbb8f98-bfa7-4b92-b5bb-1ba69a32a318)

![image](https://github.com/user-attachments/assets/eb96ef3d-d9a5-490e-9596-ddf6c01f2915)

赛事管理中心

显示队伍已经报名的队伍，可以按时参赛

![image-20241227214506086](C:\Users\LEGION\AppData\Roaming\Typora\typora-user-images\image-20241227214506086.png)

赛事界面

提供详细赛事信息和规则

参赛队伍可以通过使用socks5代理工具例如Proxifier进行代理访问内网容器，并进行加固防御以及对其他队伍进行攻击。

同时，当本队伍被攻击至无法访问的情况，也就是沦陷。可以点击重置通过付出分数换取新环境的机会。

![image](https://github.com/user-attachments/assets/5c8d6d00-ed45-41e6-b422-80406e13cf7f)

后台管理

请部署者在部署完成后第一时间访问8080端口进行管理员的配置，配置后进入如下登录页面。

![image](https://github.com/user-attachments/assets/e01b2255-6c13-4e96-a438-b6c879919a87)

核心管理功能-题目导入

镜像名称格式如：pwn:latest

需要完整的镜像名称与版本，同时需要提前导入到minikube内部。

![image-20241227215040317](C:\Users\LEGION\AppData\Roaming\Typora\typora-user-images\image-20241227215040317.png)

Tips：pods管理暂时没有实现
