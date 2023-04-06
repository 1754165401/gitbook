# 闭包和装饰器

## 闭包

### 1.必须有一个内嵌函数

### 2.内嵌函数必须引用外部函数中的变量

### 3.外部函数的返回值必须是内嵌函数

#### 注：使用闭包的过程中，一旦外函数被调用一次返回了内函数的引用，虽然每次调用内函数，是开启一个函数执行过后消亡，但是闭包变量实际上只有一份，每次开启内函数都在使用同一份闭包变量。

```
def outer():
    name = 'alex'
​
    def inner():
        nonlocal name
        name = name+' python'
        print("inner", name)
    return inner
    
f = outer()
print(f)
f()
```

### 装饰器

#### 调用方法

第一种： 函数接受对象 = 装饰器函数(被装饰函数) 函数接受对象() 第二种： 装饰器函数(被装饰函数)() 第三种： @装饰器函数 def 被装饰函数(): print("测试") 被装饰函数()

#### 被装饰函数和装饰器不带参数

```
def my_decorator(func):
    def inner():
        print("**********")
        print("要添加的功能代码")
        func()
    return inner
```

#### 被装饰的函数带参数装饰器不带参数

```
def my_decorator(func):
    def inner(*args, **kwargs):     # 可变参数*args和关键字参数**kwargs
        print("**********")
        print("要添加的功能代码")
        func(*args, **kwargs)
    return inner
```

#### 被装饰的函数带参数装饰器带参数

```
def my_decorator(name):
    def outer(func):
        def inner(*args, **kwargs):
            print("********")
            print("添加带装饰器参数%s的功能代码" % self.name)
            func(*args, **kwargs)
        return inner
    return outer
```

#### 多个装饰器嵌套

```
def decorator_a(func):
    print 'Get in decorator_a'
    def inner_a(*args, **kwargs):
        print 'Get in inner_a'
        return func(*args, **kwargs)
    return inner_a
​
def decorator_b(func):
    print 'Get in decorator_b'
    def inner_b(*args, **kwargs):
        print 'Get in inner_b'
        return func(*args, **kwargs)
    return inner_b
​
@decorator_b
@decorator_a
def f(x):
    print 'Get in f'
    return x * 2
​
f(1)
```
