# 流程控制

### 分支结构

```
if.....
​
if.....else.....
​
if......elif......elif......else
```

（分数范围查看）

### 循环结构

#### while循环

```
while 判断条件(condition)：
​
执行语句(statements)……
```

如果 while 结束时，则执行 else 的语句块。

（猜数字游戏）

```
import random
# random.randint(start, end) 生成一个包括start和end的随机整数
​
y = random.randint(1, 10)
# print(y)
for i in range(1, 4):  # i 猜错机会  1 2 3
    x = int(input("请输入一个1-10以内的整数："))
    if x == y:
        print("恭喜你猜对了！")
        break
    else:
        print(f"很抱歉，猜错了！还有{3-i}机会")
```

#### for循环

```
for iterating_var in sequence:
​
   statements(s)  
```

如果 for 结束时，则执行 else 的语句块。

（九九乘法表）

```
for i in range(1, 10):
    for j in range(1, i+1):
        print("{} * {} = {}".format(i, j, i*j), end=' ')
    print()
```

#### break 关键字 可以直接退出当前整个循环结构，直接终止循环，不执行else语句块

#### continue 关键字 跳过当前循环,进入下一次循环，会执行else语句块

### 列表推导式、列表生成式

```
[a for a in rang(1,10)]
​
jjcf = [[i*j for j in range(1, i+1)] for i in range(1, 10)]
```
