# CLRS中的算法收纳袋
受学习进度所迫，目前所有的函数均用伪代码写成，之后会修炼python重新编写。

## Linked list

### [Search](https://hyp.is/SbA1FkeyEeyRTRsbHjGWMw/web.iiit.ac.in/~pratik.kamble/storage/Algorithms/Cormen_Algorithms_3rd.pdf)

Use a simple linear search though the list.

``` python
def LIST_SEARCH(L,k):
    x = L.head
    while x != None and x.key != k:
        x = x.next
    return x
```

Worst-case complexity: $\Theta(n)$

### [Insert](https://hyp.is/ozeYmkeyEeyXa3v3eZiSFA/web.iiit.ac.in/~pratik.kamble/storage/Algorithms/Cormen_Algorithms_3rd.pdf)

Insert an element $x$ into the head of the list with the value of $key$.

```python
def LIST_INSERT(L,x):
    x.next = L.head
    if L.head != None
        L.head.prev = x
    L.head = x
    x.prev = NIL
```
L.head.prev denotes the prev attribute of the object that L.head points to.

Complexity: \(O(1)\)

### [Delete](https://hyp.is/yrOIrEeyEeyqkSP1cUixOw/web.iiit.ac.in/~pratik.kamble/storage/Algorithms/Cormen_Algorithms_3rd.pdf)

```python
def LIST_DELETE(L,x):
    if x.prev != None:
        x.prev.next = x.next
    else L.head = x.next
    if x.next != None:
        x.next.prev = x.prev
```

LIST-DELETE runs in \(O(1)\) time, but if we wish to delete an element with a given key, \(\Theta(n)\) time is required in the worst case because we must **first call LIST-SEARCH to find the element**.

### With sentinel
![](https://i.bmp.ovh/imgs/2021/11/a1a038fcd21fb5b6.png)

```python
def LIST_SEARCH_WITH_SENTINEL(L,x):
    x.next = L.nil.next
    while x != L.nil and x.key != k:
        x = x.next
    return x
```

```python
def LIST_INSERT_WITH_SENTINEL(L,x):
    x.next = L.nil.next
    L.nil.next.prev = x
    L.nil.next = x
    x.prev = L.nil
```
In this book, we use sentinels only when they truly simplify the code.

