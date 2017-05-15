# vue学习笔记---实例和生命周期（2）

1. 构造器

```
var vm = new Vue(name,{
	
})
```
vm是MVVM中 viewmodel的缩写，寓意使用mvvm设计模式。
	* 第一个参数是实例名称
	* 第二个参数是一个对象选项，包括挂载元素，数据，方法，模板，生命周期等。


2. 属性和方法 

所有的vue实例中的对象选项属性都被vue实例代理，只有在实例化的时候已经写入的选项。

```
var data1 = {
        maessage:"消息"
    };  
var vm = new Vue({
    el:"#app1",
    data:data1
})

var a = vm.maessage == data1.maessage;
console.log(vm.maessage);
console.log(data1.maessage);
console.log(a);

```

此外，所有的vue实例有一些公用的实例属性和方法，这些方法和实例使用$前缀，和代理的data属性区分:

```
var data1 = {
        maessage:"消息"
    };  
var vm = new Vue({
    el:"#app1",
    data:data1
})

console.log(1,vm.$data);
console.log(1,vm.$el);
console.log(1,vm.$watch);
```

3. 生命周期
	* 组件的生命周期就是 created，init，destroy等
	* vue实例被初始化的过程中，实例需要配置数据观测，模板编译，挂载实例到dom，数据更新时更新dom。在这个过程中，会有一些过程向外抛出一些钩子，可以让我们自定义事件的发生。比如created。
	* 其他的
	
```
	<div id="app2"></div>
	
	
	var vm2 = new Vue({
		el:"#app2",
		data:{
			todos:[{name:1},{name:2},{"name3":3}]
		},
		created:function(){
			console.log(this + "is be created");
		}
	})
```
<img src="https://raw.githubusercontent.com/siwenyu/doc/master/img/vueLife.png" width="500px">

如图所示：
	* 初始化实例 ->（'beforeCreate'）->  检测数据 -> 初始化事件 -> ('created') -> el？挂载 ->  template？编译 -> （beforeMount）-> 创建实例自身方法 -> (mounted) -> mounted：(beforeUpdate):渲染:(updated) -> (beforeDestroy) -> tearDown监听，子组件 -> destroyed -> (destroyed)
	* 上面的工程中，()内是抛出的事件钩子，其他是vue实例的生命周期过程。









