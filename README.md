# weapp
 
小程序


## UI组件

1. **weui**和**zanui**两个文件夹在项目打包（预览、上传）过程中已经被排除，现在放到项目里主要为了参考
2. 建议最开始先使用weui的组件，weui.wxss已经提取到style文件夹中了；
3. zanui是外部可以直接引用的组件，后期如果使用，在项目打包过程中不能排除


## wxml和html区别

        <view></view>_div
        <scroll-view></scroll-view>_会滚动的div
        <navigator></navigator>_a
    	<text></text>_span文字
    	<image/>_img图片
    	<icon>_i小图标
    	<picker></picker>_select单选多选，通过mode来区分


## 小程序字体规范

1. rpx单位是微信小程序中css的尺寸单位，rpx可以根据屏幕宽度进行自适应。
2. 开发微信小程序时设计师可以用 iPhone6(750*1334) 作为视觉稿的标准。
3. 参考网站 [http://www.51xuediannao.com/javascript/xiaochengxu_rpx.html](http://www.51xuediannao.com/javascript/xiaochengxu_rpx.html)
![http://res.xiaohucdn.com/Upload/Ad/20180717/dcc7ccffd64a46f8875f5e2c5951fbce.jpg](http://res.xiaohucdn.com/Upload/Ad/20180717/dcc7ccffd64a46f8875f5e2c5951fbce.jpg)

        .f10{font-size:20rpx} 小标签（常用）
    	.f12{font-size:24rpx} 一般常用字体大小，文章内容（常用）
    	.f14{font-size:28rpx} 小标题（常用）
    	.f16{font-size:32rpx} 大标题（常用）
    	.f18{font-size:36rpx} 大大标题

## CSS
### 解析原则
css选择器是从右往左解析
[https://blog.csdn.net/jinboker/article/details/52126021](https://blog.csdn.net/jinboker/article/details/52126021)

### 原则
1\. 书写简洁、高效的css，所谓高效就是让浏览器查找更少的元素标签来确定匹配的css属性<br/>
2\. 一个div建议最多有3个css属性，减少查找时间（那天说4个不是很建议）
### CSS命名规范
1\. 一律小写<br/>
2\. 尽量用英文<br/>
3\. 可以加中划线和下划线（H5中书写不建议使用"_"，因为有浏览器兼容性的问题，在IE6下无效，但小程序不考虑这一点，且官方weui中划线和下划线都有用）<br/>
4\. 少用层级关系，下面一个例子看看就明白了，我列的是H5的标签，小程序也是一样的道理（把层级关系体现在命名里面）

```
## 不建议这样写
<div class="main">
	<div class="top">
		<p></p>
	</div>
	<div class="center">
		<p></p>	
	</div>
	<div class="bottom">
		<p></p>
	</div>
</div>
<style>
.main .top p{...}
.main .center p{...}
.main .bottom p{....}
</style>
## 建议下面这样写，把层级关系体现在命名里面
<div class="main">
	<div class="main-top">
		<p class="main-top-p"></p>
	</div>
	<div class="main-center">
		<p class="main-center-p"></p>
	</div>
	<div class="main-bottom">
		<p class="main-bottom-p"></p>
	</div>
</div>
<style>
.main-top-p{...}
.main-center-p{...}
.main-bottom-p{...}
</style>
```

### CSS优先级问题
1\. 先看看css选择器有哪些再看优先级的问题，下面列了常用的几个

```
##ID选择器
id="name",id="name_txt"
## 类选择器
.class="head",class="head_logo"
## 标签选择器
body,div,p,ul,li
## 组合选择器
.head .head_logo
## 后代选择器
#head .nav ul li 从父集到子孙集的选择器)
## 伪类选择器,就是链接样式,a元素的伪类，4种不同的状态
a:link,a:visited,a:active,a:hover
```
2\. 优先级排序
行内样式>ID选择器>类选择器>标签选择器<br/>
注：下面的例子<br/>
```
<div class="content">
	<p class="con-p colred"></p>
</div>
<style>
## 下面这种定义会显示蓝色，优先级第一行>第二行
.content .con-p{ color:blue}
.colred{ color:red}
## 下面这种定义会显示红色，优先级第二行>第一行
.con-p{color:blue}
.colred{ color:red}
## 下面这种定义会显示蓝色，同级的话，优先级写在后面的>前面的
.colred{ color:red}
.con-p{color:blue}
</style>
```

## 参考的网站

 微信UI在线预览
 [https://weui.io/](https://weui.io/)
 
 weui-git地址
 [https://github.com/Tencent/weui-wxss](https://github.com/Tencent/weui-wxss)
 
 小程序开发资源汇总
 [https://github.com/justjavac/awesome-wechat-weapp](https://github.com/justjavac/awesome-wechat-weapp)
 