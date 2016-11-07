---
title: installation of SASS
date: 2016-11-07 14:33:45
tags: sass
---

## 基于windows系统的SASS安装

#### 安装步骤

1.	首先要安装ruby，[Ruby Installer](http://rubyinstaller.org/)
2.	打开终端`cmd`，执行`gem install sass`
3.	查看是否安装成功`sass -v`

#### 安装过程遇到的情况

1.	执行命令`gem install sass` 报错如下：                                                       ![install error](/img/sass_error_1.png)
2.	1是由于路径被强掉，可用淘宝镜像一试`gem sources -a http://ruby.taobao.org`，结果报错如下：![sass_taobao_fail](/img/sass_tb_fail.png)
3.	于是改用腾讯云`gem sources -a http://gems.ruby-china.org/`代替，完美！![install success](/img/sass_sussess.png)
4.	执行命令`sass -v` 测试是否安装成功,完美！                                                     ![sass_v](/img/sass_v.png)


<!--more-->
[RubyGems](http://gems.ruby-china.org/)一直以来在国内都非常难访问到，在本地你或许可以翻墙，当你要发布上线的时候，你就很难搞了！这是一个完整 [RubyGems](http://gems.ruby-china.org/) 镜像，你可以用此代替官方版本，我们是基于国内 CDN + 国外服务器的方式，能确保几乎无延迟的同步。



