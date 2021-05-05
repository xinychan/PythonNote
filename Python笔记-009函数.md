# 函数

## 函数的定义与调用

    # a,b;形参；方法定义处为形参
    def caladd(a, b):
        c = a + b
        return c

    # a=5,b=5；位置实参；方法调用处为实参
    res = caladd(5, 5)
    print(res)

    # a=5,b=10；关键字实参；方法调用处为实参
    res = caladd(b=10, a=5)
    print(res)

## 函数的参数传递

    # 函数的参数传递
    def fun(arg1, arg2):
        print(arg1, arg2)  # 10 [1, 2, 3]
        arg1 = 100
        arg2.append(10)  # 100 [1, 2, 3, 10]
        print(arg1, arg2)
        return


    n1 = 10
    n2 = [1, 2, 3]
    print(n1, n2)  # 10 [1, 2, 3]
    fun(n1, n2)
    print(n1, n2)  # 10 [1, 2, 3, 10]

    """
    函数调用过程中，进行参数的传递
    如果是不可变对象，函数体内的修改不会影响实参的值
    如果是可变对象，函数体内的修改会影响实参的值
    """

## 函数返回值

    """
    函数的返回值
    如果函数没有返回值，return可以省略
    函数返回值数量为1，直接返回该类型
    函数返回值数量为多个，返回元组
    """

    def fun1(a, b):
        return a + b

    def fun2(a, b):
        return a * a, b * b

    print(fun1(10, 10))  # 20
    print(fun2(10, 10))  # (100, 100)

## 函数的参数定义

    # 默认值参数
    def fun(a, b=10):
        return a, b

    print(fun(5))  # (5, 10)
    print(fun(5, 6))  # (5, 6)

    # 个数可变的位置参数
    def fun2(*args):
        # 参数类型为元组
        print(args)  # (1, 2, 3)
        for arg in args:
            print(arg)

    fun2(1, 2, 3)

    # 个数可变的关键字参数
    def fun3(**args):
        # 参数类型为字典
        print(args)  # {'a': 10, 'b': 20, 'c': 30}
        for arg in args:
            print(arg)

    fun3(a=10, b=20, c=30)

    # 个数可变的位置参数，要定义在个数可变的关键字参数之前
    def fun4(*arg1, **agr2):
        pass

## 参数使用总结

    # 位置实参与关键字实参
    def fun(a, b, c):
        print(a, b, c)

    # 位置参数实参
    fun(1, 2, 3)
    # 将列表中的每个元素都转为位置实参
    list1 = [10, 20, 30]
    fun(*list1)
    # 关键字参数实参
    fun(a=4, b=5, c=6)
    # 将字典中的每个元素都转为关键字实参
    dict1 = {"a": 7, "b": 8, "c": 9}
    fun(**dict1)

    # 关键字形参；从*之后的参数，传入时必须使用关键字实参
    def fun2(a, b, *, c, d):
        print(a, b, c, d)

    fun2(1, 2, c=3, d=4)  # 后两个参数必须使用关键词实参

## 变量作用域

    # 局部变量
    def fun(a, b):
        # abc为局部变量，仅在方法体内部使用
        c = a + b
        print(c)

    name = "Python"

    # 全局变量
    def fun2():
        # name为全局变量，在方法体内部和外部都可以使用
        print(name)

    fun2()

    # 局部变量转全局变量
    def fun3():
        # 函数内部定义的局部变量，使用global关键字，转为全局变量
        global age
        age = 20
        print(age)

    fun3()
    # 必须先调用fun3()函数，然后才能访问到age变量；否则：NameError: name 'age' is not defined
    print(age)
