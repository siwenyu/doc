# vue学习笔记--条件，循环,事件(5)

1. v-if

字符串模板中(etpl，Handlebars)：

```
	{{#if ok}}
		输出
	{{/if}}
```
在vue中：

```
	<div id="vue1">
	<div v-if="ok">输出</div>
	<div v-else>no</if>
	</div>
```
那么，怎么让他们对应呢？如果多个if else的话。
必须紧跟，压缩之后如果还有内容，不被识别。
2. 通过key管理可复用的元素

```
<template v-if="loginType === 'username'">
  <label>Username</label>
  <input placeholder="Enter your username" key="username-input">
</template>
<template v-else>
  <label>Email</label>
  <input placeholder="Enter your email address" key="email-input">
</template>

```
在ifelse的判断中如果没有添加key属性，默认是一样的key属性，所以仍可以复用.

3. v-show 只是单纯的不显示，加了一个dispaly:none;

```
	<div id="app2" v-show="show">
		v-show
	</div>

```

4.v-show与v-if

v-if是真正的条件限制，如果false，则完全不再执行当前语句的内容，v-show是false仍然会执行，然后只是不显示而已。


运行条件不太会改变时候使用v-if，频繁切换使用v-show

5 循环：v-for

```
	<ul id="example-1">
  	<li v-for="item in items">
    	{{ item.message }}
  	</li>
	</ul>

	// 支持两个参数，键值(不可省略)，索引(key)
	<ul id="example-2">
  	<li v-for="(item, index) in items">
    	{{ parentMessage }} - {{ index }} - {{ item.message }}
  	</li>
	</ul>

	// 整数循环输出
	<div>
  	<span v-for="n in 10">{{ n }}</span>
	</div>

```

6. v-for 比 v-if优先级更高，先执行循环再执行if，这样不会影响条件判断，很方便。

7. 点击增加次数


```

	<div id="app4">
    
    	<input v-model="addNum"><br>
    	<button v-on:click="addNum ++">点击+1</button><br>
    	<button v-on:click="addNumfn">点击+1</button><br>
	</div>

	var vm4 = new Vue({
    el: "#app4",
    data: {
        addNum:1
    },
    methods:{
        addNumfn:function(){
            return this.addNum++
        }
    }
	})

```

8.事件

```
	.stop
	.prevent
	.capture
	.self
	.once
	
	
	<!-- 阻止单击事件冒泡 -->
	<a v-on:click.stop="doThis"></a>
	<!-- 提交事件不再重载页面 -->
	<form v-on:submit.prevent="onSubmit"></form>
	<!-- 修饰符可以串联  -->
	<a v-on:click.stop.prevent="doThat"></a>
	<!-- 只有修饰符 -->
	<form v-on:submit.prevent></form>
	<!-- 添加事件侦听器时使用事件捕获模式 -->
	<div v-on:click.capture="doThis">...</div>
	<!-- 只当事件在该元素本身（而不是子元素）触发时触发回调 -->
	<div v-on:click.self="doThat">...</div>
	
	
	<!-- 只有在 keyCode 是 13 时调用 vm.submit() -->
	<input v-on:keyup.13="submit">
```

































