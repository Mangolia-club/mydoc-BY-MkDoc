[[Projects]]

**[Project 1: The Game of Hog | CS 61A Fall 2021 (berkeley.edu)](https://inst.eecs.berkeley.edu/~cs61a/fa21/proj/hog/)**

解压出以下文件：

![[Pasted image 20220123000411.png]]

只需修改`hog.py`即可。

---

## Phase 1: Simulator

这部分需要做出游戏需要的所有的逻辑部分的自定函数。

---

### Problem 0 (0 pt)

理解`make_test_dice` 和`make_fair_dice` 两个函数做几道题即可。

---

### Problem 1 (2 pt)

理解并补全 `roll_dice`函数。我的结果如下：

```python
def roll_dice(num_rolls, dice=six_sided):
	sum = 0
	num = 0
	saw_sad=False
	for i in range (0,num_rolls):
		num=dice()
		if num!=1:sum += num
		else: saw_sad=True
	return sum if saw_sad==False else 1```

---

### Problem 2 (3 pt)

理解并补全 `picky_piggy`函数。我的结果如下：
```python
def picky_piggy(score):
	dividend=1
	divisor=7
	quotient=0
	remainder=1
	i=1
	if score==0:return 7
	else:
	while i <= score:
		dividend=10*remainder
		quotient=dividend//divisor
		remainder=dividend%divisor
		i+=1
	return quotient
```


**注意**：关键词不能有for，应该是因为还没讲到。

---

### Problem 3 (2 pt)

Implement the `take_turn` function, which returns the number of points scored for a turn by rolling the given `dice` `num_rolls` times.

比较简单，就是按情况输出对应的函数就可以了：

```python
def take_turn(num_rolls, opponent_score, dice=six_sided, goal=GOAL_SCORE):
	return picky_piggy(opponent_score) if num_rolls==0 else roll_dice(num_rolls,dice)
```


---

### Problem 4 (1 pt)

Implement `hog_pile`, which takes the current player and opponent scores and returns the points that the current player will receive due to Hog Pile. If Hog Pile is not applicable, the current player could also recieve 0 additional points.

也非常简单：

```python
def hog_pile(player_score, opponent_score):
    if player_score == opponent_score : return player_score
    else: return 0
```


---

### Problem 5 (4 pt)

Implement the `play` function, which simulates a full game of Hog. Players take turns rolling dice until one of the players reaches the `goal` score. A turn is defined as one roll of the dice.

这个函数比较复杂（?），结构上很简单，但是难的地方在于如何熟练理解运用之前写好的那一大堆的自定函数。

```python
def play(strategy0, strategy1, score0=0, score1=0, dice=six_sided,
         goal=GOAL_SCORE, say=silence):
    """Simulate a game and return the final scores of both players, with Player
    0's score first, and Player 1's score second.

    A strategy is a function that takes two total scores as arguments (the
    current player's score, and the opponent's score), and returns a number of
    dice that the current player will roll this turn.

    strategy0:  The strategy function for Player 0, who plays first.
    strategy1:  The strategy function for Player 1, who plays second.
    score0:     Starting score for Player 0
    score1:     Starting score for Player 1
    dice:       A function of zero arguments that simulates a dice roll.
    goal:       The game ends and someone wins when this score is reached.
    say:        The commentary function to call at the end of the first turn.
    """
    who = 0  # Who is about to take a turn, 0 (first) or 1 (second)
    # BEGIN PROBLEM 5
    while 1:
        if who == 0:
            score0+=take_turn(strategy0(score0, score1),score1,dice,goal)
            score0+=hog_pile(score0,score1)
        if who == 1:
            score1+=take_turn(strategy1(score1, score0),score0,dice,goal)
            score1+=hog_pile(score1,score0)
        if score0 >= goal or score1 >= goal:
            break
        who = next_player(who)
    return score0, score1
```


---

之后就可以运行`python3 hog_gui.py`来玩上一把啦~~

---

## Phase 2: Commentary

第二部分就是print一些自动生成的==~~彩虹屁~~==评语，like:`"22 point(s)! That's a record gain for Player 1!"`

### Commentary examples

The function `say_scores` in `hog.py` is an example of a commentary function that simply announces both players' scores. ==**Note that `say_scores` returns itself, meaning that the same commentary function will be called each turn.**==

```python
def say_scores(score0, score1):
    """A commentary function that announces the score for each player."""
    print("Player 0 now has", score0, "and Player 1 now has", score1)
    return say_scores
```

简单来讲就是一个返回自己的函数，期间会说预设好的话，**每一次**都会调用自己。

```python
def play(strategy0, strategy1, score0=0, score1=0, dice=six_sided,
         goal=GOAL_SCORE, say=silence):
    while 1:
        if who == 0:
            score0+=take_turn(strategy0(score0, score1),score1,dice,goal)
            score0+=hog_pile(score0,score1)
        if who == 1:
            score1+=take_turn(strategy1(score1, score0),score0,dice,goal)
            score1+=hog_pile(score1,score0)
        say=say(score0,score1)
        if score0 >= goal or score1 >= goal:
            break
        who = next_player(who)
	return score0, score1
```

有一个点：必须要在判定胜负前say，不然胜前的最后一次就会缺失say（过不了ok）。

懒得截图了，溜

---

### Problem 7 (3 pt)

理解并编写 `announce_highest`：用于输出某个玩家获得了他的最高一次分数。

```python
def announce_highest(who, last_score=0, running_high=0):
    assert who == 0 or who == 1, 'The who argument should indicate a player.'
    def say(score0,score1, last_score=last_score, running_high=running_high):
        if who == 0:
            if (score0 - last_score) > running_high: 
                print(score0 - last_score,"point(s)! That's a record gain for Player 0!")
                running_high = score0 - last_score
            return announce_highest(who,score0,running_high)
        if who == 1:
            if (score1 - last_score) > running_high: 
                print(score1 - last_score,"point(s)! That's a record gain for Player 1!")
                running_high = score1 - last_score
            return announce_highest(who,score1,running_high)
    return say
```

有一段时间卡在回溯之前的情况改写不会留存之前的数据这里了，say函数里面用的是nonlocal来把`announce_highest`的`last_score`和`running_high`传入say。

应该是因为nonlocal相当于是里外函数的变量做的是强链接而不是形参引用这样，，所以如果一个玩家的`running_high`改变了，会传到外层函数，另一个玩家调用函数的时候用的就是这个值？

等我再去研究一下[[Higher-order Functions|高阶函数]]的具体知识。

---

## Phase 3: Strategies

In the third phase, you will experiment with ways to improve upon the basic strategy of always rolling a fixed number of dice. First, you need to develop some tools to evaluate strategies.

写AI策略咯~~

---

### Problem 8 (2 pt)

Implement the `make_averaged` function.

计算某种策略的平均得分。

```python
def make_averaged(original_function, trials_count=1000):
    """Return a function that returns the average value of ORIGINAL_FUNCTION
    called TRIALS_COUNT times.
    >>> dice = make_test_dice(4, 2, 5, 1)
    >>> averaged_dice = make_averaged(roll_dice, 1000)
    >>> averaged_dice(1, dice)
    3.0
    """
    # BEGIN PROBLEM 8
    def f(*args):
        total = 0
        for i in range(trials_count):
            total += original_function(*args)
        return total / trials_count
    return f
    # END PROBLEM 8
```

这里的`*args`指的是`original_function`的各个参数，依赖的是选择的roll函数，如果就是普通的`roll_dice`，即需要传入`(num_rolls, dice=six_sided)`。

如果需要调用`make_averaged`，不仅需要它自己的参数，因为它是一个返回函数的高阶函数，还需要传入f的参数。

```python
whatever = make_averaged(roll_dice,1000）
whatever(2,dice)
#相当于以下形式：
whatever=make_averaged(roll_dice,1000)(2,dice)
```

我愿称之为套娃函数（嵌套函数），即第二个括号前其实相当于是一个函数名：`f`，而后面才是给他传入的参数，第一个括号内的参数会影响f这个函数的函数体。

我觉得还是有点为了用高阶而用高阶了，之前的announce函数可以有回溯的功能，而在这里仅仅是比较费脑子罢了。

也只有到了这里才稍微搞清楚了一点高阶函数的事情。。

不过继续前进吧，**只要不断前进，道路就会不断延伸。**

---

### Problem 9 (2 pt)

Implement the `max_scoring_num_rolls` function, which runs an experiment to determine the number of rolls (from 1 to 10) that gives the maximum average score for a turn. Your implementation should use `make_averaged` and `roll_dice`.

写 `max_scoring_num_rolls` ，即是调用之前的函数来估计本次丢多少骰子可以获得最大的期望分数。

```python
def max_scoring_num_rolls(dice=six_sided, trials_count=1000):
    """Return the number of dice (1 to 10) that gives the highest average turn score
    by calling roll_dice with the provided DICE a total of TRIALS_COUNT times.
    Assume that the dice always return positive outcomes.

    >>> dice = make_test_dice(1, 6)
    >>> max_scoring_num_rolls(dice)
    1
    """
    max=0
    index=1
    for i in range (1,11):
        average=make_averaged(roll_dice,trials_count)(i,dice)
        if average > max: index,max = i,average
    return index
```

函数体本身比较简单，关键在于如何正确调用高阶函数，如同上面讲述的。

---
### Problem 10 (1 pt)

A strategy can try to take advantage of the _Picky Piggy_ rule by rolling 0 when it is most beneficial to do so. Implement `picky_piggy_strategy`, which returns 0 whenever rolling 0 would give **at least** `cutoff` points and returns `num_rolls` otherwise.

很简单，只需要调用`picky_piggy`然后和`cutoff`比较即可。

```python
def picky_piggy_strategy(score, opponent_score, cutoff=8, num_rolls=6):
    """This strategy returns 0 dice if that gives at least CUTOFF points, and
    returns NUM_ROLLS otherwise.
    """
    return 0 if picky_piggy(opponent_score) >= cutoff else num_rolls
```

---

### Problem 11 (1 pt)

A strategy can also take advantage of the _Hog Pile_ rules. The Hog Pile strategy always rolls 0 if doing so triggers the rule. In other cases, it rolls 0 if rolling 0 would give **at least** `cutoff` points. Otherwise, the strategy rolls `num_rolls`.

```python
def hog_pile_strategy(score, opponent_score, cutoff=8, num_rolls=6):
    """This strategy returns 0 dice when this would result in Hog Pile taking
    effect. It also returns 0 dice if it gives at least CUTOFF points.
    Otherwise, it returns NUM_ROLLS.
    """
    return 0 if picky_piggy(opponent_score)+score==opponent_score or picky_piggy_strategy(score,opponent_score,cutoff,num_rolls)==0 else num_rolls
```

为了一行写下牺牲了很多哈哈、。

---
### Optional: Problem 12 (0 pt)

Implement `final_strategy`, which combines these ideas and any other ideas you have to achieve a high win rate against the baseline strategy.

写一个自定义的策略，还有个建好的`run_experiments()`可以调用来测试胜率。

但是我时间有限（进度差了太多）所以就简单写了一下，胜率略微比0.5高、、

---


完结撒花~~

![[Pasted image 20220129120753.png]]