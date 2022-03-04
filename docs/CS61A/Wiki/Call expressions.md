[[Wiki]]

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