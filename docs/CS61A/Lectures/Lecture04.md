[[Lectures]]

2022.1.21

---

## [[Iteration]] Example

**[61A Fall 2016 Lecture 4 Video 2 - YouTube](https://www.youtube.com/watch?v=pveIuZT0GJE&list=PL6BsET-8jgYWpp0J7kXl4jaLpdTL2FTeg&index=2)**

### The [[Fibonacci]] Sequence

![[Pasted image 20220121192601.png]]

图为斐波那契和他的头巾的合影


![[Pasted image 20220121192735.png]]

斐波那契螺线 

```python
def fib(n):
	'''Compute the nth Fibonacci number?'''
	pred,curr = 0,1
	k=1
	while k < n :
		pred,curr = curr,pred + curr
		k = k + 1
	return curr
```

上面这个代码可以实现第1~n的斐波那契数输出，但是第零个也就是0无法输出。

据此改进代码，可以按照当前算法**向前推一轮loop**：

即从：
```python
	...
	pred,curr = 0,1
	k=1
	...
```
变到：
```python
	...
	pred,curr = 1,0
	k=0
	...
```
传入n=0，while循环不会进入，直接输出curr，也就是0。

缺点：输出>0的数会比改进前多走一次循环，加大时间开销（几乎可以忽略）。

---

## Designing Functions

**[61A Fall 2014 Lecture 4 Video 3 - YouTube](https://www.youtube.com/watch?v=FzbVzGnVBB4&list=PL6BsET-8jgYWpp0J7kXl4jaLpdTL2FTeg&index=3)**

- **函数化**-->
	- 使程序看起来更加通顺， 
	- 减少编程时的工作量，
	- 减少程序员头发的消耗量。

- 定义域(Domain)：输入的参数的集合
- 值域(Range)：输出的值的集合

函数的一些准则：
- 每个函数一个具体的功能（原子化）
- 每次只执行一次，通过调用次数调整执行次数（不自循环）
- 通用化函数，电源插头,no（制式多样）；USB, yes。

---

## Higher-Order Functions

**[61A Fall 2013 Lecture 4 Video 4 - YouTube](https://www.youtube.com/watch?v=UlXvz-34Me0&list=PL6BsET-8jgYWpp0J7kXl4jaLpdTL2FTeg&index=4)**

### assert

![[assert]]

**高阶函数**：可以将其他函数作为参数或者返回结果。

Generalization 一些在不同的函数中相同的步骤，将其做成另一个函数，只需调用这个函数即可，无需在每个函数中重复编写。

![[Pasted image 20220122164918.png]]

---

## Lambda Expressions


**[61A Fall 2014 Lecture 6 Video 2 - YouTube](https://www.youtube.com/watch?v=vCeNq_P3akI&list=PL6BsET-8jgYWpp0J7kXl4jaLpdTL2FTeg&index=6)**

![[Lambda Expressions]]

![[Pasted image 20220122173552.png]]

---

## Control Expressions

### Logical Operators

![[Boolean Operators#^logic-expressions]]


基本上就是[[Lab01]]里的[[Boolean Operators]]，tnnd怎么现在才讲。应该是John把视频顺序弄错了，，

```python
def has_big_sqrt(x):
	return x > 0 and sqrt(x) > 10

def reasonablr(n):
		return n == 0 or 1/n != 0
```

上例展示了`and`和`or`的不一样的用法：**限制或者扩展函数的定义域**。

### Conditional Expressions

A conditional expression has the form:

```python
<consequent> if <predicate> else <alternative>
```

like:
```python
abs(1/x if x !=0 else 0)
```

等价于：

```python
if <predicate>:
	<consequent>
else:
	<alternative>
```


---