# 常用的math方法总结

常用的math方法总结如下：

1. MAth.pow() 平方值

```
	Math.pow(2,53)
	9007199254740992
	Math.pow(2,1/2)
	1.4142135623730951

```

2.Math.round()  四舍五入

```
	Math.round(0.5);
	1
	Math.round(0.2);
	0
	Math.round(0.7);
	1
```

3.Math.ciel 向上取整

```
	Math.ceil(.3)
	1
```

3.Math.floor 向下取整

```
	Math.ceil(.3)
	0
```

4.Math.abs  绝对值

```
	Math.abs(0)
	0
	Math.abs(-10)
	10
	Math.abs(10)
	10
```

5.Math.min()  Math.max()  最大值最小值

```
	Math.max(2,3,4,0.3)
	4
	Math.max(2,3,4)
	4
	Math.min(0,0.1,-9)
	-9
```
求数组的最大值最小值：

```
	var arr1 = [2,3,4,5,6,7];
	Math.max.apply(null,arr1);
	7
	Math.min.apply(null,arr1);
	2

```

6.Math.random() 生成0<= x <1的随机数

```
	Math.random()
	0.1791025059457798
	Math.random()
	0.41003543142250143
	Math.random()
	0.7319803827364633

```

7.Math.sqrt() 平方根

```
	Math.sqrt(4)
	2
	Math.sqrt(-4)
	NaN
	Math.sqrt(44)
	6.6332495807108
```
8.(+-)Infinity 无穷大
9.NaN 代表非数字的特殊值

```
	var w;
    console.log(parseInt(w))
	NaN
	
```
isNaN() 来判断一个值是否是数值，是，返回false，不是返回true

```
	isNaN(2)
	false
	isNaN(NaN)
	true  //与它本身也不相等
	isNaN(parseInt("sads"))
	true
```

那么如何判断是不是NaN呢？
a是NaN，是一个不是数值的特殊值，两个特殊值不相等。

```
var a = parseInt("sada");
a != a
true
```

10.0，-0，+0 正0和负0是完全相等的，除了作为除数之外。

```

console.log(0==-0);
console.log(0===-0);
console.log(0!=0);

true
true
false
//作为除数
2/0
Infinity
2/-0
-Infinity
```

11.小数的大小比较要慎重，整数可以进行比较。所有的基于二进制的计算方法都有这个问题。原因是小数部分表示成二进制精确不准确。比如：0.1表示成二进制：0.00011001100110011001100110011001...。所以《权威指南》建议用大整数进行重要的数值计算，避免设计小数。