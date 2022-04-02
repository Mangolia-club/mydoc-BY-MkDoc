*[[Lectures]]*
# Tree recursion
[[2022-02-08]]

---
## Order of Recursive Calls
用如下的例子讲解了递归调用的顺序，ez
<iframe width="800" height="400" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20cascade%28n%29%3A%0A%20%20%20%20if%20n%20%3C%2010%3A%0A%20%20%20%20%20%20%20%20print%28n%29%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20print%28n%29%0A%20%20%20%20%20%20%20%20cascade%28n//10%29%0A%20%20%20%20%20%20%20%20print%28n%29%0A%0Acascade%28123%29&codeDivHeight=400&codeDivWidth=350&cumulative=true&curInstr=0&origin=composingprograms.js&py=3&rawInputLstJSON=%5B%5D"> </iframe>

**其Frame像链条一样，后调用的链在先套用的后面。**

因为在line 3和line 5里`print`调用了两次
可以简化为如下：
```python
def cascade(n):
	print(n)
	if n >= 10:
		cascade(n//10)
		print(n)
```

这样更加简洁，但是上面的结构更加典型：有对base case 的处理

---
## Example: Inverse Cascade
![[Pasted image 20220209184644.png]]

```python
grow=lambda n: f_then_g(grow,print,n//10)
shrink=lambda n: f_then_g(print,shrink,n//10)
```

两个的区别是先输出还是先递归调用。

---
## Tree [[Recursion]]
>每次的递归调用大于1个的递归

常用于可以将大问题一分为多的递归调用。
理解算导里面的Recursion Tree和计算递归式。

递归树的调用顺序多为先序遍历。
![[Pasted image 20220209190330.png]]
### Trace
在ucb文件里提供的函数trace，可以跟踪在递归调用时的函数调用顺序（IDE里步进也行）
用法：
```python
from ucb import trace

@trace
def function():
	...
	...
```

![[Pasted image 20220209191026.png]]

### Repetition
有时候会有许多重复调用，在之后的学习中会学习如何通过记住之前的结果减少重复计算。

---
## Example: Counting Partitions
![[Pasted image 20220209191424.png]]
![[Pasted image 20220209192104.png]]
![[Pasted image 20220209192122.png]]
