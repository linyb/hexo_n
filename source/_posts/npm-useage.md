---
title: npm useage
date: 2016-11-03 22:51:32
tags:
- npm
- 用法
- nodejs
---

## npm 的用法

`npm install <package name> <--save(-S) || --save-dev(-D)> ` package name是可选的，没有的时候默认按照package.json的配置安装
`npm uninstall <package name>` 卸载包
`npm update <package name>` 更新包
`npm init <--yes>` 初始化node项目（其实就是创建package.json这个文件）


### 示例

1. `npm i nrm -g` 在全局安装nrm这个包.
2. `npm install` 在当前目录下查找`package.json` 这个文件， 如果没找到这个文件，则报错， 找到则根据它的依赖安装。

`npm install nrm -g --registry=https://registry.npm.taobao.org` --registry指定源，单次有效
`nrm use taobao` 使用淘宝源（加快国内下载速度）