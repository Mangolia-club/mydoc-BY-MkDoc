---

mindmap-plugin: basic

---

# Data Abstraction
[[2022-02-16]]
[[Lectures]]

---
 ## P1: Data Abstraction

指一个复合的数据类型，将几个不同的部分组合起来。

比如日期之于年月日

![[Pasted image 20220216121519.png]]

- Data abstraction: A methodology by which functions enforce an abstraction barrier between ***representation*** and ***use***
	函数在表示和使用之间设置抽象屏障的一种方法

目前对我而言还是一个比较晦涩的概念，用一个例子展示：

### 表示有理数
任何有理数都可以表示为分数，即两个整数相除：
$$
\frac{\text{numerator}}{\text{denominator}}
$$
要将它完全的表示为小数（浮点数）必定会损失精度，比如1/3转化为0.33333，只要表示的循环在某一个地方断掉了，那就会造成精度损失，从而两者之间不再可以画等号。

**所以精确的表示有理数只能使用分数。**


定义几个函数：
```python
rational(n,d)返回有理数x
numer(x) 返回x的分子
denom(x) 返回x的分母

def mul_rational(x,y):
	return rational(numer(x) * numer(y),denom(x) * denom(y))

def add_rational(x,y):
	return rational(nx * dy + ny * dx,dx * dy)

def equal_rational(x,y):
	return numer(x) * demon(y) == numer(y) * denom(x)
```
具体的使用在下一节

---

## Representing Rational Numbers

### Pair
可以用自带的list来表示一对数：`list = [1,2]`
访问某一个值的时候可以用： `list[0]`

据此就可以完善之前没有完整定义的用于表示有理数的函数啦：
```python
def rational(n,d):
	'''返回有理数x'''
	return [n, d]

def numer(x):
	return x[0]

def denom(x):
	return x[1]
```

我们希望有理数的上下是一个最简的分数：

引入一个自带函数gcd(n,d)：返回两个数的最大公约数

现在改进一下刚刚的rational函数：
```python
from fractions import gcd
def rational(n,d):
	g = gcd(n,d)
	return [n//g, d//g]
```

---
## Abstraction Barrier
![[Pasted image 20220216214803.png]]
从上到下，其实现(implementation)逐渐从高级到基本。
想运用某层的功能只需要使用该层的函数，不可跨界，或者说**不用关心更底层的实现**。
比如说做做某几个有理数之间的运算并不需要我们的有理数是怎样实现的，是不是用两个整数来表示分数并不重要，更不需要知道他们是不是依赖list实现的。

使用某种数据结构的时候不需要知道其是如何实现的，更关注是如何运用的。

类似于 [[Dijkstra]] 说的：![[最聪明的程序员……#^e70bb3]]![[最聪明的程序员……#^798235]]

---
## Data Representation
[Data Representations - YouTube](https://www.youtube.com/watch?v=NgL6JsQNTPg&list=PL6BsET-8jgYXo1QlITc1kGVW3G7JCW-a9&index=5)

如果严格的遵照如上讲述的规则，每一层的实现不越界，那么可以这样做：

如果要修改某一层的实现，比如找到了更优异的算法，更适合的数据结构，此时无需更改其他层，只需要修改这一层的实现就可以。

太妙了！

具体例子看视频。

---
## Dictionaries
新数据结构：字典[[Dictionary]]

[Python 字典 (w3school.com.cn)](https://www.w3school.com.cn/python/python_dictionaries.asp)

![[Pasted image 20220216220226.png]]

 就像现实中的字典，有（索引）关键词有条目。
 一个关键词对应一个条目。

 不过Python里的字典有别的规矩：
 - key不能是列表或者字典这种可变类型
 - 两个key不能相等，一个key只对应一个值（但是这个值可以是列表）

### Dictionary Comprehensions
`{<key exp>:<value exp> for <name> in <iter exp> if <filter exp>}`

我超好长，不过原理和 [[Lecture10#List Comprehensions|List Comprehensions]] 差不多

 ![[Pasted image 20220216221655.png]]

 