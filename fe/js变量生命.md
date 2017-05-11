# js变量声明

1.声明全局变量

```
	var valueA = 'valueA';
	console.log(valueA);
	console.log(window.valueA);
	
	valueA	//全局变量
 	undefined	
```
2.隐式声明全局变量

```
	valueB = 'valueB';
	console.log(valueB);
	console.log(window.valueB);
	
	valueB	//作为window的属性存在
	valueB
```

3.函数内部声明局部变量

```
	function f1(){
		var f1A = 'f1A';
	}
	f1();
	console.log(window.f1A);
	
	undefined	//局部变量
	
	var oA = new f1();
	console.log(oA.f1A);
	
	undefined	//并没有作为任何对象的属性，只是一个局部变量
	
```
4.函数内部隐式声明变量

```
	function f1(){
		f1A = 'f1A';
	}
	f1();
	console.log(f1A);
	console.log(window.f1A);
	
	
	f1A
	f1A		//全局的属性
```

显式声明的变量是一个变量，而隐式声明的变量是一个全局对象window的属性。
在正常的开发和使用中，一般这两种变量是没有区别的，但是他们本身是有区别的：

5.两种存在的区别

```
		var valueA = 'valueA';
		console.log(valueA);

		valueB = 'valueB';
		console.log(valueB);

		delete valueA;
		delete valueB;
		
		console.log(valueA);
		console.log(valueB);
		
		
		valueA
	 	valueB
 		valueA
		valueB is not defined	//全局对象的属性存在被删除了
    		
```

结论：隐式声明的变量会转换成全局对象的属性，属性是可以被删除的。显式声明的变量是不会被删除的。