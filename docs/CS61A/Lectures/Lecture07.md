*[[Lectures]]*
# Function Expamples
[[2022-02-01]]

---
## Implementing a Function

写一个去数字的函数，传入n和digit，去除掉n中所有的digit：
```python
def remove(n,digit):
    kept,digits = 0,0
    while n>0:
        n,last= n//10 , n%10
        if last != digit:
            kept = kept/10 + last
            digits+=1
    return round(kept*10**(digits-1))
print(remove(231,3))
```
从右向左取数，所以从右到左构造
新数要在旧数左边，可以`kept/10` 。
或者
```python
			kept = kept + last*10**digits
	return kept//10
```

---
## Decorators
