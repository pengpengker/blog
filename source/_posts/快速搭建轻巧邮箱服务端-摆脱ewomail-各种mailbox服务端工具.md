---
title: 快速搭建轻巧邮箱服务端-摆脱ewomail-各种mailbox服务端工具
date: 2021-06-08 09:48:59
tags:
---

# 快速搭建轻巧邮箱服务端-摆脱ewomail-各种mailbox服务端工具



**开源免费的邮件服务端:[hMailServer](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fwww.hmailserver.com%2F)|[ewomail](https://ewomail.com) **

优点:功能强大，完善  imap pop smtp等齐全

缺点:占用资源较多，邮件处理缓慢，成本较高，批量或接收邮件需要先创建账号



为了仅只简单接收各种网站发来的邮件，或者想自己定义邮件处理方式的同时节省服务器成本，特此捣鼓一下。



---

##### mailin-小型邮件服务端库

[mailin](https://github.com/Flolagale/mailin)定义:小型的smtp服务器，监听电子邮件并解析内容



---

##### 1-使用nodejs方式调用mailin处理邮件(方式的总结和分析)

> 为了完成这一方法，您需要具备的技能：
>
> 1.nodejs+npm 基础知识

默认您已经具备nodejs+npm，并且已经将它安装完成

首先创建一个项目，或者一个nodejs文件。然后npm安装mailin

```nodejs
npm install mailin
```

您也可以加上-g命令将它全局安装。奥，默认您已经拥有nodejs基础，此处废话了

然后，您需要打开您的nodejs项目或nodejs文件，并写入已下为您提供的简单例子：

```nodejs
var mailin = require('mailin');
mailin.start({
  port: 25,
  disableWebhook: true // 这里没什么用，请关闭
});
mailin.on('message', function (connection, data, content) {
  console.log(data);
  /* 当mailin收到新邮件时会触发该函数，内容在data里，请下断点debugging */
});
```

一个简单的邮件服务端就完成了

现在，我们需要想办法调试它，我们需要知道data里的参数格式，和是否能接收到邮件。

您最好的方式是将程序放入服务器中，或您本身有公网ip

然后将域名添加MX解析记录：

@ MX 10 IP

如果您已经完成部署和域名解析，这是您应该使用vscode或其它方式远程断点on函数，当您发送一封您域名相关的邮箱信息时，断点应当被触发

> 总结:nodejs加载mailin库达到邮件的接收和处理
>
> 不需要提前操作邮箱账号等

不想写了。。。大家自己折腾吧

---

##### 2-使用mailin执行程序webhook转发(总结和分析)

> 为了完成这一方法，您需要具备的技能：
>
> 1.nodejs+npm 基础知识

默认您已经具备nodejs+npm，并且已经将它安装完成

首先全局安装mailin，(请加上-g 否则后期mailin无法使用)

```nodejs
sudo npm install -g mailin
```

然后将mailin程序运行起来，并指定webhook地址

```linux
sudo mailin --webhook http://mydomain.com/incoming_emails
```

域名解析相关请参考第一节

此时，如果当有新邮件发来，mailin会将它转发到http://mydomain.com/incoming_emails这个地址。格式请参考mailin文档。

懒了，不想哔哔了。

就酱，就是这么简单



至于大家说的自定义邮件失效时间，或者将邮件存起来，既然程序取到了内容，为什么不自己想想怎么处理呢？



拜了个拜
