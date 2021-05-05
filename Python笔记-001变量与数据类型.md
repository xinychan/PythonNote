# 变量与数据类型

## 变量的定义和使用

Python 是一门动态语言，声明变量时没有类型；
Python 不使用大括号来表示逻辑的递进关系，而是使用缩进来表示；

    name = '玛利亚'
    print(name)
    print('标识', id(name))  # 变量标识，变量存储的内存地址：2244516377296
    print('类型', type(name))   # 变量类型 <class 'str'>
    print('值', name)  # 变量值 玛利亚

## Python 常用数据类型

### 整数类型 int

    n1 = 90
    n2 = -76
    n3 = 0
    print(n1, type(n1))
    print(n2, type(n2))
    print(n3, type(n3))

### 浮点数 float

    a = 3.14
    print(a, type(a))

### 布尔类型 bool

    f1 = True
    f2 = False
    print(f1, type(f1))
    print(f2, type(f2))

    # 布尔值可以转成整数计算；True=1,False=0
    print(f1 + 1)  # 2
    print(f2 + 1)  # 1

### 字符串类型 str

    # 单行字符串
    str1 = '人生苦短，我用Python'
    str2 = "人生苦短，我用Python"
    # 多行字符串
    str3 = '''人生苦短，
    我用Python'''
    str4 = """人生苦短，
    我用Python"""

### 数据类型转换

    name = '张三'
    age = 20
    print(type(name), type(age))

    # 类型转换错误示例
    # print('我是' + name + '年龄' + age)  # TypeError: can only concatenate str (not "int") to str
    print('我是' + name + '年龄' + str(age))

    # str()转字符串类型
    a = 6
    b = 3.14
    c = True
    print(type(a), type(b), type(c))
    print(type(str(a)), type(str(b)), type(str(c)))
    print(str(a) + str(b) + str(c))

    # int()转整数类型
    s1 = '123'
    s2 = '3.14'
    s3 = 3.14
    s4 = False
    print(type(s1), type(s2), type(s3), type(s4))
    print(int(s1))  # 字符串转int，字符串必须为整数
    # print(int(s2))# 字符串不是整数，无法转换int
    print(int(s3))  # float转整数，只保留整数部分
    print(int(s4))  # 布尔值转整数，True = 1 ，False = 0

    # float()转浮点数类型
    s1 = '123'
    s2 = '3.14'
    s3 = 3
    s4 = False
    print(type(s1), type(s2), type(s3), type(s4))
    print(float(s1))  # 123.0
    print(float(s2))  # 3.14
    print(float(s3))  # 3.0
    print(float(s4))  # 0.0

## 注释

Python 使用 `#` 作为单行注释；使用三引号作为多行注释

    # 打印内容（单行注释）
    print('输入输出')

    '''
    我是
    多行
    注释
    '''

    """
    我也是
    多行注释
    且优先使用
    双引号多行注释
    """

## Python 中的保留字/关键字

    import keyword
    print(keyword.kwlist)
    # 如下为Python保留字
    ['False', 'None', 'True', '__peg_parser__',
    'and', 'as', 'assert', 'async', 'await',
    'break', 'class', 'continue', 'def', 'del',
    'elif', 'else', 'except', 'finally', 'for',
    'from', 'global', 'if', 'import', 'in', 'is',
    'lambda', 'nonlocal', 'not', 'or', 'pass',
    #'raise', 'return', 'try', 'while', 'with', 'yield']
