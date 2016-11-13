---
title: bottom element
date: 2016-11-10 17:17:30
tags:
- html元素
- 固定
- 底部
---

## 比较HTML元素固定在页面底部的几种做法

### 需求一

>例如：移动端商城的购车车中，需要把结算以及金额统计等元素放在页面底部，要求：（1）当页面内容不足一屏的时候，在屏幕可视区的底部出现；（2）当页面内容大于一屏，也就是有垂直滚动条时，在文档的最后显示。

#### 解决方式

1.	使用`position:absolute;`,定位为`bottom:0`。
2.	使用`position:relative`。
3.	使用`flex`属性实现。

#### 利弊解析

1.	`position:absolute`只能把元素定位到第一屏的底部，但不会随着滚动条的出现跑到文档最底部，满足需求(1)，不满足需求(2)。
2.	`position:relative`只能满足需求(2)，不能满足需求(1)，可以配合js实现。
3.	`flex`即可满足需求(1)，也可满足需求(2)，重点阐述。

#### 实例：使用flex属性实现元素位于页面底部

	//stylesheet
    .wOutSide{
        position: absolute;
        height: 100%;
        width: 100%;
        top:0;bottom: 0;left: 0;right: 0px
    }
    .wWrapper {
        min-height: 100%;
        width: 100%;
        position: relative;
        /**父元素display设置为flex**/
        display:flex;
        display:-webkit-flex;
        /**父元素的布局是垂直方向**/
        flex-direction: column;
        -webkit-flex-direction: column;
        align-items: center;
        -webkit-align-items: center;
    }
    .wInSide{
        width:100%;
        flex:1;
        -webkit-flex: 1;
    }
    //html结构为：
    <div class="wOutSide">
    	<div class="wWrapper">
        	<div class="wInSide"></div>
            <footer></footer>
        </div>
    </div>

#### 效果如下（先为不足一屏；再为超过一屏）
![betweenScreen](/img/betweenScreen.png)	![overScreen](/img/overScreen.png)

<!--more-->
### 需求二

>例如：移动端商城的购车车中，需要把结算以及金额统计等元素放在页面底部，要求：（1）当页面内容无论是不足一屏还是超过一屏，都在页面底部显示（该最底部不是文档的最后，而是可视区的底部）。

#### 解决方式（图略）
1.	使用`position:fixed`，定位为`bottom:0`;

#### 实例
	//stylesheet
    .wFooter{
        width:100%;
        height:1.86rem;
        padding:.3rem;
        position: fixed;
        bottom:0;
    }
    //html结构(为避免iPhone上滚动条问题，尽可能将footer写在body的直接子元素)
    <body>
    	<div></div>
    	<footer></footer>
    </body>




