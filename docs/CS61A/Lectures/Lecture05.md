[[Lectures]]
2022.1.29

# Environments
---

## Environments for Higher-Order Functions

![[Self-defined function#^Call-a-self-defined-function]]^Call-a-self-defined-function

![[Pasted image 20220129165137.png]]

在外层返回的`f(f(x))`实际上还是代表着在global frame的`square(x)`，只是绑定的名字在local frame。

---

## Higher-Order Function Example: Repeat

介绍了一个简单的高阶函数作为示例，但是作为经历过hog考验的我来说可谓是简简单单，就不多啰嗦了，毕竟长路漫漫，而时间短短。

---

## Environments for Nested Definitions

Nested def:
<iframe width="800" height="300" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20make_adder%28n%29%3A%0A%20%20%20%20def%20adder%28k%29%3A%0A%20%20%20%20%20%20%20%20return%20k%20%2B%20n%0A%20%20%20%20return%20adder%0A%20%20%20%20%0Aadd_three%20%3D%20make_adder%283%29%0Aadd_three%284%29&codeDivHeight=400&codeDivWidth=350&cumulative=true&curInstr=0&origin=composingprograms.js&py=3&rawInputLstJSON=%5B%5D"> </iframe>


![[Pasted image 20220129171001.png]]

- 上图解释了为什么会有父框架是一个函数的函数：因为该函数是在父函数里定义并且作为返回值输出的。

框架结构是这样的：1-->2-->3

这样的结构中文叫做闭包：

![[Higher-order Functions#^closure]]

**总结**：
1.每一个自建函数都有一个父框架（通常是global frame） 
2.父框架即是该函数被定义的地方
3.每一个local frame都有父框架（通常是global frame）
4.框架的父框架是里面函数被调用的那个父框架
^6f9887
(有点绕弯，但是其实抽象上还是挺好理解的，差不多就是说每个人都有父辈，父辈就是定义你是谁谁孩子的地方，子辈都有父辈，子辈里面的人的父辈都是这个子辈的父辈）

 ![[Pasted image 20220129172901.png]]

 即是：
 ![[Self-defined function#^Define-a-self-defined-function]]
  ![[Self-defined function#^Call-a-self-defined-function]]

  ---

  ## [[Local Names]]

>  **局部变量对于别的函数来说是不可见的。** --John DeNero


---

## Function Composition

和hog里面的both类似，，没什么好说的、、

反正就是高阶函数弯弯绕绕，，

---

## Self-Reference
函数可以返回自己，所以也可以套娃！

```python
def print_all(x):
	print(x)
	return print_all

print_all(1)(3)(5)

#相当于以下函数：
print(1)
print(3)
print(5)

'''输出会是:
1
3
5
'''
```

---

## Function Currying

>在计算机科学中，柯里化（Currying）是把接受多个参数的函数变换成接受一个单一参数(最初函数的第一个参数)的函数，并且返回接受余下的参数且返回结果的新函数的技术。这个技术由 Christopher Strachey 以逻辑学家 Haskell Curry 命名的，尽管它是 Moses Schnfinkel 和 Gottlob Frege 发明的。
>--[柯里化_百度百科 (baidu.com)](https://baike.baidu.com/item/%E6%9F%AF%E9%87%8C%E5%8C%96/10350525)

即是将需要多个参数的函数转换成高阶函数，然后()()这样调用
也就是一次输一个参数，输出[[Higher-order Functions#^closure|闭包]]这个参数的函数。