[[Labs]]

### Lab 00: Getting Started

[link](https://inst.eecs.berkeley.edu/~cs61a/su20/lab/lab00/)

Come up with the most creative expression that evaluates to 2020,
using only numbers and the +, *, and - operators.

```py
def twenty_twenty():
    """Come up with the most creative expression that evaluates to 2020,
    using only numbers and the +, *, and - operators.

    >>> twenty_twenty()
    2020
    """
    return ((2020+2020)-2020)*1
```
**过程：**

这是第0个lab，是新手教程，主要目的是带大家熟悉做题以及提交流程。

CS61A有一个自动测试软件叫[okpy](okpy.org)专为本课开发，杜绝了人工批阅可能存在的各种问题，感觉好厉害，但是更值得欣赏的是教学的态度。据说之后的游戏作业为了搞定自动批阅，几乎考虑到了所有的情况，实在佩服。

cd到文件所在目录，之后用`python3 ok`

但是我的没有反应，应该是因为我安装的python是anaconda环境？换成`python ok`就可以了

由于是自学没有伯克利的邮箱也自然没有enroll到课程里去，但是这并不影响我们使用ok

第一次输入`python3 ok`会让你输入邮箱，只要输自己邮箱就可以了，我用的gmail，跳出网页点击继续就可以，有结果但是不会累计你的分数。

**提交成功**

![](docs/CS61A.assets/5.png)

---