---
title: autoprefixer in webstorm
date: 2016-11-16 18:09:59
tags:
- autoprefixer
- webstorm
- css3浏览器前缀
---

## 如何在webstorm下使用autoprefixer

小白晚上好，又到了该整理的时间惹~~

### 需求分析
> 虽然内置了css3自动补全功能，当输入`user-select`时，webstorm会自动补全，但是很多情况下这种自动补全并不令人满意，比如，当输入`display:flex;`时，webstorm就不会自动补全。而`Autoprefixer`是一个后处理器(Postprocessor)，它是在CSS代码产生之后才进行后续处理。不像`Sass,Less,Stylus`之类的预处理器(Preprocessor)，它适用于普通的CSS，可以实现CSS3代码自动补全，也可以跟`Sass,Less,Stylus`集成，在CSS编译前或编译后运行。当`Autoprefixer`添加前缀到你的CSS，还不会忘记修复语法差异，这种方式，CSS是基于最新的W3C规范产生；

### 安装&配置

1.	安装 [nodeJS](https://nodejs.org/en/)，可用`node -v`查看是否已经安装。
2.	使用命令`npm install autoprefixer -g`安装Autoprefixer。
3.	使用命令`npm install postcss-cli -g`安装postcss-cli。
4.	启动webstorm，File -> Settings -> Tools -> External Tools -> add
5.	设置快捷键File -> Settings -> Keymap，搜索External Tools,配置autoprefixer,不与其他快捷键冲突即可，我的配置是（Ctrl + Shift + Alt + Space）。
6.	配置如下:
```
	Name: autoprefixer
    /*你所安装的postcss-cli的PATH，由于我的window不能识别autoprefixer,故改用postcss.cmd*/
    Program: C:\Users\Administrator\AppData\Roaming\npm\postcss.cmd
    Parameters: -u autoprefixer -o $FileDir$/$FileName$  $FileDir$/$FileName$
    Working directory: $ProjectFileDir$
```

<!--more-->

## 小白的额外收获

本小白在[w3cplus.com](http://www.w3cplus.com/css3/autoprefixer-css-vender-prefixes.html)中了解了，可使用自动化工具实现Autoprefixer功能，像`Grunt`或者是`Gulp`,安装方法雷同，待本小白研究后再更本文。

---

### 传说中的-prefix-free

其实也是解决手工书写浏览器前缀的一个方案，由[Lea Verou]()提供的一个[-prefix-free](http://leaverou.github.io/prefixfree/)脚本。只需在`.html`中（建议在样式文件之后）添加`-prefix-free.js`文件。当然，弊端也是显而易见的啦。添加这个脚本之后，使用CSS3的属性时，只需书写标准样式即可。但是这种做法将所有压力交给了客户端来处理。如此一来页面解析压力就大了，性能会打一定的折扣，并且一旦脚本加载失败，那么就会出现浏览器无法正常渲染CSS3的样式风格。其次，prefixfree脚本仅在IE9+、Opera10+、Firefox3.5+、Safari4+得到支持。

### 编辑器插件Autoprefixer,撞名了~

1.	与webstorm类似，在编辑器中安装Autoprefixer插件，首先需要你的环境中已经安装好了Node.js。
2.	开启你的Sublime Text编辑器，你可以同时按下`command + Shift + p`三个键，选择`Install Package`。然后搜索`Autoprefixer`。
3.	现在就可以随心所欲写样式啦，按下`command + Shift + p`三个键，选择`Autoprefix CSS`，就可以补充需要带前缀的style。



