# 函数递归

### 定义

#### 1.必须有一个明确的结束条件，要不就会变成死循环了，最终撑爆系统

#### 2.每次进入更深一层递归时，问题规模相比上次递归都应有所减少

#### 3.递归执行效率不高，递归层次过多会导致栈溢出

```
# 设置递归深度
# import sys
# sys.setrecursionlimit(1100)
# print(my_reduce_add(1000))
```

### 累计运算

#### # 普通累积计算

```
def my_reduce(n):
    if n == 1:
        return 1
    return n + my_reduce(n-1)
```

### 斐波那契数列

```
def my_fabonacci(n):
    if n == 1:
        return 0
    if n == 2:
        return 1
    v = my_fabonacci(n-1) + my_fabonacci(n-2)
    print(v)
    return v
```

### 汉诺塔问题

#### 在世界刚被创建的时候有一座钻石宝塔A，其上有64个金蝶。所有碟子按从大到小的次序从

#### 塔底堆放至塔顶。紧挨着这座塔有另外两个钻石宝塔B和C。从世界创始之日起，波罗门的

#### 牧师就一直在试图把塔A上的碟子移动到C上去，其间借助于塔B的帮助。每次只能移动一个

#### 碟子，任何时候都不能把一个碟子放在比它小的碟子上面。当牧师们完成这个任务时，世界

#### 末日也就到了

```
def move(current, target):
    print("==" * 40)
    print("移动前:\n\t\t{} \n\t\t{} \n\t\t{}".format(A, B, C))
    target.append(current.pop())
    print("移动后:\n\t\t{} \n\t\t{} \n\t\t{}".format(A, B, C))
    print("==" * 40)
​
def Hanoi(n, current, buffer, target):
    if n == 1:
        move(current, target)
    else:
        Hanoi(n-1, current, target, buffer)
        move(current, target)
        Hanoi(n-1, buffer, current, target)
```

A = \[3, 2, 1] B = \[] C = \[] Hanoi(3, A, B, C)
