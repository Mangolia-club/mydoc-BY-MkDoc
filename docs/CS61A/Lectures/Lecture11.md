---

mindmap-plugin: basic

---


# Lecture11
[[2022-02-12]]
[[Lectures]]

---
## Box-and-Pointer

介绍了一种用矩形表示一个列表的元素，挨着的矩形连起来表示一个列表，左上角是它的角标。
![[Pasted image 20220212182704.png]]

---
## [[Slicing]]
```python
>>>odds = [1,3,5,7,9]
>>>odds[1:3]
[5,7]
```
切片，这里的例子都蛮好理解的。

---
## Processing Container Values
讲了几个用于处理序列的内建函数

### sum
`sum(iterable[, start]) -> value`
Return the sum of an [[Iterable]] of numbers (NOT strings) plus the value of parameter 'start' (which defaults to 0). when the iterable is
empty, return start.

即是：`sum`可以接收一些可迭代的数据，然后从`start`开始加。
![[Pasted image 20220212183719.png]]

### max

`max( iterable[ , key=func] ) -> valuemax(a, b, c, ...[, key=func] ) -> value`
With a single iterable argument,return its largest item.
With two or more arguments,return the largest argument.

即是`max`有两个参数，一个是传入数据，一个是`key function`，默认情况下返回传入数据中最大的，`key=<func>`的情况下返回将传入数据带入到`<func>`时最大的结果。

或者也可以直接记：**`max`返回某传入函数在传入数据里的最大值，即传入数据作为定义域下的值域的最大值。**

### all
`all(iterable) -> bool`
Return True if bool(x) is True for all values x in the iterable.If the iterable is empty, return True.
即：**all true -> true**

	


