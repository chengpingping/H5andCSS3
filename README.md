# HTML5
HTML的第五个版本
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
file:
	(值)
	文件
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

##获取元素的方法
1.索引（不直观）
```window.onload=function(){
	document.getElementsByTagName("li")/*获得的是一个数组*/
}```
2.querySelector(新增)
query:查询
selector:选择器
querySelector(传去选择器的名称)只能获取单个元素，如果获取的元素不只一个，只会返回第一个元素。
参数要求：如果是类选择器，必须添加. ;如果是id选择器必须添加# ；否则当标签处理。

```window.onload=function(){
	var javali=document.querySelector(".green");
	console.log(javali);
}```
3.querySelectorAll(新增)
获取满足条件的所有元素--数组
```var allli=document.querySelectorAll("li");
	console.log(allli);
```

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
	window.addEventListener("ononline",function(){
		alert("网络连通");
	})
2.onoffline:网络断开时响应
	window.addEventListener("onoffline",function(){
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
**比如：**添加三个按钮的点击事件
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
2.readAsBinaryString():读取任意类型的文件。返回二进制字符串。这个方法不是用来读取的文件展示给用户看，而是存储文件。例如：读取二进制数据，传给后台，后台接收数据之后，再讲文件存在服务器
3.readAsDataURL():读取文件获取一段data开头的字符串，这段字符串的本质就是DataURL。
DataURL是一种将文件（一般指图像或者能够嵌入到文档的文件格式）嵌入到文档的方案。比如：展示图片，src-指定路径（资源定位--url），src请求的是外部文件，一般来说是服务器资源。意味着他需要向服务器发送请求，占用了服务器资源
DataURL是将资源转换为base64编码的字符串形式，并且将这些内容直接存放在url中，可以优化网站加载速度
4.abort():中断读取
例如:我们现在有一个需求：即使预览；
及时：用户选择图像后立刻进行预览
预览：通过文件读取对象readAsDataURL()完成

	function getFileContent(){
		console.log(123)
	}

## 拖拽接口
实现常见的拖拽接口

## 地理定位接口
获取用户地理信息

## Web存储接口
实现数据的读写

## 应用缓存接口

## 多媒体接口
实现自定义播放器