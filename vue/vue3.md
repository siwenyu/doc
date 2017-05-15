# vue学习笔记--模板语法（3）

1. 虚拟dom：
	* 虚拟dom就是js结构中逻辑使用的dom结构，并没有直接写在html中。
	* 出现原因：操作dom成本是非常非常大的，能不能处理好了逻辑之后再渲染dom？
	* 类似于cpu和硬盘，cpu是非常快的，相当于js操作虚拟dom，读写硬盘是非常慢的，相当于渲染真实dom。
	
2. 普通文本绑定：

```
	<div id="app1">{{ name }}</div>  	
```

此时会监听name，只要实例中的data.name变化发生变化，vue的监听机制就会改变这个dom的值。如果不想改变：

```
	<div id="app1" v-once>{{ name }}</div>  
```
第一次渲染的时候是什么就是什么，data改变，dom中的变量不会改变。

3. 纯html插入

```
	<div id="app2" v-html="html"></div>
	
	var data = {
    name: "zhangsan",
    height: "75KG",
    data: [
        {data1:1},
        {data2:2},
        {data3:3},
        {data4:4},
        {data5:5},
        ],
    html: "<p style='color:red;'>这是插入的html</p>"
}

var vm3 = new Vue({
    el:"#app3",
    data: data
    
})
```

4. 属性绑定：v-bind

比如绑定title ：

```
	<span v-bind:title="message1">鼠标悬停显示的文字</div>
```

5. 模板中使用js：

	* 所有的数据作用域是当前实例的作用域
	* 只支持单一表达式，不支持语句比如：var，if else等

```
	<div id="app4" >{{ name=='zhangsan'?'name是zhangsan':'name不是zhangsan' }}</div>

```

5. 指令：

* 指令的预期是将某些行为加在dom上

```
	<p v-if="seen">Now you see me</p>
```	

6. 参数

* 指令v-bind:aaa="bbb"，aaa是属性名称，bbb是参数，要绑定的参数值、要执行的事件。比如：

```
	<div v-bind:title="title"></div>  //绑定title属性，值是data中的title

	<div v-on:click="dosomething">   //绑定click事件，值是methods中的方法名。
```

7. 修饰符

	* 指令需要以某种特殊方式绑定，修饰符定义这种方式
```
	<form v-on:submit.prevent="onSubmit"></form>
``` 
	提交的时候调用'event.preventDefault()'阻止默认事件。

8. 过滤器


	* 目的：文本转换，不进行复杂计算。
	* 使用：模板插值，v-bind绑定属性的时候

9. 缩写：

* v-指令为模板添加动态行为时候很有用，但是有些指令使用频繁，可以省略：

			
```
	<!-- 完整语法 -->
	<a v-bind:href="url"></a>
	<!-- 缩写 -->
	<a :href="url"></a>
	
	<!-- 完整语法 -->
	<a v-on:click="doSomething"></a>
	<!-- 缩写 -->
	<a @click="doSomething"></a>

```























