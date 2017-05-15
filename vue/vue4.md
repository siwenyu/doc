# vue学习笔记--计算属性(4)

1. 什么是计算属性？属性需要被计算，恩，是的。在模板中可以进行简单的计算，比如+1，但是不合适进行大量的计算，维护困难，这也不符合逻辑模板分离的思想。

比如，进行字符串反转：

```
	<div id="example">
		<p>Original message: "{{ message }}"</p>
		<p>Computed reversed message: "{{ reversedMessage }}"</p>
	</div>

	可以这么写：
	
	<div id="example">
		<p>Original message: "{{ message }}"</p>
		<p>Computed reversed message: "{{ message.split('').reverse().join('') }}"</p>
	</div>
	
	
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
    html: "<p style='color:red;'>这是插入的html</p>",
    message: "hello"
}

var vm1 = new Vue({
    el: "#app1",
    data: data
})

	
```

2. 计算


```
	var vm2 = new Vue({
    el: "#app2",
    data: data,
    computed: {
        reverseMessage: function () {
                return this.message.split('').reverse().join('')
            }
    }
})	
	
```

cumputed用来声明计算属性，此中所有的变量都被汲监测。


3. 想一下methods属性，也有这个功能。

```
	<div id="app2">
        <p>Original message: {{ message }}</p>
        <p>Computed reversed message: {{ reverseMessage() }}</p>
    </div>


	var vm2 = new Vue({
    el: "#app2",
    data: data,
    methods: {
        reverseMessage: function () {
                return this.message.split('').reverse().join('')
            }
    }
})

	控制台输出：
	vm3.now
	1494830264031
	vm3.now
	1494830264031
	vm3.now
	1494830264031
	
```
以上可以看出
	* computed中的属性是在内部计算的，是被缓存的变量，只要检测依赖的变量不发生变化，就不会重新返回。而method中的方法返回值，在每次调用方法的时候都会重新返回。
	
4. watch属性与computed比较

computed:

```
 computed: {
    fullName: function () {
      return this.firstName + ' ' + this.lastName
    }
  }
```

watch：

```
	watch: {
    firstName: function (val) {
      this.fullName = val + ' ' + this.lastName
    },
    lastName: function (val) {
      this.fullName = this.firstName + ' ' + val
    }
  }
```

那什么时候用watch什么时候使用computed呢 ？？

5. watch

响应数据的变化：更混乱了。官方的例子是异步的时候使用watch。