# border绘制六边形

### 方法一：
html部分：

```
	<div class="six-divall">
        <div class="six-div1">
            <div class="six-div11">
            </div>
        </div>
        <div class="six-div2"></div>
        <div class="six-div3">
            <div class="six-div33">
            </div>
        </div>
    <div>
    <div class="sixcontent">
        <div class="sixdiv">
            <div class="sixdiv-left"></div>
            <div class="sixdiv-right"></div>
        </div>
        <div class="sixdiv1">
            <div class="sixdiv-left1"></div>
            <div class="sixdiv-right1"></div>
        </div>
    </div>
```

css部分：

```
		.six-divall {
            height: 210px;
            width: 180px;
            position: relative;
        }
        .six-div1 {
            height: 28.5715%;
            width: 100%;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-bottom: 100px solid #9b999a;
        }
        .six-div11 {
            height: 28.5715%;
            width: 99%;
            border-left: 148px solid transparent;
            border-right: 148px solid transparent;
            border-bottom: 98px solid white;
            position: absolute;
            left: 0.5%;

        }

        .six-div2 {
            height: 42.857%;
            width: 100%;
            border-left: 2px solid #9b999a;
            border-right: 2px solid #9b999a;
        }
        .six-div3 {
            height: 28.5715%;
            width: 100%;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-top: 100px solid #9b999a;
        }
        .six-div33 {
            height: 29%;
            width: 99%;
            border-left: 148px solid transparent;
            border-right: 148px solid transparent;
            border-top: 98px solid white;
            position: absolute;
            left: 0.5%;
            bottom: 0;
        }
```
此六边形尖朝上，如果太大或者太小，可根据实际稍微调整数值，因为是百分比计算，四舍五入有差异。

### 方法二：
html:

```
	<div class="sixcontent">
        <div class="sixdiv">
            <div class="sixdiv-left"></div>
            <div class="sixdiv-right"></div>
        </div>
        <div class="sixdiv1">
            <div class="sixdiv-left1"></div>
            <div class="sixdiv-right1"></div>
        </div>
    </div>
```

css:

```
		.sixcontent {
            width: 138px;
            height: 120px;
            position: absolute;
            right: 0px;
        }
        .sixdiv{
            width: 66px;
            height: 120px;
            background-color: #9b999a;
            position: relative;
            margin-left: 35px;
        }
        .sixdiv .sixdiv-left{
            width: 0;
            height: 0;
            position:absolute;
            left:-35px;
            top:0;
            border-right:35px solid #9b999a;
            border-top:60px solid transparent;
            border-bottom:60px solid transparent;
        }
        .sixdiv .sixdiv-right{
            width: 0;
            height: 0;
            position:absolute;
            right:-35px;
            top:0;
            border-left:35px solid #9b999a;
            border-top:60px solid transparent;
            border-bottom:60px solid transparent;
        }

        .sixdiv1{
            width: 64px;
            height: 118px;
            background-color: white;
            position: relative;
            margin-left: 36px;
            top: -119px;
            left: 0px;
        }
        .sixdiv1 .sixdiv-left1{
            width: 0;
            height: 0;
            position:absolute;
            left:-35px; 
            top:0;
            border-right:35px solid white;
            border-top:59px solid transparent;
            border-bottom:59px solid transparent;
        }
        .sixdiv1 .sixdiv-right1{
            width: 0;
            height: 0;
            position:absolute;
            right:-35px;
            top:0;
            border-left:35px solid white;
            border-top:59px solid transparent;
            border-bottom:59px solid transparent;
        }
```
此绘制顶平六边形，大小不可定制。
