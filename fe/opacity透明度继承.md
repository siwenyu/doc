# opacity透明度继承
关于pc端opacity兼容问题：
```
	opacity:0.5;
  	filter:alpha(opacity=50);

```

继承现象：
原始demo代码：
```
<!DOCTYPE html>
	<html lang="en">
	<head>
	  <meta charset="UTF-8">
	  <title>Document</title>
	  <style>
	  *{
	  	margin:0px;
	  	padding:0px;
	  }
	  .div1 {
	  	position:absolute;
	  	bottom:0px;
	  	left:0px;
	  	color:white;
	  }
	  .bg {
	  	background:url(https://unsplash.it/200/300/?random);
	  	width:200px;
	  	height:300px;
	  	background-repeat:no-repeat;
	  	position:relative;
	  }
	  /* 修改测试的部分 */
	  .div1{
	  	background:black;
	  	opacity:0.5;
	  }
	  .div2{
	  	opacity:1;
	  }
	  </style>
	</head>

	<body class="bg">
		<div class="div1">
			我想要透明度
			<div class="div2">
				其实我是子元素，不想有透明度。
			</div>
		</div>
		<div class="">
			其实我是兄弟元素，没有透明度。
		</div>
	<hr>
	<p>PS:如果图片不够明显，请刷新换图</p>
	</body>
	</html>
```
如图：
	<img src="img/op2.png">

可是我只想黑色背景透明度变化。
解决办法1:
```
  .div1{
  	background:rgba(0,0,0,0.5);
  }
  .div2{
  }
 ```
解决办法2：
将背景内的文字部分拿出来，不让这部分成为设置透明度元素的子元素。代码：略
如图：
	<img src="img/op1.png">