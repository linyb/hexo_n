---
title: React Native 之IOS环境配置
date: 2017-12-02 10:01:32
tags:
- React Native
- IOS环境配置
- boost_1_63_0.tar.gz
---

## 搭建React Native的开发环境

### 我的相关版本

*	目标平台：iOS
*	开发平台：macOS Sierra 10.12.6
*	node: v8.5.0
*	react-native-cli: 0.50.3
*	npm:5.5.1
*	Xcode:9.1

### 安装

#### 必需的软件

*	Homebrew,Mac系统的包管理器
*	Node(4.0+)
*	React Native的命令行工具（react-native-cli）
*	Xcode(7.0+),可以通过App Store或者到[Apple开发者官网][1]

#### 推荐安装的工具
*	Watchman:`brew install watchman`

#### 测试安装
```
react-native init appProject
cd appProject
react-native run-ios
```

#### 安装障碍
1 执行react-native run-ios异常 ![react-native-ios-error](/img/react-native/react-native-ios.jpeg)
异常原因：
对于react-native版本高于0.45的创建项目，需要下载boost库，该库比较大，导致下载问题，参考[issues-1][2]和[issues-2][3]


[1]:https://developer.apple.com/xcode/downloads/
[2]:https://github.com/facebook/react-native/issues/14368
[3]:https://github.com/facebook/react-native/issues/14447

解决方案：

*	降低版本 `react-native init myApp --version 0.44.3`
*	替换资源文件,下载如下四个相关文件放到项目根目录下的 .rncache 目录`/用户/creamlin/.rncache/`下，进行替换：

		[glog-0.3.4](https://github.com/google/glog/archive/v0.3.4.tar.gz)
		[double-conversion-1.1.5](https://github.com/google/double-conversion/archive/v1.1.5.tar.gz)
		[boost_1_63_0](https://github.com/react-native-community/boost-for-react-native/releases/download/v1.63.0-0/boost_1_63_0.tar.gz)
		[folly-2016.09.26.00](https://github.com/facebook/folly/archive/v2016.09.26.00.tar.gz)

然后重新执行 react-native run-ios

#### 说明
以上四个包是`pro/node_modules/react-native/third-party`中所需的，之所以异常，因为缺少了这几个包


