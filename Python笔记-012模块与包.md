# 模块与包

## 导入模块

    # 导入math模块，使用math相关函数
    import math

    print(id(math))
    print(type(math))  # <class 'module'>
    print(math)  # <module 'math' (built-in)>
    print(math.pi)
    print(dir(math))
    print(math.pow(2, 8))

    # 导入模块中的某个类/函数/属性
    from math import pi

    print(pi)

    # 导入自定义模块
    import calc

    num = calc.add(10, 10)
    print(num)

    # 导入以主程序方式运行的自定义模块
    import calc2

    print(calc2.add(10, 10))

## 包和目录的区别

    """
    包：含有__init__.py文件的文件夹，称为包
    目录：不含有__init__.py文件的文件夹，称为目录
    """

    import pack1.fun_a as funa
    import pack1.fun_b as funb

    print(funa.a)
    print(funb.b)

## 常用的内置模块

    import sys
    import time
    import urllib.request

    # sys 模块；Python解释器以及环境操作的标准库
    print(sys.getsizeof(10))
    print(sys.getsizeof(20))
    print(sys.getsizeof(True))
    print(sys.getsizeof(False))

    # time 模块；时间相关函数的标准库
    print(time.time())
    print(time.localtime(time.time()))

    # os 模块；操作系统服务功能的标准库

    # calendar 模块；日期相关函数的标准库

    # urllib 模块；读取网络数据的标准库
    print(urllib.request.urlopen("http://www.baidu.com").read())  # 打开某个网页，并读取数据

    # json 模块；序列化和反序列化Json的标准库

    # re 模块；字符串执行正则表达式的标准库

    # math 模块；算数运算函数的标准库

    # decimal 模块；精确运算精度有效位相关函数的标准库

    # logging 模块；日志相关函数的标准库