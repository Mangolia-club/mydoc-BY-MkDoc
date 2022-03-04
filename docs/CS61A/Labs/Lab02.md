[[Labs]]

2002-01-02

---
[Lab 2: Higher-Order Functions, Lambda Expressions | CS 61A Fall 2021 (berkeley.edu)](https://inst.eecs.berkeley.edu/~cs61a/fa21/lab/lab02/)

### Q3: Lambdas and Currying

Write a function `lambda_curry2` that will curry any two argument function using lambdas. Refer to the [textbook](http://composingprograms.com/pages/16-higher-order-functions.html#currying) for more details about currying.

[[柯里化]]一个函数。

一开始是这么写的但是没有过syntax check，显示多返回了一个函数项：
```python	 
def lambda_curry2(func):
    def f(x):
        def g(y):
            return func(x,y)
        return g
    return f

Error: expected
	['Expr', 'Return']
 but got
	['Expr', 'FunctionDef', 'Return']
```

网上查阅了别人的答案：[cs61a-lab02 | Hexo (giancarlo-ma.github.io)](https://giancarlo-ma.github.io/2018/08/29/cs61a-lab02/)

使用[[Lambda Expressions]]避免了return函数：
```python
def lambda_curry2(func):
    return lambda x: lambda y: func(x, y)
```

而且更加整洁，多多学习。

### Q4: Count van Count

Consider the following implementations of `count_factors` and `count_primes`:

即是将两个函数体类似的函数合一，将判定条件转变为合函数的参数。

```python
def count_cond(condition):
    """Returns a function with one parameter N that counts all the numbers from
    1 to N that satisfy the two-argument predicate function Condition, where
    the first argument for Condition is N and the second argument is the
    number from 1 to N.

    >>> count_factors = count_cond(lambda n, i: n % i == 0)
    >>> count_factors(2)   # 1, 2
    2
    >>> count_factors(4)   # 1, 2, 4
    3
    >>> count_factors(12)  # 1, 2, 3, 4, 6, 12
    6

    >>> is_prime = lambda n, i: count_factors(i) == 2
    >>> count_primes = count_cond(is_prime)
    >>> count_primes(2)    # 2
    1
    >>> count_primes(3)    # 2, 3
    2
    >>> count_primes(4)    # 2, 3
    2
    >>> count_primes(5)    # 2, 3, 5
    3
    >>> count_primes(20)   # 2, 3, 5, 7, 11, 13, 17, 19
    8
    """
    def f(n):
        i = 1
        count = 0
        while i <= n:
            if condition(n,i):
                count += 1
            i += 1
        return count
    return f
```

![[Pasted image 20220201131945.png]]