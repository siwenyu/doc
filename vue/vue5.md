# vue学习笔记--class与style(5)

模拟addClass，removeClass，js动态写样式属性。

class命名不能使用-

2. 添加普通class与普通方式一样
3. 根据变量动态切换class：

```
	<style>
    .vue_active {
        color: #38f;
    }
    </style>
    
    <div id="app1" v-bind:class="{ vue_active:active }">
    	<div>{{ name }}</div>
	</div>

	var vm1 = new Vue({
    el: "#app1",
    data: {
        name:"我的名字",
        active: true
    }
})

// 生成的dom结构：
	<div id="app1" class="vue_active"><div>我的名字</div></div>
	
	
	控制台输入：
	vm1.active = false

// 生成的dom结构	：

	<div id="app1" class=""><div>我的名字</div></div>
```

4. 绑定一个对象，动态添加多个class

```
	<div v-bind:class="classObject"></div>
	
	
	data: {
  	classObject: {
    	active: true,
    	'text-danger': false
  		}
	}
	
```

5. 综合以上两种，可以结合computed使用，computed用来保存变量的结果，并以计算属性的形式返回。

```

	<div id="app1" v-bind:class="classOb">
    	<div>{{ name }}</div>
	</div>
	
	
	var vm1 = new Vue({
    el: "#app1",
    data: {
        name:"我的名字",
        active: true
    },
    computed:{
        classOb:function(){
            return {
                vue_active : true,
                vue_border : true
            }
            
        }
    }
})
```

6. 数组语法：v-bind:class接受一个数组

```
	<div v-bind:class="[activeClass, errorClass]">
	
	// 三元表达式
	
	<div v-bind:class="[isActive ? activeClass : '', errorClass]">
	
	
	
	<div id="app2" v-bind:class="[vue_active, border]">
    	<div>{{ name }}</div>
	</div>
	
	<div id="app2" v-bind:class='[active ? vue_active : "", border]'>
    	<div>{{ name }}</div>
	</div>
	
	var vm2 = new Vue({
    el: "#app2",
    data: {
        name:"我的名字",
        active: true,
        vue_active : "vue_active",
        border : "border"
    }
        
})
	
```
7. 内联样式：v-bind:style，非常像原生的css，但是是js渲染的，所以属性名使用驼峰式命名方法

```
	<div id="app3" class="classOb" v-bind:style="{color:'red'}">
    	<div>{{ name }}</div>
	</div>
	
```

v-bind:style接受一个对象：

```
	<div id="app4" class="classOb" v-bind:style="styleOb">
    	<div>{{ name }}</div>
	</div>
	
	
	styleOb:{
            color:"red",
            lineHeight:'30px'
        }
```

8. vue会添加css属性前缀，只添加三个

浏览器私有前缀包括Firefox 的 -moz-，IE的 -ms-，Safari 和 Chrome 的 -webkit-。
 























