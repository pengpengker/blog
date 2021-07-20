---
title: amazon验证码的识别与训练
date: 2021-07-20 15:38:46
tags:
---
### 训练验证码

> 暂时不太想花时间写教程，直接使用现成的框架就好了
>
> [快AI - 深度学习图像识别平台 (kuai-ai.com)](https://kuai-ai.com/)
>
> 流程:采集样本-标注-训练-模型部署
>
> 至于框架使用问题可以咨询客服，有时间也可以跟我交流



##### 无混淆jpg版本验证码-少见，常见于爬虫验证单页

![](C:\Users\pengp\Desktop\amazon_captcha\jpg_np_hx\1623274822.jpg)

```http
https://www.amazon.com/ap/captcha?appAction=SIGNIN_PWD_COLLECT&_=1623279741168
```

##### 混淆jpg验证码-常见，用于登录等常规无高风险验证

![混淆静态](C:\Users\pengp\Desktop\amazon_captcha\jpg_hx\162327977002629.jpg)

```html
https://www.amazon.com/ap/captcha?appAction=SIGNIN_PWD_COLLECT&captchaObfuscationLevel=ape%3AaGFyZA%3D%3D&captchaType=image&marketPlaceId=ATVPDKIKX0DER&_=1623279741168
```

##### 动态gif混淆验证码-常见，用于登录等常规高风险验证

```html
等待补充链接
```

##### 点选验证码-仅注册使用，用于注册防灌水新型验证码

```html
待补充
```





样本下载：https://1drv.ms/u/s!AoCPSvI44H0khh4l-QACElCmv84R?e=S7z9Lb

