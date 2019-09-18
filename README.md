# HTML5

1.HTML的第五个版本

2.支持

	所有的主流浏览器都支持：(chrome、firefox、Safari)，以及ie9(选择性支持)及以上，ie8以下不支持；

3.改变了用户的交互方式；多媒体：video、audio、canvas；

4.增加了其他新特性：语义特性、本地存储特性、网页多媒体、二维三维、特效（过滤、动画）

5.相对于h4：

	1.进步：抛弃了一些不合理不常用的标记和属性；
	2.新增了一些标记和属性；
	3.从代码的角度而言，h5的网页结构代码更加简洁。

# h5中的新标签

nav:导航

header:页眉

footer:页脚

main:主体

article:文章

aside:主题内容以外

# h5的兼容性

## 行级元素在IE浏览器中设置宽高是无效的；

解决方法：将行级元素改成块级元素

	display: block;

## IE8完全不支持，IE8不认识新标签无法解析；

### 第一种方法：手动创建

解决方法：创建标签

在<script>中```document.createElement("header")```;

但是，默认的标签都是行级元素；

解决方法：将行级元素改成块级元素

	display: block;

### 第二种方法：引入第三方插件

html5shiv.min.js:在默认的情况下，IE8及一下不支持H5，引入这个文件就可以做到兼容

	<script src="../js/html5shiv.min.js"></script>

# ***form表单中***

# h5中的新增属性

type属性:

	(值)
	email：验证邮箱
	tel:在移动端弹出数字键盘，让你只能输入数字的
	url:网址验证
	number:数字，max最大值，min最小值，value默认值
	search:框内有删除，更人性化的体验
	range:范围滑动条，max最大值，min最小值，value默认值（50）
	color:颜色识取
	date：日期(年月日)
	time:时间(时分秒)
	datetime:日期时间(大多数不支持，只有Safari支持)
	datetime-local:日期时间,大多数支持
	month:月份
	week:星期
	file:文件

placehoder属性:

	(值)
	提示文本

autofocus:自动获取焦点(没有值)

autocomplete:自动提示

	(值)
	on打开
	off关闭
	***必须提交过，必须有name属性(可以直接加在表单上)***

required:必须输入(没有值)

pattern:

	(值)
	正则表达式验证

***\*代表任意个，?代表0个或则1个，+代表一个或则多个;^开始，$结束***

multiple:选择多个文件、邮箱(没有值)

form:

	(值)
	表单的id
	表单元素并没有包含在form表单中,却需要和表单一起提交，给原表单设置一个id,设置表单的form="id"

# h5中新增的元素：

## datalist:创建选项列表(firefox不支持)

同样使用option设置选项：value具体的值，lable提示信息，辅助值

建立输入框与datalist相连：在input中添加list="datalist的id"

***如果type是网址，一定要加上：http://***

## keygen:加密(大多数浏览器不支持)

客户端：

	生成公钥和私钥
	提交时:信息+私钥>>二次密码

服务端：

	公钥
	二次加密的数据
	解密：使用收到的公钥解密数据

## output:只能显示，不能修改

语义性更强

***作用不大***

# h5中新增的事件

## oninput

监听当前指定元素的内容的改变：只要内容改变（添加、删除），就会触发这个事件监听器；

他与onkeyup和onkeydown的区别：

onkeyup:键盘弹起时触发；

onkeydown:键盘按下时触发。

## oninvalid

当验证不通过时触发。

自定义提示信息：```this.setCustomValidity(自定义信息)```;

# prograss

h5中新增了进度条;

max:最大值

value:当前值

## meter

度量器：衡量当前的进度值

high:规定的最大值

low:规定的最小值

max:最大值

min:最小值

value:当前值

# h5中的多媒体标签

之前：

embed：直接插入视频文件，本质是调用本机上安装的软件，有兼容性问题；

flash插件：安装flash，1.学习flash,增加成本；2.apple设备部支持flash

h5为了解决这个问题，添加了两个标签：

## audio音频

src:播放音频的路径

controls:音频播放器的控制器面板

autoplay:自动播放

loop:循环播放

## video视频

src:播放视频的路径

controls:视频播放器的控制器面板

autoplay:自动播放

loop:循环播放

width:宽度

height:高度

poster：当视频还没有完全下载或则用户还没点击播放前的默认显示时间。默认是视频的第一帧。

设置视频宽高是等比例设置，所以只需要设置width或者height

***重要***

soucer:因为浏览器支持的视频文件格式不一样，所以我们在添加视频时，需要考虑浏览器是否支持。我们可以准备多个视频文件，让浏览器自动选择

# h5中的DOM操作

## 获取元素的方法

1.索引（不直观）

	window.onload=function(){
		document.getElementsByTagName("li")/*获得的是一个数组*/
	}

2.querySelector(新增)

query:查询

selector:选择器

querySelector(传去选择器的名称)只能获取单个元素，如果获取的元素不只一个，只会返回第一个元素。

参数要求：如果是类选择器，必须添加. ;如果是id选择器必须添加# ；否则当标签处理。

	window.onload=function(){
		var javali=document.querySelector(".green");
		console.log(javali);
	}

3.querySelectorAll(新增)

获取满足条件的所有元素--数组

	var allli=document.querySelectorAll("li");
	console.log(allli);

## 操作元素的样式

新增：classList

1.添加

add:一次只能添加一个样式

	document.querySelector("#add").onclick=function(){
		document.querySelector("li").classList.add("red")
	}

***添加多个：需要在写一次添加代码***

**之前**

	document.querySelector("li").className="underline";//会将之前的样式去掉，但是可以使用+=

2.移除

remove:为元素移除指定名称的样式，一次也只能移除一个;只移除样式，不移除属性。

	document.querySelector("#remove").onclick=function(){
		document.querySelector(".blue").classList.remove("blue");
	}

3.改变

toggle：切换元素样式，如果元素之前没有指定名称的样式则添加；否则，移除；

	document.querySelector("#toggle").onclick=function(){
		document.querySelector(".green").classList.toggle("green");
	}

4.判断

contains:判断元素是否包含指定名称的样式，返回true/false

	document.querySelector("#contain").onclick=function(){
		document.querySelectorAll("li")[3].classList.contains("green");
	}

5.获取样式

获取元素添加的样式

	document.querySelector("li").classList.item(0);

# h5中自定义属性
 
## 定义

**规范：**

1.data-开头

2.data-后必须有一个字符

**建议：**

1.名称应该都是用小写--不要包含任何大写字符

2.名称中不要有任何特殊字符

3.名称不要使用纯数字

	<p data-school-name="itcast"></p>

## 取值

1.获取自定义属性

2.将data-后面的单词使用camel命名法连接,必须使用camel命名法，否则无法取到

	window.onload=function(){
		var p=document.querySelector("p");
		var value=p.dataset["schoolName"];//camel命名法
		console.log(value);
	}

# 网络监听接口（主要实现移动端）

## 网络状态改变的接口

改变事件

1.ononline：网络连接的时候触发这个事件

	window.addEventListener("online",function(){
		alert("网络连通");
	})
	
2.onoffline:网络断开时响应

	window.addEventListener("offline",function(){
		alert("网络断开");
	})

## 全屏API 

实现元素全屏效果

全屏操作的主要方法和属性：

1.requestFullScreen():开启全屏显示

	不同的浏览器支持的方式不同,需要添加不同的前缀，比如：Chrome-webkit;firefox:moz;ie:ms;opera:o
	我们需要做一些判断来支持不同的浏览器，使用能力测试，添加不同浏览器的前缀

2.cancelFullScreen():退出全屏显示

	也要添加前缀，退出全屏只能使用document来实现
	
3.fullScreenElement:是否是全屏显示状态

	也只能只能使用document判断
	也要添加前缀，退出全屏只能使用document来实现

3.fullScreenElement:是否是全屏显示状态

	也只能只能使用document判断

**比如**添加三个按钮的点击事件

	window.onload=function(){
		var div=document.querySelector("div");
		/*全屏操作*/
		document.querySelector("#full").onclick=function(){
			if(div.requestFullScreen){
				div.requestFullScreen();
			}else if(div.webkitRequestFullScreen){
				div.webkitRequestFullScreen();
			}else if(div.moRequestFullScreen){
				div.moRequestFullScreen();
			}else if(div.msRequestFullScreen){
				div.msRequestFullScreen();
			}
		}
		/*退出全屏*/
		document.querySelector("#cancelFull").onclick=function(){
			if(document.requestCancelScreen){
				document.requestCancelScreen();
			}else if(document.webkitRequestCancelScreen){
				document.webkitRequestCancelScreen();
			}else if(document.mozRequestCancelScreen){
				document.mozRequestCancelScreen();
			}else if(document.msRequestCancelScreen){
				document.msRequestCancelScreen();
			}
		}
		/*判断是否是全屏*/
		document.querySelector("#isFull").onclick=function(){
			if(document.fullscreenElement||document.webkitFullscreenElement||document.mozFullScreenElement||document.msFullscreenElement){
				alert(true);
			}else{
				alert(false)
			}
		}
	}

## 文件读取接口

实现文件读取效果

FileReader：读取文件内容

1.readAsText():读取文本文件（可以使用TXT打开的文件），返回文本字符串，默认编码是UTF-8；

2.readAsBinaryString():读取任意类型的文件。返回二进制字符串。这个方法不是用来读取的文件展示给用户看，而是存储文件。例如：读取二进制数据，传给后台，后台接收数据之后，再讲文件存在服务器；

3.readAsDataURL():读取文件获取一段data开头的字符串，这段字符串的本质就是DataURL。

	DataURL是一种将文件（一般指图像或者能够嵌入到文档的文件格式）嵌入到文档的方案。比如：展示图片，src-指定路径（资源定位--url），src请求的是外部文件，一般来说是服务器资源。意味着他需要向服务器发送请求，占用了服务器资源。
	DataURL是将资源转换为base64编码的字符串形式，并且将这些内容直接存放在url中，可以优化网站加载速度。

4.abort():中断读取

例如:我们现在有一个需求：即使预览；

及时：用户选择图像后立刻进行预览；

预览：通过文件读取对象readAsDataURL()完成

	function getFileContent(){
		//console.log(123)
		/*创建文件读取对象*/
		var read=new FileReader();
		/*读取文件，获取DataURL*/
		var file=document.querySelector("#myFile").files[0];
		read.readAsDataURL(file);//没有返回值，但是读取完之后，他会将读取的结果存储在文件读取的对象result中；需要一个参数（blob:binary large object）；文件存储在file表单元素的files属性中，他是一个数组
		/*读取数据*/
		/*
		 * FileReader提供了完整的时间模型，用来捕获读取文件时的状态
		 * onabort:读取文件中片段时触发
		 * onerror:读取错误时触发
		 * onload:文件读取成功时触发
		 * onloadend:文件读取完成是触发，无论失败还是成功
		 * onloadstart:开始读取时触发
		 * onprogress:读取文件的过程中持续触发*/
		read.onload=function(){
			//console.log(reader.result);
			/*展示*/
			document.querySelector("img").src=read.result;
		}
	}

## 拖拽接口

实现常见的拖拽接口

在h5中，如果想拖拽元素，就必须添加元素```draggable="true"```.(图片和超链接是默认可以拖拽的)

但是学习拖拽主要是学习拖拽事件：

1.应用于被拖拽元素的事件

	ondrag:拖拽的过程中会触发(持续)
	ondragstart：拖拽开始时触发
	ondragleave：鼠标离开拖拽元素时触发
	ondragend：拖拽结束时触发

2.应用于目标元素的事件

	ondragenter:当拖拽元素时鼠标进入目标元素时触发
	ondragover:当拖拽元素停留在目标元素上时调用
	ondrop:当在目标元素上松开鼠标时触发（浏览器会默认阻止），如果想要触发就要在ondragove事件上阻止浏览器的默认行为;添加被拖拽的元素到当前的目标元素
	ondragleave:当鼠标离开目标元素时触发

***阻止浏览器的默认行为，才能触发drop事件***

当我们有多个元素需要拖拽，并且有多个目标元素时，我们需要一个通用的方法解决这个问题:
使用事件源参数（事件捕获）来获取当前被拖拽的子元素:

1.应用于被拖拽元素的事件

	var obj=null;//不安全
	document.ondragstart=function(e){
		//console.log(e.target);
		obj=e;
		e.target.style.opacity=0.5;
		e.target.parentNode.style.borderWidth="5px"
	}
	document.ondragend=function(e){
		e.target.style.opacity=1;
		e.target.parentNode.style.borderWidth="1px"
	}

2.应用于目标元素的事件

	document.ondragenter=function(e){
		//console.log(e.target);
	}
	document.ondragover=function(e){
		e.preventDefault();
	}
	document.ondrop=function(e){
		e.target.appendChild(obj)
	}

由于只用全局变量存储数据不安全，所以我们通过```dataTransfer```来实现数据的存储与获取

1.setData(format,data);

format:数据类型(text/html text/uri-list)

data:数据（一般来说时字符串的值）

2.getData(format);

通过dataTransfer存储的值只能在drop中取

## 地理定位接口

获取用户地理信息（基于位置的服务）

API:navigator.geolocation.getCurrentPosition(success,error,option);

option：可以设置获取数据的方式,enableHighAccuracy:true/false(是否使用高精度)，timeout:设置超时时间（单位ms），maximumAge:可以设置浏览器重新获取地理信息的时间间隔（单位ms）；

要使用三方接口来获取地理信息：百度地图，高德地图

**百度地图**

	<script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=百度地图密钥"></script>
	<script type="text/javascript">
	var map = new BMap.Map('allmap');
	map.centerAndZoom(new BMap.Point(116.404269,39.913828), 12);
	map.enableScrollWheelZoom(true);
	// 覆盖区域图层测试
	map.addTileLayer(new BMap.PanoramaCoverageLayer());

	var stCtrl = new BMap.PanoramaControl(); //构造全景控件
	stCtrl.setOffset(new BMap.Size(20, 20));
	map.addControl(stCtrl);//添加全景控件
	</script>

获取位置的方式：

1.IP地址

优点：任何地方都有

缺点：不精确

2.GPS

优点：精确

缺点：

3.WI-FI

4.手机信号

5.用户定义

获取用户地理信息

## Web存储接口

实现数据的读写

**以前**使用cookie来存储数据，但是cookie只有4k，并且cookie解析比较复杂；

1.sessionStorage的使用：

存储数据到本地，存储容量5MB左右。本质是数据存储在当前页面中；生命周期为关闭当前页面之前，关闭页面会自动清除。

**方法：**

	1.setItem(key.value):以键值对的方式存储数据；
	2.getItem(key):通过指定名称的key获取对应的value值；
	3.removeItem(key):通过指定名称key删除对应数据；
	4.clear:清空所有存储的内容。(慎用)

2.localStorage的使用：

存储的内容更多，大概20MB；不同浏览器不能共享数据，但是同一浏览器不同页面可以共享数据；永久生效，它是存储在硬盘上的不会因为浏览器的关闭而消失；如果要清除必须手动清除。

**方法：**

	1.setItem(key.value):以键值对的方式存储数据；
	2.getItem(key):通过指定名称的key获取对应的value值；
	3.removeItem(key):通过指定名称key删除对应数据；
	4.clear:清空所有存储的内容。(慎用)

## 应用缓存接口

通过创建cache manifest文件，可以轻松创建web应用离线版本；

**优势**

	可以配置需要缓存的资源；
	网络无连接应用仍可用；
	本地读取缓存资源，提升访问速度，增强用户体验；
	减少请求，缓解服务器负担；

**实现**

1.指定属性

manifest="应用程序缓存清单文件的路径（建议文件的扩展名是appcache,这个文件的本质就是一个文本文件）"
	<html manifest="demo.appcache">

2.创建缓存清单文件

manifest文件：
	1.CACHE MANIFEST--表示这是一个manife；
	2.CACHE--在此标题下列出文件在首次加载后进行缓存的内容清单；
	3.NETWORK--在此标题下列出文件需要与服务器的连接而不会被缓存；
	4.FALLBACK--在此标题下列出无法访问的文件回退页面（比如：404）

## 多媒体接口

实现自定义播放器

1.方法

play()播放

load()加载

pause()暂停

这些都是原生方法，如果使用jQuery实现自定义播放器就要jQuery对象转成DOM元素，才能调用这些方法

2.属性

autoplay

controls

currentTime当前播放时间

duration音频视频总时间

paused视频播放的状态

3.事件

oncanplay当视频可以播放时触发

onpause暂停时触发

onended视频播放结束时触发

ontimeupdate时间改变

**注意：直接从编辑器中打开页面可能会不支持跳播，直接打开网页源文件就可以实现跳播**

***

# CSS3

1.CSS的第三个版本

2.新增了许多的属性，弥补了C2的不足，使得web开发更加的便捷；

**现状**

3.CSS3的兼容性差，需要添加私有前缀；移动端支持优于PC端；CSS>>js；应用广泛；

**使用**

4.渐进增强（优雅降级-hack）；考虑用户群体；遵照产品方案；

**环境**

5.chrome ver46+;firefox ver42+;photoshop CS6

**手册**

6.[]:表示可选；||：表示或者；|：表示多选一；?:表示0个或者1个；*：表示0个或者多个；{}:表示范围；

# 选择器

## 属性选择器：

属性时相对于标签而言的；所谓属性选择器就是根据属性名称的值来查找元素

E[attr]:查找拥有attr属性的E标签

E[attr=value]:查找拥有attr属性的E标签并且attr的属性值等于value（严格匹配）

E[attr*=value]:查找拥有attr属性的E标签并且attr的属性值中包含value

E[attr^=value]:查找拥有attr属性的E标签并且attr的属性值以value开头

E[attr$=value]:查找拥有attr属性的E标签并且attr的属性值以value结尾

## 伪类选择器

**之前**
	a:hovers鼠标移动到元素之上
	a:link未访问过
	a:active鼠标点击了元素
	a:visited已访问过

***结构伪类***

1.相对于父类元素

E:first-child:查找**E元素**的**父级元素**中**第一个**E元素

E:last-child:查找**E元素**的**父级元素**中**最后一个**E元素

查找时限制类型(更实用)：也是相对于父元素；查找时指挥查找满足类型的元素，过滤其他元素；

	E:first-of-type
	E:last-of-type

E:nth-child(从1开始的索引||关键字||表达式):指定索引位置

**关键字**

	even:偶数
	odd:基数

限制类型：

	E:nth-of-type

**表达式**

如：
	E:nth-of-type(n)--n默认取值范围为0-子元素的长度，当n<=0时无效

**空值**

	E:empty：没有任何内容，也不能加空格

E:target:可以为锚点的目标元素添加元素，当目标元素被触发为当前锚链接的目标时，调用此伪类

2.相对于兄弟元素

+:获取当前元素**相邻**的**指定类型**的元素

~：获取当前元素**指定类型**的**兄弟**元素

## 伪元素选择器

**重点**E::first E::after

**特点**他的功能完全等价于一个dom元素；他不会在dom树中生成；

**注意**必须添加content元素，否则后期不可见；默认是行级元素，要想设置宽高必须设置为块级元素display:block position float

**其他**

	E::first-letter 文本的第一个字母或字
	E::fist-line 文本第一行（如果设置可first-letter,firstletter就无法再识别）
	E::selection 可改变选中文本的样式

# 颜色的设置

**之前**

1.使用预设值：red blue……

	background-color:red;

2.使用颜色拾取器(RGB值)：选择颜色面板

	background-color:#fff;

## RGBA

R:red

G:green

B:blue

A:Alpha颜色透明通道

颜色是6位16进制数据

	background-color:rgb(0,0,0);

## HSLA

H:Hue(色调 色相)，0/360表示红色，120表示绿色，240表示蓝色；取值：0-360过度为红橙黄绿青蓝紫。

S:Saturatuion(饱和度)，取值：0.0%-100.0%；

L:Lightness(亮度)，取值：0.0%-100.0%，50%是平衡值；(photodhop里是Brightness/B)**建议保留50%**

A:Alpha(透明度)，取值：0-1，0代表完全透明，1代表完全不透明

	background-color:hsl(0,0%,0%)

## 透明度的使用

**之前**

	opacity:0.5;

**但是**此方法用于设置父级容器透明，容器中的所有子元素都会透明；

**现在**

	background-color:rgba(255,0,255,0.2)

***不会影响子元素***

透明度补充说明：

	opacity:针对整个盒子设置透明度，子盒子及内容会继承父盒子的透明度
	transparent:不可调节透明度，始终是完全透明
	使用rgba来控制颜色透明度，相对于opacity，不具有继承性。

# 文本阴影

text-shadow:none|<length>none|[<shadow>,]\*<shadow>或none|<color>[,<color>]\*

[颜色(color) x轴(X Offset) y轴(Y Offset) 模糊半径(Blur)],[颜色(color) x轴(X Offset) y轴(Y Offset) 模糊半径(Blur)]……

lenth:长度值，同时确定阴影的角度和距离

shadow:阴影模糊值

color:指定阴影的颜色

	text-shadow:2px 3px 2px #000;/*Xoffset Yoffset Blur color*/

# 盒模型

文档中的每个元素都被描绘成一个盒子，渲染时width指内容的宽度

默认情况下，css设置盒子宽度只是内容的宽度，而非盒子的宽度，高度同样；所以盒子的宽度=padding+border+width，所以很容易出现问题；

css3中通过box-sizing来指定盒模型

	content-box:设置的width是内容的属性值
	border-box:设置的width是盒子最终的宽度

# 圆角

**之前**使用Photoshop画出圆角，在导入代码文件中引用，但是修改起来非常不方便。

**现在**

	border-radius: 0px;

一个值：四个角都一样

两个值：（左上 右下）（右上左下）

三个值：（左上）（右上左下）（右下）

四个值：左上 右下 右下 左上

如果我们要画一个椭圆就要使用```border-radius: 100px/50px```;

**/是用来设置当前不同方向的半径（水平/垂直方向）**

添加某个圆角：

	border-radius:0px 10px 0px 0px;
	border-top-right-radius: 10px;

设置某个角点上两个方向的圆角

	border-top-right-radius: 100px 50px;

设置四个角点不同方向上的不同圆角

	border-radius:100px 80px 60px 40px/ 20px 40px 60px 80px;

# 边框阴影

**文本阴影** text-shadow:offsetX offsetY blur color

**边框阴影** box-shadow:h(水平) v(垂直) blur spread(扩展) color inset(内阴影)

# c3中的渐进实现

渐变不是一个单一色，他产生的是一个图像，所以使用background来添加；

## 线性渐变

1.linear-gradient:线性渐变指沿着某条直线朝一个方向产生渐变效果

**语法**

	linear-gradient([<point>||<angle>,]?<stop>[,<stop>]*)

**取值**

point:

	to-left:从右到左渐变
	to-right：从左到右渐变
	to-top：从下到上渐变
	to-bottom：从上到下渐变

angle:角度

	0deg:向上渐变
	90deg:向右渐变
	180deg:向下渐变（默认值）
	270deg:向左渐变

stop:色标

	第一个是起点颜色
	第二个是终点颜色

## 径向渐变

radial-gradient:从一个点向四周产生渐变效果；

**语法**

	radial-gradient([<shap>||<size>][at <position>]?,[at <position>,]?<color-stop>[,<color-stop>]+)

**取值**

shap:形状

	circle:产生一个正圆
	ellipse:适配当前形状

at position:位置

	默认在正中心，可以赋值坐标也可以赋值关键字（left right top bottom）

size:大小

	closest-side:最近的边
	farthest-side:最远的边
	closest-corner:最近的角
	farthest-corner:最远的角(默认)

color-stop

	第一个是起点颜色
	第二个是终点颜色

## 重复渐变

**语法**

	repeating-radial-gradient(<shap> position,color stop,color stop)
	repeating-linear-gradient(point,color stop,color stop)

# c3中的background新增属性

**之前**

1.颜色：
	background-color:color;

2.图片：

	background-image:url(".../...");

如果图片大于容器，那么默认从容器左上角开始放置；如果图片小于容器，那么图片就默认平铺；

3.设置背景平铺

background-repeat

	no-repeat：不平铺
	round:将图片缩放平铺
	space：不会缩放平铺，会在图片间生成相同的间距

4.设置在滚动容器中的背景行为：跟随滚动、固定

background-attachment

	fixed:背景图的位置固定不变
	scroll:滚动容器的时候背景跟着一起滚动
	local:背景图片会跟随内容一起改变

**新增**

background-size：

语法：
	background-size:auto(原始图片大小)||number(数值)||percentage(百分比)||cover(放大铺满)||contain(缩小铺满)
	length:使用之前先确定宽高比
	percentage:设置百分比是参照父容器可放置内容的50%
	contain：按比例调整大小，使宽高自动适应背景区，可能会有空白区域；图片大于容器，将图片缩小；当图片小于容器，将图片放大；
	cover:与contain相反,背景图片会按比例缩放，适应整个背景区域，图片内容可能会溢出；

background-position:

	center:图片居中显示

**增大响应区**

background-origin:设置背景的原点

	border-box从border的位置开始填充背景，会与border重叠
	padding-box从padding开始填充背景，会与padding重叠
	content-box从内容的位置开始填充背景

background-clip:设置内容的裁切，控制的是显示

	border-box显示border及以内的内容
	padding-box显示padding及以内的内容
	content-box显示content及以内的内容

# c3中的图片边框基本用法

	border-image-source: url(../img/head.jpeg);/*设置边框图片*/
	border-image-slice: 27 fill;/*设置四个方向上的裁切距离*/
	fill:做内容填充
	border-image-width:边框图片宽度，如果没有设置，那么边框的大小就是元素的大小
	border-image-outset:扩展边框
	border-image-repeat:repeat直接平铺,round缩放平铺,stretch拉伸

**缩写**

border-image:source slice/width/outset repeat;

**细节**

1.边框图片的本质是背景，不会影响元素的内容；

2.内容只会被容器的border和padding影响。

**建议**增加padding值或者border值


颜色会被图片覆盖

# c3中的transition属性

过渡效果

**之前**

	active：单击响应效果

**现在**

	transition：过渡
	transition-property:添加过渡效果样式属性名称
	transition-duration:过渡效果耗时
	transition-timing-function:设置时间函数--控制运动的速度，linear匀速，ease先慢后快
	transition-delay:过渡效果的延迟

过渡效果执行完毕会默认还原到原始状态

**简写**

	transition:属性名称    过渡时间    时间函数    延迟

**为多个样式添加过渡效果**

	transition:属性名称    过渡时间    时间函数    延迟，属性名称    过渡时间    时间函数    延迟，……
	transition:all(所有样式) 过渡时间    时间函数    延迟(效率较低)
	steps(4):步长值，可以让过渡效果分几个步骤

过渡效果非常严格，只能从某个数值过渡到一个具体的数值

# c3中的transform属性

2d、3d变换效果

## 2D转换

通过css transform属性可以实现移动、缩放、旋转、斜切

	transform-origin:设置旋转的轴心，left top bottom center

**移动**

translate()：可以把元素从原来的位置移动，参照元素左上角原点;执行完毕后会恢复到原始状态。

语法：

	translate(tx)|translate(tx,ty)
	translateX(tx)|translateY(ty)

**缩放**

scale():让元素根据几何中心进行缩放

语法：

	scale(sx|sy)|scale(sx,sy)
	scaleX(sx)|scaleY(sy)

**旋转**

rotate():是元素根据在指定的角度进行二维的旋转，接受一个角度值，顺时针旋转为正值，逆时针旋转为负值；

语法：

	rotate(0)

**斜切**

skew():能够让元素倾斜展示。

语法：

	skew(ax)|skew(ax,ay)
	skewX(ax)skew(aY)

[例1：旋转轴心](./css3demo/15-旋转轴心的案例.html)
[例2：添加多个transfrom](./css3demo/16-添加多个transform属性.html)
[例3：实现居中](./css3demo/17.实现任意元素居中.html)

## 3D转换