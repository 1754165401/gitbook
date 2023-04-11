# 文件处理

### 错误和异常

#### 语法错误(SyntaxError: invalid syntax)

#### 异常

```
ZeroDivisionError: division by zero 0 不能作为除数，触发异常
​
NameError: name 'spam' is not defined 变量 未定义，触发异常
​
TypeError: can only concatenate str (not "int") to str  int 不能与 str 相加，触发异常
```

#### 异常处理

```
# try/except 语句
​
while True:
    try:
        x = int(input("请输入一个数字: "))
        break
    except ValueError:
        print("您输入的不是数字，请再次尝试输入！")
        
​
# try/except...else...finally
​
    try:
        print("当前是try块")
    except Exception:
        print("当前是error块")
    else:
        print("当前是else块")
    finally:
        print("当前是finally块")
​
# 手动抛出异常
​
# raise [Exception [, args [, traceback]]]
​
try:
    raise NameError('HiThere')
except NameError as e:
    print('An exception flew by!')
    print(e)
```

### 文件操作

#### open(file, mode='r', buffering=-1, encoding=None) # 打开文件

* mode(文件打开模式)
  * t 文本模式 (默认)。
  * &#x20;x 写模式，新建一个文件，如果该文件已存在则会报错。
  * &#x20;b 二进制模式。
* 打开一个文件进行更新(可读可写)。
* &#x20;r 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。&#x20;
* rb 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。&#x20;
* r+ 打开一个文件用于读写。文件指针将会放在文件的开头。&#x20;
* rb+ 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。&#x20;
* w 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。&#x20;
* wb 以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。&#x20;
* w+ 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。&#x20;
* wb+ 以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。
* &#x20;a 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。
* &#x20;ab 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。
* &#x20;a+ 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。&#x20;
* ab+ 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。
* buffering：缓冲区
  * buffering= -1 t和b都是io.DEFAULT\_BUFFER\_SIZE buffering=0 二进制模式 关闭缓冲区，文本模式不支持 buffering=1 文本模式行缓冲，遇到换行符才flush buffering>1 二进制模式表示缓冲大小。缓冲区的值可以超过 io.DEFAULT\_BUFFER\_SIZE，直到设定的值超出后才把缓冲区flush，文本模式，是io.DEFAULT\_BUFFER\_SIZE字节，flush完后把当前字符串也写入磁盘

```
import time
f = open('data.txt', 'w+', buffering=1, encoding="UTF-8")
​
# buffering = 1
# f.write("第一行")
# # f.flush()
# print("等待2秒")
# time.sleep(2)
# f.write("\n第二行")
​
# buffering > 1
# for i in range(51):
# # for i in range(50):
#     f.write("a\n".encode())
# print("等待3秒")
# time.sleep(3)
​
f.close()
```

* encoding：编码，仅文本模式使用

#### 关闭文件 f.close()

#### 读取

* f.read()读取全部
* f.readline()读取一行并换行
* f.readlines()返回所有的行到列表中(带换行符)
* f.read().splitlines()返回所有的行到列表中(不带换行符)
* for fr in f: print(fr) 遍历所有行

#### 写入

* f.write(string) 将 string 写入到文件中, 然后返回写入的字符数，如果要写入一些不是字符串的东西, 那么将需要先进行转换
* file.writelines(sequence)向文件写入一个序列字符串列表，如果需要换行则要自己加入每行的换行符
* file.flush() #刷新文件内部缓冲,直接把内部缓冲区的数据立刻写入文件, 而不是被动的等待输出缓冲区写入.
* f.seek(offset\[,whence])移动文件指针位置.offest偏移多少字节,whence从哪里开始向后seek可以越界,越界返回空字符;但是向前seek不能越界,否则抛异常
* file.tell()返回文件当前位置

#### with关键字

*   当处理一个文件对象时, 使用 with 关键字是非常好的方式。在结束后, 它会帮你正确的关闭文件。 而且写起来也比 try - finally 语句块要简短:

    ```
    with open('/tmp/foo.txt', 'r') as f:
        read_data = f.read()
        f.closed
    ```

    \
