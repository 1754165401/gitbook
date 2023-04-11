# 函数

### 意义: 函数是指将一组语句的集合通过一个名字(函数名)封装起来，要想执行这个函数，只需调用其函数名即可

### 定义

```
def 函数名(参数):
    函数体
    return 返回值
```

### 函数返回值

```
return 返回值
```

### 调用

#### \[返回值] = 函数名(\[实参值])

### 函数的参数

#### 位置参数

* def test(x,y,z): # x,y,z 就是位置形参 print(x,y,z) ​ test(1,2,3) # 1 2 3 就是位置实参

#### 关键字参数

* test(y=1,x=2,z=3)

#### 默认参数

* def test(x,y,z=2): print(x,y,z)

#### 可变长度的参数

* \*args
  * def foo(x, y, z=1, \*args)
* \*\*kwrgs
  * def foo(x,\*\*kwargs):

#### 参数传可变对象和不可变对象

#### 参数传函数

```
def func(f):
    print(f)
​
def my_func():
    print("i am func")
​
func(my_func)
```

#### 函数嵌套

```
def outer():
    print("我是嵌套外部函数")
​
    def inner():
        print("我是嵌套内部函数")
```

### 匿名函数

#### lambda \[arg1 \[,arg2,.....argn]]:expression

```
# list(map(lambda x:x+1, a))map将传入的函数依次作用到序列的每个元素，并把结果作为新的Iterator返回
​
from functools import reduce
​
a = [1,2,3,4,5,6,7,8,9]
#reduce函数必须接收两个参数，reduce把结果继续和序列的下一个元素做累积计算
print(reduce(lambda x, y: x+y, a))
​
filter()把传入的函数依次作用于每个元素，返回值是 True则保留，否则舍弃list(filter(lambda x: x % 2, a))
​
print(sorted(a, key=lambda e: (e > 0, abs(e))))
```

### 命名空间

#### locals:函数内部的名字空间，一般包括函数的局部变量以及形式参数

enclosing:在嵌套函数中外部函数的名字空间, 若fun2嵌套在fun1里，对fun2来说，fun1的名字空间就enclosing. globals:当前的模块空间，模块就是一些py文件。 builtins: 内置模块空间，也就是内置变量或者内置函数的名字空间。

```
import random
random = 0
def fun():
  random = 1
  def fuc():
      random = 2
      print(random)
  return fuc()
fun()
```

* 修改全局变量使用global关键字
* 修改嵌套作用域（enclosing 作用域，外层非全局作用域）中的变量使用nonlocal关键字

#### import builtins

print(dir(builtins)) 查看内置变量
