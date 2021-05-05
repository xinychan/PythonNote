# 字符串

字符串是基本数据类型，是不可变的字符序列

## 字符串的驻留机制

    s1 = "Python"
    s2 = "Python"
    s3 = "Py" + "thon"
    print(s1, id(s1))  # 字符串相同，指向同一个id，不会开辟新内存
    print(s2, id(s2))
    print(s3, id(s3))

    """
    驻留机制
    1-字符串长度为0或者1会驻留
    2-符合标识符的字符串会驻留
    3-字符串只在编译时进行驻留，而不是运行时
    4-[-5,256]之间的整数数字会驻留
    sys.intern()方法会强制内容相同字符串指向同一个对象
    PyCharm对字符串进行了优化；不符合标识符的字符串，和不是[-5,256]之间的整数数字，只要内容一致则会驻留
    """

## 字符串的查询

    s1 = "hello,hello"
    print(s1.index("lo"))  # 3；查找子串第一次出现位置，不存在子串则 ValueError: substring not found
    print(s1.find("lo"))  # 3；查找子串第一次出现位置，不存在子串则返回 -1
    print(s1.rindex("lo"))  # 9；查找子串最后一次出现位置，不存在子串则 ValueError: substring not found
    print(s1.rfind("lo"))  # 9；查找子串最后一次出现位置，不存在子串则返回 -1

    # print(s1.index("python"))  # ValueError: substring not found
    print(s1.find("python"))  # -1；查找子串第一次出现位置，不存在子串则返回 -1
    # print(s1.rindex("python"))  # ValueError: substring not found
    print(s1.rfind("python"))  # -1；查找子串最后一次出现位置，不存在子串则返回 -1

## 字符串大小写转换

    name = "python,HI"
    print(name.upper())  # PYTHON,HI;全部转为大写
    print(name.lower())  # python,hi;全部转为小写
    print(name.swapcase())  # PYTHON,hi;大写转小写，小写转大写
    print(name.capitalize())  # Python,hi;第一个字符串转为大写，其余转为小写
    print(name.title())  # Python,Hi;每个单词的第一个字符转为大写，其余转为小写
    # 使用upper/lower等函数后，会生成一个新的字符串
    upper_name = name.upper()
    print(id(name))
    print(id(upper_name))

## 字符串对齐

    name = "python"
    # 居中对齐
    print(name.center(2))  # python；宽度参数小于原字符长度，返回原字符
    print(name.center(10))  # 默认填充符为空格
    print(name.center(10, "*"))  # **python**；指定填充符为*
    # 左对齐
    print(name.ljust(10))  # 默认填充符为空格
    print(name.ljust(10, "*"))  # python****；指定填充符为*
    # 右对齐
    print(name.rjust(10))  # 默认填充符为空格
    print(name.rjust(10, "*"))  # ****python；指定填充符为*
    # 右对齐；只能用0填充，不能自定义填充符
    print(name.zfill(10))  # 0000python；填充符为0
    print("-2021".zfill(10))  # -000002021；负数字符串的0添加到负号之后

## 字符串的分隔

    name = "python hello hi"
    print(name.split())  # ['python', 'hello', 'hi']；默认使用空格分隔
    name = "python-hello-hi"
    print(name.split("-"))  # ['python', 'hello', 'hi']；使用指定分隔符
    name = "python-hello-hi"
    print(name.split("-", maxsplit=1))  # ['python', 'hello-hi']；设置最大分隔次数为1
    # 从右边开始分隔
    name = "python-hello-hi"
    print(name.rsplit("-"))  # ['python', 'hello', 'hi']
    print(name.rsplit("-", maxsplit=1))  # ['python-hello', 'hi']

## 字符串的判断

    # 是否是合法标识符；合法标识符只有数字下划线和字母
    name = "python,hello"
    print(name.isidentifier())  # False
    name = "hello_张三_123"
    print(name.isidentifier())  # True
    # 判断字符串是否由空白字符组成
    name = "   "
    print(name.isspace())  # True
    # 判断字符串是否由字母组成
    name = "python张三"
    print(name.isalpha())  # True
    name = "python_hello"
    print(name.isalpha())  # False
    # 判断字符串是否由十进制数字组成
    name = "python"
    print(name.isdecimal())  # False
    name = "123456789"
    print(name.isdecimal())  # True
    name = "123四56789"
    print(name.isdecimal())  # False
    # 判断字符串是否由数字组成
    name = "python"
    print(name.isnumeric())  # False
    name = "123四56"
    print(name.isnumeric())  # True;中文数字也识别为数字
    # 判断字符串是否由字母和数字组成
    name = "python_123"
    print(name.isalnum())  # False
    name = "python123"
    print(name.isalnum())  # True

## 字符串的替换

    # 字符串的替换
    name = "hello,python,python,python"
    print(name.replace("python", "java"))  # hello,java,java,java
    # 设置最大替换次数：最多只替换2次
    print(name.replace("python", "java", 2))  # hello,java,java,python

## 字符串的合并

    # 字符串的合并
    # 对列表和元组的字符串进行合并
    name = ["java", "python", "hello"]
    print("-".join(name))  # java-python-hello
    name = ("java", "python", "hello")
    print("*".join(name))  # java*python*hello
    # 对字符串拆分成序列进行连接
    name = "Python"
    print("*".join(name))  # P*y*t*h*o*n

## 字符串的比较

    print("apple" > "app")  # True
    # 比较原理
    print("a" > "b")  # False
    print(ord("a"), ord("b"))  # 97 98
    print(chr(97), chr(98))  # a b

## 字符串的切片

    # 字符串是不可变类型，不具备增删改操作；所以切片会产生新的字符串对象
    name = "hello,Python"
    name1 = name[:5]
    name2 = name[6:]
    print(name1)  # hello
    print(name2)  # Python

    name1 = name[0:5]
    name2 = name[6:]
    print(name1)  # hello
    print(name2)  # Python

    name1 = name[1:5:2]
    print(name1)  # el
    name1 = name[::2]  # 从0开始，直到最后一个字符；步长为2
    print(name1)  # hloPto
    name1 = name[::-1]  # 步长为负数，字符串会倒序
    print(name1)  # nohtyP,olleh

## 格式化字符串

    # % 占位符
    name = "Python"
    age = 20
    print("我叫%s 今年%d" % (name, age))  # 我叫Python 今年20

    # {} 占位符
    name = "Python"
    age = 20
    print("我叫{0} 今年{1}".format(name, age))

    # f-string
    name = "Python"
    age = 20
    print(f"我叫{name} 今年{age}")

    # 字符串数字宽度和精度；使用%
    print("%d" % 99)  # [99]
    print("%10d" % 99)  # [        99];设置字符串宽度长度为10
    print("%f" % 3.141592)  # 3.141592
    print("%.3f" % 3.141592)  # 3.142;保留3位小数
    print("%10.3f" % 3.141592)  # [     3.142];同时设置宽度和保留小数位
    # 字符串数字宽度和精度；使用{}
    print("{0}".format(3.141592))
    print("{0:.3}".format(3.141592))  # 3.14；保留3位数字
    print("{0:.3f}".format(3.141592))  # 3.142；保留3位小数
    print("{0:10.3f}".format(3.141592))  # [     3.142];同时设置宽度和保留小数位
