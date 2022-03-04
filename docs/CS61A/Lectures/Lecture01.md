[[Lectures]]

2021.12.18

---

## **About the course**

<iframe width="560" height="315" src="https://www.youtube.com/embed/R--ROH7wOIw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

![](../../CS61A.assets/image-20211218180346821.png)

---

## **An Introduction to Computer Science**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CK4xrHi-IrQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* What is This Course About?
  * A course about managing complexity
    - **Mastering abstraction**（本课程最核心的目标）
    - Programming paradigms
    * "Not all about 0 's and 1 's
  - An introduction to Python
    - Full understanding of language fundamentals
    - Learning through implementation
    -How computers interpret programming languages
  - A challenging course that will demand a lot of you

> 本课程会学习python，但是不是仅仅讲述每个功能，而是深入到细节。

---

## **Expressions**

<iframe width="560" height="315" src="https://www.youtube.com/embed/0P4kOL7pFFo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### [[Call expressions]]

**组成**

![](docs/CS61A.assets/9.png)

is an expression that involves a function call.     [From CS61A Wiki.](https://www.ocf.berkeley.edu/~shidi/cs61a/wiki/Expression) 

```py
from operator import add, mul
add(mul(2, 3), 1)
7
``` 

1. evaluate operator of `add(mul(2, 3), 1)` and find that it is function add
2. evaluate operand `mul(2, 3)`
      1. evaluate operator `mul`and find that it is function $m u l$
      2. evaluate operand 2 (primitive)
      3. evaluate operand 3 (primitive)
      4. apply function `mul` to 2 and 3 , returns 6
3. evaluate operand 1 (primitive)
4. apply function add to 6 and 1 , returns 7

>即调用add累加函数，以及mul累乘函数，作用是将输入的参数依次做加和或者乘积，a sinple function right?

**Evaluation procedure for call expressions:**

1. Evaluate the operator and then the operand subexpressions
2. Apply the function that is the value of the operator subexpression to the arguments that are the values of the operand subexpression

**According to the evaluate procedure, evaluate nested expressions**

调用树（表达树）
![](docs/CS61A.assets/3.png)

---

### Functions, Objects, and Interpreters

用文本在python命令行中玩耍了一下, 没有什么太重要的内容。但是很有趣hh。

<iframe width="560" height="315" src="https://www.youtube.com/embed/2SopsFYlGr4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

之后还有Lab00：[link](http://localhost:8000/CS61A/Labs/Lab00/)