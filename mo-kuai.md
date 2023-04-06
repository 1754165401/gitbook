# 模块

### 好处：

1.最大的好处是大大提高了代码的可维护性。其次，编写代码不必从零开始。当一个模块编写完毕，就可以被其他地方引用。我们在编写程序的时候，也经常引用其他模块，包括Python内置的模块和来自第三方的模块。 2.使用模块还可以避免函数名和变量名冲突。每个模块有独立的命名空间，因此相同名字的函数和变量完全可以分别存在不同的模块中，所以，我们自己在编写模块时，不必考虑名字会与其他模块冲突

### 种类：

1.内置标准模块（又称标准库）python自带 2.第三方开源模块，可通过pip install 模块名 联网安装 3.自定义模块

### 调用方法：

import module\_a # 导入 from module import xx from module.xx.xx import xx as rename # 导入后重命名 from module.xx.xx import \* # 导入一个模块下的所有方法，不建议使用 module\_a.xxx #调用

### 常用模块

#### OS模块

```
print(os.path.basename('./sadafasda/sadasfas.txt'))  # 去掉目录路径，返回文件名
​
print(os.path.dirname('./sadafasda/sadasfas.txt'))  #去掉文件名，返回目录路径
​
print(os.path.join('sadfa', 'wqwq', 'dsafg', 'dasc.txt'))  # 将分离的各部分组合成一个路径名
​
print(os.path.split('../sadafasda/sadasfas.txt'))  # 返回(dirname(),basename())元组
​
print(os.path.splitext('../sadafasda/sadasfas.txt'))  # 返回filename,extension)元组
​
print(os.path.exists('tttttt.txt'))  # 是否存在
```

#### sys模块

```
print(sys.argv)  # 实现从程序外部向程序传递参数
​
sys.exit(0)  # 程序中间的退出，arg=0为正常退出
​
print(sys.path)  # 获取指定模块搜索路径的字符串集合
```

#### time模块

```
print(time.time())  # 获取当前时间戳
​
print(time.localtime(time.time()))  # 获取当前时间戳转换的元组数据
​
print(time.asctime(time.localtime(time.time())))  # 获取当前时间戳格式化数据
​
print((time.strftime("%Y-%m-%d %H:%M:%S %A %B %j %p %U", time.localtime())))  # 获取当前时间戳格式化日期
​
%y 两位数的年份表示（00-99）
​
%Y 四位数的年份表示（000-9999）
​
%m 月份（01-12）
​
%d 月内中的一天（1-31）
​
%H 24小时制小时数（1-24）
​
%I 12小时制小时数（01-12）
​
%M 分钟数（00=59）
​
%S 秒（00-59）
​
%a 本地简化星期名称
​
%A 本地完整星期名称
​
%b 本地简化的月份名称
​
%B 本地完整的月份名称
​
%c 本地相应的日期表示和时间表示
​
%j 年内的一天（001-366）
​
%p 本地A.M.或P.M.的等价符
​
%U 一年中的星期数（00-53）星期天为星期的开始
​
%w 星期（0-6），星期天为星期的开始
​
%W 一年中的星期数（00-53）星期一为星期的开始
​
%x 本地相应的日期表示
​
%X 本地相应的时间表示
​
%Z 当前时区的名称
​
%% %号本身
```

#### random模块

```
print(random.random())  # 用于生成一个[0,1)的随机浮点数
​
print(random.uniform(1, 10))  # 用于生成一个[1,10)的随机浮点数
​
print(random.randint(1, 10))  # 用于生成一个[1,10]的随机整数
​
print(random.randrange(1, 10, 8))  # 从指定范围中，按指定基数递增的集合中获取一个随机数 start默认为0，step默认为1
​
print(random.choice(a))  # 从序列中随机获取一个元素
​
random.shuffle(a)  # 用于将一个列表中的元素打乱
​
print(random.sample(a, 1))  # 从指定序列中随机获取指定长度的片段
```

#### pickle模块（实现了对一个 Python 对象结构的二进制序列化和反序列化）

```
pickle.dump(data, fw)
​
print(pickle.load(fr))
```

```
import pickle
data1 = {'a': [1, 2.0, 3, 4+6j],
         'b': ('string', 'Unicode string'),
         'c': None}
output = open('data.txt', 'wb+')
pickle.dump(data1, output)
output.seek(0, 0)
print(type(pickle.load(output)))
​
output.close()
```

#### json模块（是一个文本序列化格式（它输出 unicode 文本，尽管在大多数时候它会接着以 utf-8 编码））

```
json.dumps(data)
​
json.loads(jsonData)
```

```
import json
# data1 = {
#     'no' : 1,
#     'name' : 'alex',
#     'url' : 'http://www.alex.com'
# }
# 写入 JSON 数据
# with open('data.json', 'w') as f:
#     json.dump(data1, f)
​
# 读取数据
# with open('data.json', 'r') as f:
    # data = json.load(f)
    # print(type(data))
```

#### re模块

```
re.search(pattern, string, flags=0)扫描整个字符串并返回第一个成功的匹配
​
re.sub(pattern, repl, string, count=0, flags=0)用于替换字符串中的匹配项
​
re.compile(pattern[, flags])函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用
​
re.findall(pattern, string, flags=0)在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表.
```

```
import re
phone = "13435114567"
# 前3位是网络识别号、4-7位是地区编码（HLR归属位置寄存器）、8-11位是用户号码（随机分配）
email = "mouliang@zzt.com"
# 登录名@主机名.域名   登录名@qq.com  登录名@163.com
print(re.search(r"1\d{2}\d{4}\d{4}", phone).group())
print(re.search(r"[0-9a-zA-Z]{1,19}@[0-9a-zA-Z]{2,4}.com", email).group())
```

### flag

```
re.I    使匹配对大小写不敏感
​
re.M    多行匹配，影响 ^ 和 $
​
re.S    使 . 匹配包括换行在内的所有字符
```

### pattern

```
^   匹配字符串的开头
​
$   匹配字符串的末尾。
​
.   匹配任意字符，除了换行符，当\w    匹配数字字母下划线
​
\W  匹配非数字字母下划线
​
\s  匹配任意空白字符，等价于 [\t\n\r\f]。
​
\S  匹配任意非空字符
​
\d  匹配任意数字，等价于 [0-9]。
​
\D  匹配任意非数字
​
\A  匹配字符串开始
​
\Z  匹配字符串结束，如果是存在换行，只匹配到换行前的结束字符串。
​
\z  匹配字符串结束
​
\G  匹配最后匹配完成的位置。
​
\b  匹配一个单词边界，也就是指单词和空格间的位置。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。
​
\B  匹配非单词边界。'er\B' 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。
​
*   匹配0个或多个的表达式
​
+   匹配1个或多个的表达式
​
?   匹配0个或1个由前面的正则表达式定义的片段，非贪婪方式
​
[...]   用来表示一组字符,单独列出：[amk] 匹配 'a'，'m'或'k'
​
[^...]  不在[]中的字符：[^abc] 匹配除了a,b,c之外的字符
​
{n}   匹配n个前面表达式。例如，"o{2}"不能匹配"Bob"中的"o"，但是能匹配"food"中的两个o。
​
{n,}    精确匹配n个前面表达式。例如，"o{2,}"不能匹配"Bob"中的"o"，但能匹配"foooood"中的所有o。"o{1,}"等价于"o+"。"o{0,}"则等价于"o*"。
​
{n, m}  匹配 n 到 m 次由前面的正则表达式定义的片段，贪婪方式
​
a| b    匹配a或b
```
