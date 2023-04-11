# 迭代器和生成器

### 可迭代(iterable)

#### 这些可以直接作用于for循环的对象统称为可迭代对象

```
from collections.abc import Iterable, Iterator
list1 = [1, 2, 3]
print(isinstance(list1, Iterable))
```

### 迭代器(Iterator)

#### 可以被next()函数调用并不断返回下一个值的对象称为迭代器 把list、dict、str等Iterable变成Iterator可以使用iter()函数

```
while True:
try:
    print (next(it))
except StopIteration:
    sys.exit()
```

### 生成器(Generator)

#### 在 Python 中，使用了 yield 的函数被称为生成器（generator）。

跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。

在调用生成器运行的过程中，每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行。

```
def fibonacci(n):
    a, b = 0, 1
​
    while n > 0:
        yield a
        a, b = b, a + b
        n -= 1
​
​
f = fibonacci(7)
for i in f:
    print(i)
```

#### 生成器表达式

```
a = (i for i in range(100))
```
