# vue学习笔记（1）

1. 框架引入：

```
	<script src="https://unpkg.com/vue/dist/vue.js"></script>
```
1. 基础模板结构：
	* 标签名
	* 标签标识
	* 标签绑定的数据
	* 指令：绑定其他元素属性：v-dind:title。但是title是标签的自带属性，不绑定也会有，但是不能绑定vue对象。指令带有前缀：v-，响应js行为


```
	<div id="app" >
		{{ message }}
		<span v-bind:title="message">
			这是鼠标悬停显示的title。
		<span>
	</div>


```

1. JS逻辑，构造器
	* new一个vue实例
	* 参数列表：
		1. 绑定的元素
		2. 绑定的数据
		3. 		

```
	var app = new Vue({
		el: "#app",
		data: {
			message:"这是一个信息"
		}
	});
```

2. 判断:
	* 绑定v- + 判断语法if

```
	<div id="app1" >
		<p v-if="seen">{{ message }}</p>
	</div>
	
	var app1 = new Vue({
		el: "#app1",
		data: {
			message: "APP1的message",
			seen:false
		}
	});
	
```


3. 循环
		* 循环体必须是app元素的子元素，app标记元素不能循环。
		* 循环的参数是一个数组，也可以是一个对象.如果是数组，todo是每一项的值；如果是对象，todo是每一项的键值；如果是数组对象，使用todo.name返回值，其中todo是数组中项，name是对象中属性名

```
	<div id="app4">
		<div v-for="todo in todos">{{todo}}</div>
	</div>	
	
	var app4 = new Vue({
		el:"#app4",
		data:{
			todos:[
				{text:"name"},
				{text:"sex"},
				{text:"weight"}
			]
		}
	})
	
```
修改数组和字符串使用一般的数组字符串方法即可。

4. 事件监听v-on,事件名称v-on参数，所有的事件写在实例中的methods属性中；所有的this指向当前的app实例。
特征：数据驱动视图：没有操作dom，改变了dom的内容，js直接改变变量。

```
	/* 点击按钮改变指定dom文案 */
	<div id="app5">
		<p>{{data}}</p>
		<button v-on:click="change">点击变换文字</button>
	</div>
	
	
	
	var app5 = new Vue({
		el:"#app5",
		data: {
			data:点击之前,
			data1:"点击之后，我的文本变化了"
		},
		methods:{
			change:function(){
				this.data = this.data1;
			}
		}
	})

```

5. v-model指令的双向绑定。
V-model：当前元素的返回值,只支持表单元素，不支持div、p等元素。

```
	<div id="app6">
		<p>{{ message }}</p>
		<p v-model="message"></p>
	</div>

	var app6 = new Vue({
		el:"#app6",
		data:{
			message:"这是啥"
		}
		})
```
6. 组件定义
	* 组件名称不能有大写字母，和驼峰式命名违背，咋想的。
	* 接受参数props

```
Vue.component("mycom",{
	props:"val",
	template:"<div>这是模板内容</div>"
})

```

7. 组件使用：
	* 先注册组件Vue.component。模板结构，props组件使用的数据
	* 组件的使用和app除了在数据上，其他地方并没有耦合。
	* props接受什么参数，需要引用组件的标签上绑定响应的数据名

```
	<div id="app7">
		<ol>
			<mycom v-for="todo in todos1" v-bind:item="todo"></mycom>
		</ol>
	</div>


	/* 组件注册 */
	Vue.component("mycom", {
	    props:["todo","todo1"],
	    template:"<div>{{ todo1.text }}</div>"
	})

	var app7 = new Vue({
    el:"#app7",
    data:{
        todos:[1,2,3,4,5,6],
        todos1:[
            { "text": '蔬菜' },
            { "text": '奶酪' },
            { "text": '随便其他什么人吃的东西' }
        ]
    }
})
```
但是这段代码会报worning，但是能正常输出。：

```

[Vue tip]: <mycom v-for="item in todos1">: component lists rendered with v-for should have explicit keys. See https://vuejs.org/guide/list.html#key for more info.

(found in <Root>)

```
组件list使用v-for渲染必须有明确的key。应该是渲染组件的时候，for循环中的每一项呗自身引用，造成还未声明，在mycom组件外嵌套一层<templat>循环子项的父级元素可以解决报错：


```
	<div id="app7">
        <template v-for="item in todos1">
        <mycom  v-bind:todo = "item"  v-bind:todo1 = "item">11</mycom>
        </template>
    </div>

```
js不变。不清楚官网这是在做什么？可能是为了更好的让新人上手吧。

























