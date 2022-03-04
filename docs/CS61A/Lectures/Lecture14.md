---

mindmap-plugin: basic

---

# Mutability
[[2022-02-27]]
[[Lectures]]

---
## Objects
![[Pasted image 20220302150308.png]]

---
## Example: Strings
介绍了 ASCII和Unicode

---
## Mutation Operations
![[Pasted image 20220302151634.png]]
![[Pasted image 20220302151714.png]]

Functions can change the value of any object in its scope.

即改变一个对象的内容，不会因为有别的名字bound在上面而留存：

我不管怎么变从小到大都是叫这个名字，这个名字指向我这个人，不管我是变成了渣男还是方丈。

而别人叫我外号，随着我改变，叫我外号不等于叫之前的我而是现在的我。

在函数中对对象造成改变亦是如此。

---
## Tuples
即[[元组]]。不可以mutation的值[[Python]]


---

定义一个元组：

![[Pasted image 20220302152352.png]]

- 元组可以被用作字典的key

---
## Mutation
![[Pasted image 20220302155136.png]]

### Identity
`<exp0> is <exp1>`

返回`True`如果两者被bound到一个对象。
而`==`返回的是两者的值的比较，即使不是一个对象。

---
## Mutable Functions
 





