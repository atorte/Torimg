# Lsky-pro蓝空图床付费版部署教程

在部署的时候踩了很多坑，重新装了几次还没有搞好，还好有作者直接远程控制解决问题，现在项目已经正常运行，项目地址:[洋葱图床](https://www.torimg.top/)现在新项目开工，限时领8折优惠码：N3FMPG，先到先得，2025年7月28上午9点到期。项目图片访问链接使用国内CDN加速，延迟1~10ms。

简单介绍一下蓝空图床

> 兰空图床（Lsky Pro）是一款基于PHP和MySQL开发的开源图床程序，主要用于图片的上传、管理和分享。它支持多种存储方式，包括本地存储和第三方云存储（如阿里云OSS、腾讯云COS、七牛云等），适合个人博客、技术社区或作为云相册使用。

蓝空图床的官方网站：[兰空图床 - 您的图片存储与管理解决方案](https://www.lsky.pro/)

## 注册蓝空图床

我们要部署蓝空图床付费版本，就要现有产品授权。我们进入官网。[![71](https://pic.itxiaohui.top/20250720/cbcdd202a00f2e92f27922c4bb1ebbbf.png)](https://pic.itxiaohui.top/20250720/cbcdd202a00f2e92f27922c4bb1ebbbf.png)

进入授权中心，现在购买授权官方还送一年onenav可以使用，非常划算了

[![进入授权中心](https://pic.itxiaohui.top/20250720/bd5ad3470733fd9827654e2e772c594b.png)](https://pic.itxiaohui.top/20250720/bd5ad3470733fd9827654e2e772c594b.png)

注册并登录，注册时可以使用邀请码：XQD7AM5M 有购物优惠

[![注册界面](https://pic.itxiaohui.top/20250720/6ee1159ceeecee255ebb0e7015f80333.png)](https://pic.itxiaohui.top/20250720/6ee1159ceeecee255ebb0e7015f80333.png)

[![76](https://pic.itxiaohui.top/20250720/ac3b6ab0c0dd5b7985f82920fc594962.png)](https://pic.itxiaohui.top/20250720/ac3b6ab0c0dd5b7985f82920fc594962.png)



## 购买授权

创好了后，点击产品中心，购买授权

[![77](https://pic.itxiaohui.top/20250720/be1ae999feaab775de13b773e4f7c2e3.png)](https://pic.itxiaohui.top/20250720/be1ae999feaab775de13b773e4f7c2e3.png)

注意请仔细阅读购买须知

[![78](https://pic.itxiaohui.top/20250720/a9c1e1cb68120ccc0013035fbe18ab4b.png)](https://pic.itxiaohui.top/20250720/a9c1e1cb68120ccc0013035fbe18ab4b.png)

购买后会得到授权密钥复制备用，点击进入管理

[![80](https://pic.itxiaohui.top/20250720/d3b846b9ae8158a405b7b6c157c4e244.png)](https://pic.itxiaohui.top/20250720/d3b846b9ae8158a405b7b6c157c4e244.png)

添加你的域名后，进入更新管理

[![81](https://pic.itxiaohui.top/20250720/d74a3203635f5f7a7db22a35e00547f5.png)](https://pic.itxiaohui.top/20250720/d74a3203635f5f7a7db22a35e00547f5.png)

软件代码下载后备用。

## 准备服务器

### 购买服务器

服务器推荐雨云，现在雨云推出了5折优惠，优惠码：torimg

点击[链接](https://www.rainyun.com/torimg_)直达

点击后进入云服务器
[rainyun-www](https://pic.itxiaohui.top/20250721/9caa9205aa6054bad5d56038c3e88ba7.png)
推荐使用香港2h4g的配置，有备案也可以选择国内

[](https://pic.itxiaohui.top/20250721/9caa9205aa6054bad5d56038c3e88ba7.png)

[](https://pic.itxiaohui.top/20250721/23beb19e567b90428696babcc6ed79a1.png)

标价是48/月，领取5折优惠券后就是48*0.5=24元。

### 配置DNS解析（无CDN）

趁着服务正在创建，可以去域名提供商配置dns解析

一些常见IDC的教程：[腾讯云DNS](https://cloud.tencent.com/document/product/302/3446)，[阿里云DNS](https://help.aliyun.com/zh/dns/novice-guide-dns)。

我使用的是spaceship，以spaceship为例

进入[spaceship官网](https://www.spaceship.com/)

![微信截图_20250721100220](https://pic.itxiaohui.top/20250721/2cae7540b9d763d9e9dda1cc6de43ac7.png)

登录后，点击

![spaceship-lanuchpad](https://pic.itxiaohui.top/20250721/b2219f9e5d3e4cf3554f12149ed9fcdd.png)

点击高级DNS![微信截图_20250721100744](https://pic.itxiaohui.top/20250721/a09b5170c2ef226d0859e6a748ea30bd.png)

选择你的域名，点击进入

![微信截图_20250721101433](https://pic.itxiaohui.top/20250721/575e101d7e01ac23404ce6d6a6275e8b.png)

进入DNS解析界面，设置记录

![微信截图_20250721101659](https://pic.itxiaohui.top/20250721/87f5fe0ee0fb2f4feb2dded61b7c1b49.png)

这个时候服务器配置应该好了，我们返回到雨云，查看IP

![微信截图_20250721102508](https://pic.itxiaohui.top/20250721/d702ff2700a1dff02d1b547699493864.png)

进入控制台复制IP地址，和密码备用

![微信截图_20250721102752](https://pic.itxiaohui.top/20250721/bd36e76ad1aeeb238cf81ceab48e3cdb.png)

将复制的IP填入DNS记录，类型选择A记录。如果有ipv6可以使用AAAA记录。

![微信截图_20250721103106](https://pic.itxiaohui.top/20250721/105ff1bb541ad467c902548800b02bee.png)

文章后面会有CDN配置教程，继续往后看。



### 链接ssh

选择ssh软件，我使用Aterminal进行链接，也可以使用其他工具。或者使用powershell链接。

[Aterminal下载](https://aterminal.net/download)

![微信截图_20250721103815](https://pic.itxiaohui.top/20250721/4380489efaf617609525eeb2e37f1ad7.png)

ssh链接的基本格式:

ssh 用户名@IP，用户名一般为root

![微信截图_20250721104102](https://pic.itxiaohui.top/20250721/5221beb3171970a26bfc5efff40fe5e4.png)



![微信截图_20250721104251](https://pic.itxiaohui.top/20250721/330fef22177f03a8da0867be2aeea03e.png)

添加成功后可以下一步

## 环境部署

### 宝塔面板安装9.6

```shell
if [ -f /usr/bin/curl ];then curl -sSO https://download.bt.cn/install/install_panel.sh;else wget -O install_panel.sh https://download.bt.cn/install/install_panel.sh;fi;bash install_panel.sh ed8484bec
```

安装之后进入宝塔面板

先安装环境，蓝空图床需要下面的基本环境

### PHP 安装

> - PHP版本=8.2
> - cURL PHP 扩展
> - DOM PHP 扩展
> - Fileinfo PHP 扩展
> - Filter PHP 扩展
> - Hash PHP 扩展
> - Mbstring PHP 扩展
> - OpenSSL PHP 扩展
> - PCRE PHP 扩展
> - PDO PHP 扩展
> - Session PHP 扩展
> - Tokenizer PHP 扩展
> - XML PHP 扩展
> - Imagick PHP 拓展
> - Pcntl PHP 拓展
> - Zip PHP 拓展

你不要看到这么多，实际上大部分安装PHP的时候就配置好了

进入软件商店

![微信截图_20250721152230](https://pic.itxiaohui.top/20250721/2816e9cd9305aa6fcf70f1e15df943fc.png)

选择下列软件

![微信图片编辑_20250721152902](https://pic.itxiaohui.top/20250721/d5876ef07010b3b23f2e39fd44b45722.jpg)

一定要注意软件版本！！！

PHP 8.2.

![微信截图_20250721153104](https://pic.itxiaohui.top/20250721/e8389410d7c0ee9ae8d34d6009d814c9.png)

Redis 7.0.11

![微信截图_20250721153238](https://pic.itxiaohui.top/20250721/bce3b6c242f3e4532c1dd01a2295bd72.png)

MySQL 5.7.44

![微信截图_20250721153425](https://pic.itxiaohui.top/20250721/29281d2c84ebc36241c946f5a0a876f0.png)

注：除MySQL外，还支持下面的数据库，推荐MySQL安装。



![微信截图_20250721153733](https://pic.itxiaohui.top/20250721/e554b8f3a35cf3154581ee99c7a7517f.png)

Nginx 1.24~1.26即可

![微信截图_20250721153900](https://pic.itxiaohui.top/20250721/6dc37028d6b6f86d48b82d48a17c6442.png)

phpMyAdmin 5.2 如果你想要多个管理员的话，需要这个软件。

<img src="https://pic.itxiaohui.top/20250721/308f2c0254310acc72ee02dfbaea5b30.png" alt="微信截图_20250721154138" />

### PHP 配置及函数

安装下面的扩展

![微信截图_20250721160225](https://pic.itxiaohui.top/20250721/136ae78c205b8bea4f0ecba52de8f1f7.png)

![微信截图_20250721160504](https://pic.itxiaohui.top/20250721/dab63861a182c64744a30f3939d0fd97.png)

下面进入配置文件，下拉到323行

![微信截图_20250721160751](https://pic.itxiaohui.top/20250721/36aa5308409d4f21bc3bee659dd0e423.png)

将下面的函数全部删除

> passthru,exec,system,putenv,chroot,chgrp,chown,shell_exec,popen,proc_open,pcntl_exec,ini_alter,ini_restore,dl,openlog,syslog,readlink,symlink,popepassthru,pcntl_alarm,pcntl_fork,pcntl_waitpid,pcntl_wait,pcntl_wifexited,pcntl_wifstopped,pcntl_wifsignaled,pcntl_wifcontinued,pcntl_wexitstatus,pcntl_wtermsig,pcntl_wstopsig,pcntl_signal,pcntl_signal_dispatch,pcntl_get_last_error,pcntl_strerror,pcntl_sigprocmask,pcntl_sigwaitinfo,pcntl_sigtimedwait,pcntl_exec,pcntl_getpriority,pcntl_setpriority,imap_open,apache_setenv

很简单直接删除等号后的全部函数即可

![微信截图_20250721161200](https://pic.itxiaohui.top/20250721/ff6d87b882692af3961a4013f1a8e76f.png)

保存成功后，回到服务，重启一下

![微信截图_20250721161322](https://pic.itxiaohui.top/20250721/8df320d6542195edd6f24cc0d0503d61.png)

## 正式部署

### 创建站点

点击网站，PHP项目，添加站点

![微信截图_20250721161812](https://pic.itxiaohui.top/20250721/bfb11ad82cf94494bfda1957e95bdc72.png)

![微信截图_20250721162246](https://pic.itxiaohui.top/20250721/bab3c122834a211b9c7fd0807c510a90.png)

创建成功后进入站点目录

![微信截图_20250721162729](https://pic.itxiaohui.top/20250721/55d56029d131a7beb32b7dff6418ab94.png)

返回上一级，上传下载的源码

![微信截图_20250721162935](https://pic.itxiaohui.top/20250721/b61017bc7e5d8fb8284487f8c2c8713c.png)

上传后解压

![微信截图_20250721164407](https://pic.itxiaohui.top/20250721/83b1e88719732df8d72f832e790ac719.png)

![微信截图_20250721164809](https://pic.itxiaohui.top/20250721/88ed511b18db8369e67325e0f0ea194a.png)

创建伪静态，复制代码到文本框中

```nginx
location / {
    try_files $uri $uri/ /index.php?$query_string;
}

location ~ ^/livewire {
    expires off;
    try_files $uri $uri/ /index.php?$query_string;
}

location ~ .*\.(jpg|jpeg|webp|avif|bmp|gif|png|tif|tiff|jp2|j2k|jpf|jpm|jpg2|j2c|jpc|jpx|heic|heif)$ {
    try_files $uri $uri/ /index.php?$query_string;
}
```

![Snipaste_2025-07-21_20-05-12](https://pic.itxiaohui.top/20250721/2e8384d5224e8136abfcf9cbb85d00f0.png)

添加数据库

![screenshort](https://pic.itxiaohui.top/20250721/f29a0e844aa846b63bb48307375703f3.png)

![Snipaste_2025-07-21_19-28-31](https://pic.itxiaohui.top/20250721/d5f7d4a9534a6d5a6ee04b2f96489954.png)

### 使用安装脚本进行安装

下面我们进入ssh客户端,进入站点目录 cd /www/wwwroot/#你的网站目录

![Snipaste_2025-07-21_19-37-42](https://pic.itxiaohui.top/20250721/49e3997f1251cf46330b2c798afebddf.png)

给脚本添加可执行权限

```shell
chmod +x install.sh
```

然后执行脚本

```shell
./install.sh
```

![Snipaste_2025-07-21_19-46-58](https://pic.itxiaohui.top/20250721/ad1cc058480618f10e9bc916d9bef5c6.png)

![微信截图_20250721195329](https://pic.itxiaohui.top/20250721/d291cce6a07d65981887bc68f31d3a44.png)

安装这样配置即可，下面是添加MySQL连接信息,并配置管理员账户

![221](https://pic.itxiaohui.top/20250721/fe9b5f38130ecdde57eaaeeec5328c1e.png)

出现以下字样就部署成功了

![Snipaste_2025-07-21_20-12-09](https://pic.itxiaohui.top/20250721/0a59547deaf5144087b95d2628fc8d70.png)

**如果不是这个界面**，有红色字体报错，请检查SQL的用户名，密码是否正确。宝塔面板有时候会默认开启防火墙，没有3306端口，请放行。

### 配置消息队列

兰空图床在生成缩略图、图片处理以及发送邮件等等功能中，这些耗时任务都需要使用消息队列来执行，我们可以使用 `php artisan queue:work` 命令来运行消息队列

回到宝塔面板，进入软件商店，搜索**进程守护管理器**，点击安装

![](https://pic.itxiaohui.top/20250721/38c9f748ff4ef0b2a111253a34133a18.png)

点开软件

![](https://pic.itxiaohui.top/20250721/ffb94fa09da2da9316bd6365d9d7cc77.png)

名称：lsky

启动用户：默认即可

运行目录：你的网站目录

启动命令

```php
php artisan queue:work
```

进程数量：按照服务器配置和性能自行设置

最后点击确定即可

### 配置计划任务

兰空图床部分功能需要定时去运行处理，我们需要通过服务器的计划任务一分钟执行一次 `schedule:run` 命令来维持任务调度。有关计划任务的更多信息请[点击这里](https://www.runoob.com/w3cnote/linux-crontab-tasks.html)了解更多。

计划任务命令为

```shell
cd /www/wwwroot/app.com && php artisan schedule:run >> /dev/null 2>&1
```

![22axs](https://pic.itxiaohui.top/20250721/38c9f748ff4ef0b2a111253a34133a18.png)

进入计划任务页面，添加计划任务
![229asdqs](https://pic.itxiaohui.top/20250721/ffb94fa09da2da9316bd6365d9d7cc77.png)

需要注意，执行用户建议使用**www**

至此，部署完成。

## 洋葱图床

即刻上传，永久托管，博客作者的最爱
全球CDN加速访问 · 永不失效外链 · 隐私自动加密。注册即送2GB储存。
全新上线的图床服务：洋葱图床
站点链接：https://www.torimg.top/

1.图片cdn延迟低：采用阿里云国内cdn加速，延迟低至10ms

2.图片自动加密，保障隐私安全（不得上传违法，色情，恋童，恐怖主义等违法中华人民共和国法律的内容。被发现/举报，删除图片，多次提醒不听劝告的删除账号及所以图片。）

3.不怕ddos，cc攻击，使用腾讯云Edgeone进行站点加速，不限流量，不限访问次数。

4.无链接安全限制。图片在社交媒体均可打开，图片cdn链接域名已经经过企业备案，国内可以超快访问。
5.图片访问测速链接，勿刷流量
[](https://pic.itxiaohui.top/20250721/5582d0ceb2f417d07d51f01a5ea3c478.png)
6.支付宝微信接入，全链路SSL，保障交易安全。
7.超低价VIP月付仅需4.99元，季付也只要11.99元。
8.支持多平台用户端，无需浏览器。支持Windows，Mac，Linux系统，CPU架构：x86,arm等。注：Android平台客户端已在QQ群文件发布。

Q群号：996529694             全场八折优惠券:N3FMPG



