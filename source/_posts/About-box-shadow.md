---
title: About box-shadow
date: 2016-11-21 11:57:58
tags:
- box-shadow
- scss
---

## box-shadow的那些事儿

### 一、语法

1.	`E {box-shadow:<length> <length> <length>? <length>? || <color>}`也就是`E {box-shadow:inset x-offset y-offset blur-radius spread-radius color}`等价于`对象选择器：{box-shadow：投影方式 X轴偏移量 Y轴偏移量 阴影模糊半径 阴影扩展半径 阴影颜色}`
2.	box-shadow 可以使用一个或多个投影，多个投影之间必须用逗号分隔开。
3.	阴影类型：默认是外阴影，如果取其唯一值`inset`即投的是内阴影。

### 二、效果

1.	单边效果
```
.border-shadow {
			@include box-shadow(-2px 0 0 green, 0 -2px 0 blue, 0 2px 0 red,2px 0 0 yellow)}
```
简单描述下，给对象四边设计阴影，我们是通过改变x-offset和y-offset的正负值来实现，其中x-offset为负值时，生成左边阴影，为正值时生成右边阴影，y-offset为正值是生成底部阴影，为负值时生成顶部阴影。设置模糊半径：
```
.multi-shadow{
		  @include box-shadow(-2px 0 5px green,0 -2px 5px blue,0 2px 5px red,2px 0 5px yellow);
}
```
在使用多层次的阴影时还需注意一个细节问题，如果前面的阴影模糊值小于后面的阴影模糊值，那么前面的显示在后面之上，如果前面阴影的模糊值大于后面的阴影模糊值，那么前面的阴影将遮住后面的阴影效果。如下面例子：
```
.multi-radius1-shadow {
		  @include box-shadow(0 0 15px green,0 0 25px red);
}
.multi-radius2-shadow {
		  @include box-shadow(0 0 25px green,0 0 15px red);
}
```
![box-shadow](/img/box-shadow/box-shadow-2.png)

2.	四边具有相同的阴影效果（只设置阴影模糊半径和阴影颜色）
```
.vague-shadow{
  		@include box-shadow(0 0 15px red);
}
```

3.	四边具有相同的阴影（只设置阴影扩展半径和阴影颜色）
```
.extend-shadow{
  		@include box-shadow(0 0 0 15px red);
}
```
该效果与border:15px solid red产生的效果相似，实则不同。阴影不会影响页面的任何布局，border的边框大小会被记在元素的宽高中，但阴影却不会。

4.	内阴影inset
```
.inset-shadow{
  		@include box-shadow(inset 0 0 15px red);
}
```

5.	测试结果
![box-shadow](/img/box-shadow/box-shadow-1.png)

6.	引用
[w3cplus.box-shadow](http://www.w3cplus.com/content/css3-box-shadow)

