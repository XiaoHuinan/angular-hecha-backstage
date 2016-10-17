---
title: 让div水平垂直居中的几种方法
categories: css规范与技巧
date: 2013-06-03 14:22:08
---

最近，公司招了一批新人，吃饭的时候恰好碰到一个新同事，就跟他聊了起来。听他说了主管面试的时候出的一些问题，其中一个问题我印象特别深刻，因为，我当年进来的时候，也被问到这个问题。虽然这个问题已经问烂了，但是我还是有必要在这里总结一个这个问题。

利用 CSS 来实现对象的垂直居中有许多不同的方法，比较难的是选择那个正确的方法。

使用 CSS 实现水平居中很容易，但要实现垂直居中并不容易。而且有些方法在一些浏览器中无效。下面我们看一下使对象垂直集中的几种不同方法，以及它们各自的优缺点。

## 一：表格布局法 ##

这个方法把一些 div 的显示方式设置为表格，因此我们可以使用表格的 `vertical-align` 属性。

	<div id="wrapper">  
	    <div id="cell">
	        <div class="content">Content goes here</div>
	    </div>
	</div>  

	#wrapper {
	    display: table;
	}
	
	#cell {
	    display: table-cell;
	    vertical-align: middle;
	}

**优点：**

content 可以动态改变高度(不需在 CSS 中定义)。当 wrapper 里没有足够空间时， content 不会被截断

**缺点：**

Internet Explorer(甚至 IE8 beta)中无效，许多嵌套标签(其实没那么糟糕，另一个专题)

## 二：假借图片法 ##

这个方法把一些 div 的显示方式设置为inline-block，和图片一样，因此我们可以使用图片的 `vertical-align` 属性。

	<div id="wrapper">  
	    <div id="likeImg">
	        <div class="content">Content goes here</div>
	    </div>
	</div>  

	#wrapper {
	    display: table;
	}
	
	#likeImg {
	    display: inline-block;
	    vertical-align: center;
	}

**优点：**

在各种浏览器中兼容性都非常好，ie6和7中有间距问题

**缺点：**

很容易影响其他的布局，导致网页布局全部瘫痪

## 方法三：绝对定位法 ##

这个方法使用绝对定位的 div，把它的 top 设置为 50％，top margin 设置为负的 content 高度。这意味着对象必须在 CSS 中指定固定的高度。

因为有固定高度，或许你想给 content 指定 overflow:auto，这样如果 content 太多的话，就会出现滚动条，以免content 溢出。

	<div class="box">
		<div id="content"> Content goes here</div> 
	</div> 

	#content {
	    position: absolute;
	    top: 50%;
	    height: 240px;
	    margin-top: -120px; /* 盒子本身高度的一半 */
	}

**优点：**

适用于所有浏览器
不需要嵌套标签

**缺点：**

没有足够空间时，content 会消失(类似div 在 body 内，当用户缩小浏览器窗口，滚动条不出现的情况)

## 方法四 ##

这种方法，在 content 元素外插入一个 div。设置此 `div height:50%; margin-bottom:-contentheight`; 
content 清除浮动，并显示在中间。

	<div id="box">
	    <div id="content">Content here</div>
		<div id="floater"> 
	</div>

	#floater {
	    float: left;
	    height: 50%;
	    margin-bottom: -120px;
	}
	
	#content {
	    clear: both;
	    height: 240px;
	    position: relative;
	}

**优点：**

适用于所有浏览器
没有足够空间时(例如：窗口缩小) content 不会被截断，滚动条出现

**缺点：**

唯一我能想到的就是需要额外的空元素了，可能对于某些强迫症患者来说是不愿意的(这个方法的应用应该也很广)

## 方法五 ##
这个方法使用了一个 `position:absolute`，有固定宽度和高度的 div。这个 div 被设置为 `top:0; bottom:0`;。但是因为它有固定高度，其实并不能和上下都间距为 0，因此 `margin:auto`; 会使它居中。使用 `margin:auto`;使块级元素垂直居中是很简单的。
	
	<div id="box">
		<div id="content"> Content here</div> 
	</div> 

	#content {
	    position: absolute;
	    top: 0;
	    bottom: 0;
	    left: 0;
	    right: 0;
	    margin: auto;
	    height: 240px;
	    width: 70%;
	}
**优点：**

简单粗暴,代码简单,其实设计者当初也根本没想到也能这样用,但是聪明的大家硬是凿出了一条简单的路。

**缺点：**

IE(IE8 beta)中无效
无足够空间时，content 被截断，但是不会有滚动条出现

最后,我不得不说一句所有开发者们最痛恨的一个浏览器,那就是IE6,但是如果你以后做开发,也不得不兼容它,你虽然痛恨他,但你有必须爱他。