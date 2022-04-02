[[Lectures]]

2021.12.21

这节开始看比较新的版本：Fall 2021

---

## Print and None

^faeb3e

[link](https://www.youtube.com/watch?v=jNYc5Gdwo3c&list=PL6BsET-8jgYWpnJAjl-O8v-xfp5Vf3zkS&index=2)

![](../../CS61A.assets/13.png)

![](../../CS61A.assets/14.png)

函数分为：

* Pure Functions: 
  
    只通过计算返回一个值

* Non-Pure Functions： 
        
    不返回值但是可能会做一些别的事情，比如`print()`是一个函数，它不输出任何值，但是会打印出来参数，所以会发生如下的事情：

    ![](../../CS61A.assets/15.png)

    Expression tree 如下：

    ![](../../CS61A.assets/16.png)

---

## Multiple Environments

[Vedio link](https://www.youtube.com/watch?v=IPec2A7j2bY&list=PL6BsET-8jgYWpnJAjl-O8v-xfp5Vf3zkS&index=3)

讲实话这节的长难句有点多，逻辑比较复杂，没有特别搞明白讲了什么，，，

然后去看了课本([1.3.1   Environments](http://composingprograms.com/pages/13-defining-new-functions.html#environments)
)，里面的介绍会比较详细而且不用担心长难句听不懂哈哈哈。
这里放几个我认为比较重要的概念和python tutor作为演示。

1. **Intrinsic name & Bound name of a function**

    <iframe width="800" height="300" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=f%20%3D%20max%0Amax%20%3D%203%0Aresult%20%3D%20f%282,%203,%204%29%0Amax%281,%202%29%20%20%23%20Causes%20an%20error&codeDivHeight=400&codeDivWidth=350&cumulative=true&curInstr=0&origin=composingprograms.js&py=3&rawInputLstJSON=%5B%5D"> </iframe>
    >The name of a function is repeated twice, once in the frame and again as part of the function itself. The name appearing in the function is called the intrinsic name. The name in a frame is a bound name. There is a difference between the two: different names may refer to the same function, but that function itself has only one intrinsic name.

    函数有两种名字：Intrinsic name & Bound name。

    在Diagram中左侧的是bound name，右侧是intrinsic name，左侧的名字是你可以改变的，比如你叫你的手机叫傻妞，但是实际上只是傻妞这个名称指向了这个唯一的设备。本质名还是那个唯一的标识码。

    演示中： 一旦`max`被bound到数值3，它就不能再作为函数使用。

2. Calling a User-Defined Function
   
    <iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=from%20operator%20import%20add,%20mul%0Adef%20square%28x%29%3A%0A%20%20%20%20return%20mul%28x,%20x%29%0A%0Adef%20sum_squares%28x,%20y%29%3A%0A%20%20%20%20return%20add%28square%28x%29,%20square%28y%29%29%0A%0Aresult%20%3D%20sum_squares%285,%2012%29&codeDivHeight=400&codeDivWidth=350&cumulative=true&curInstr=0&origin=composingprograms.js&py=3&rawInputLstJSON=%5B%5D"> </iframe>

    [[使用自建函数]]会:
	
（1）创建出一个新的子框架，称为local frame，形同global frame

（2）首先会把传入的数值和对应的形参绑定

（3）其次会使用这些形参执行函数体

* 当函数体执行时，需要用到某变量，先在当前的框架（local frame）中搜索，没有的话再去母frame（global frame）找。

---

## Miscellaneous Python Features

[[Docstring]]: def行下用于解释函数用途的语句

![[Pasted image 20220119132522.png]]

也可以这样测试样例[[Doctest]]

![[Pasted image 20220119133710.png]]


#### Operator
```python
>>>import operator
>>>truediv(2022,10)
#真除法 等价于2022/10
202.2
>>>floordiv(2022,10)
#整除 等价于2022//10
202
>>>mod(2022,10)
#取余（取模） 等同于2022 % 10
3
```

 ### [[Placeholder]]
形参可以写一个占位符，在调用时如果没有给其赋值则传入占位符的值

 ![[Pasted image 20220119134248.png]]


---

## Conditional statements

[Conditional statements - YouTube](https://www.youtube.com/watch?v=dijoBZH44kU&list=PL6BsET-8jgYWpnJAjl-O8v-xfp5Vf3zkS&index=5)

### [[Statements]]
![[Pasted image 20220119134902.png]]

![[Pasted image 20220119135255.png]]


### [[Conditional statements]]
其实没什么太多没见识过的知识，，，

![[Pasted image 20220119135643.png]]

![[Pasted image 20220119140550.png]]

---

### [[George boole]]


![[Pasted image 20220119140652.png]]
>布尔正在认真审视你的表达式是真是假  ：P

**False values** in Python: False,0, ""，None (more to come)

**True values** in Python: Anything else (True)

---

## [[Iteration]]

[[While]]

没什么内容，略

## Example: Prime Factorization

素因数分解，或因数分解

有时候把所有的功能用一个函数写完，可读性会比较差，不如把函数更加原子化，每个函数各司其职，可读性较高的同时还可以更易于编程时整理思维。

#Dijkstra  说过： 
>- 最聪明的程序员永远能意识到自己头脑的有限性，因此他们会充分谦卑的的对待自己的任务，并且避免那些看似聪明的技巧 。
>-   通往天才的最佳途径是：让问题比你的脑容量小。

[[最聪明的程序员……]]