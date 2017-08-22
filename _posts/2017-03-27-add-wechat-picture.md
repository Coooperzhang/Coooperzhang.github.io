---
layout: post
title:  "添加微信二维码"
date:   2017-03-27 14:44:54
categories: 前端技术

---

* content
{:toc}


想在模板的基础上添加自己的微信二维码，只需在header.html文件中添加如下代码：

	<div>
		<p >
			<img src="/css/pics/wechat.jpg" alt="We Chat" style="float:left;position:fixed; left:5px; top:180px;" width="150" height="150">
		</p>
	</div>
	
**调整`position`对象属性可以调整图片的显示效果：**

值 | 描述
---|---
absolute | 生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
fixed | 生成绝对定位的元素，相对于浏览器窗口进行定位。 元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
relative | 生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。
static | 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。
inherit | 规定应该从父元素继承 position 属性的值。




