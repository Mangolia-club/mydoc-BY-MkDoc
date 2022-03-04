---

mindmap-plugin: basic

---
# Containers
[[2022-02-10]]
*[[Lectures]]* *[[Python]]*
进入了二位数的课数 (#￣▽￣#)


---
## Lists
第一次系统的学list \(≧▽≦)/

`list[i]`等价于`getitem(list,i)`

<!-- basicblock-start oid="ObsJhM1rXc3jpyLd2QZg6Aau" deck='python' -->
**列表的每一个元素也可以是一个列表**

::

 Nested lists
```python
>>>pairs= [[10,20],[30,40]]
>>>pair[1]
[30,40]
>>>pair[1][0]
>>>30
```
<!-- basicblock-end -->

---
## Containers
```python
>>>digits = [1,8,2,8]
>>>1 in digits
True
>>>'1' in digits
False
#since '1' != 1
>>>[1,2] in [3,[1,2],4]
True
>>>[1,2] in [3,[[1,2]],4]
False
```
以上，in可以用于检查某个数据是否在列表中，但是仅仅只是逐元素的检查，遇到第一个相等则返回`True`。

---
## [[For]] Statements
![[Pasted image 20220210153749.png]]

### **Sequnce Unpacking**
```python
>>>pairs = [[1,2],[2,2],[3,2],[4,4]]
>>>same_count = 0
>>>for x, y in pairs:
...    if x == y: 
...	        same_count = same_count + 1
>>> same_count
2
```
x,y被分别以pair中的每个元素赋值，即变的是pair的角标。

可以这样理解：
```python
x,y = pair[0]
x,y = [1,2]
x,y = 1,2
```

---
## Range
```python
>>>range(-2,2)
range(-2,2)
>>>list(range(-2,2))
[-2,-1,0,1]
```
即是一个左闭右开的区间，取包围在其中的数作为元素的序列，用`list()`可以转换为列表

- len(range(-2,2))等于2-(-2)=4
	即range 的元素个数等于右值减左值\
- range(n)--->range(0,n)--->[0,1,2,...,n-1]

---
## List Comprehensions
```python
>>>odds =[1, 3, 5, 7, 9]
>>>[x+1 for x in odds]
[2，4，6，8，10]
>>> [x for x in odds if 25 % x == 0]
[1,5]
```
 看起来是一个很有用的东西，但是我对字符串的了解较少（不像John DeNero）。

---
## String
String也是一种list不过和一般的序列略有不同。
```python
>>>city = 'Berkeley'
>>>len(city)
8
>>>city[3]
'k'
>>>'here' in "Where's Waldo?"
True
```
在list中只能一个个匹配，但是string可以连着匹配。

---