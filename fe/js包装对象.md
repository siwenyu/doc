# js包装对象

js有六中基本数据类型：null，undefined，number，string，Boolean，object。

其中null和undefined都`可以看做`是自有类型，number，string，Boolean是值类型，object是复杂类型。

看代码：

```
var s1 = "string";	//第一种声明方法
s1.length
6	

var s1 = "string";
s1.name = "s1";
s1.name
undefined

```

* 第一个问题：除object类型之外的基本类型不是对象，为什么会有属性？

* 第二个问题：s1.name为什么undefined。



其实在声明s1的时候，执行的是`var s1 = new String("string")`，这样就生成了一个字符串对象，字符串对象有自己的属性和方法。那么为什么s1.name是undefined呢？测试：

```
var s1 = new String("string");	//第二种声明方法
s1.name = "s1";
s1.name

"s1"

var o1 = new Number(1);
var o2 = 1;
o1
o2

object
number
```

s1是可以输出的，大概可以想到这两种声明方法还是有区别的。

结论：两种生命方法都可以创建一个字符串对象，第一种是隐式创建，只有第二种是真实创建，隐式创建的对象有改数据类型的基本属性和方法，但是亲生的和领养的还是有区别的，隐式创建的对象执行`s1.name`只是临时添加了属性，此语句执行之后会立即销毁。

这种现象在三种值类型的基本数据类型中都存在。
