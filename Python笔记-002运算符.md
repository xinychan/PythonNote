# 运算符

## 算数运算符

    # 标准算数运算
    print(1 + 1)  # 加法；2
    print(1 - 1)  # 减法；0
    print(1 * 2)  # 乘法；2
    print(5 / 2)  # 除法；2.5
    print(5 // 2)  # 整除；2
    print(5 % 2)  # 取余运算；1
    print(5 ** 2)  # 幂运算；5的2次方=25

    # 整除（一正一负）
    print(-5 // 2)  # 整除（一正一负向下取整）；-3
    print(5 // -2)  # 整除（一正一负向下取整）；-3
    print(-5 // -2)  # 整除（都为正或都为负，则为正）；2

    # 取余（一正一负）：余数=被除数-除数*商
    print(-5 % 2)  # 取余运算；[(-5)-(2)*(-3)=(-5)+6=1]
    print(5 % -2)  # 取余运算；[5-(-2)*(-3)=5-6=-1]
    print(-5 % -2)  # 取余运算；都为正或负，余数前加对应正负号 -1

## 赋值运算符

    a = 20
    b = 20
    c = 20

    # 支持链式赋值
    # 链式赋值的变量指向同一个内存地址
    a2 = b2 = c2 = 20
    print(a2, id(a2))
    print(b2, id(b2))
    print(c2, id(c2))

    # 支持参数赋值
    parm = 20
    parm += 20
    print(parm)
    parm -= 20
    print(parm)
    parm *= 30
    print(parm)
    parm /= 10
    print(parm)

    # 支持系列解包赋值
    x, y, z = 10, 20, 30
    print(x, y, z)

    # 交换两个变量的值
    temp1, temp2 = 10, 20
    print('交换之前：', temp1, temp2)
    # 开始交换
    temp1, temp2 = temp2, temp1
    print('交换之后：', temp1, temp2)

## 比较运算符

    a, b = 10, 20
    print(a > b)
    print(a < b)
    print(a <= b)
    print(a >= b)
    print(a == b)
    print(a != b)

    """
    一个变量由三部分组成：标识，类型，值
    == 符号比较对象的值
    is/is not 符号比较对象的标识
    """

    a = 10
    b = 10
    print(a == b)  # True；值相等
    print(a is b)  # True；标识相等
    print(a is not b)  # False；标识相等

    list1 = [11, 22, 33, 44]
    list2 = [11, 22, 33, 44]
    print(list1 == list2)  # True；值相等
    print(list1 is list2)  # False；标识不相等
    print(list1 is not list2)  # True；标识不相等

## 布尔运算符

    a, b = 1, 2
    print(a == 1 and b == 2)  # True
    print(a == 1 and b != 2)  # False
    print(a != 1 and b == 2)  # False
    print(a != 1 and b != 2)  # False

    print(a == 1 or b == 2)  # True
    print(a == 1 or b != 2)  # True
    print(a != 1 or b == 2)  # True
    print(a != 1 or b != 2)  # False

    print(not True)  # False
    print(not False)  # True

    str_content = '123456'
    print('1' in str_content)  # True
    print('9' in str_content)  # False

    print('1' not in str_content)  # False
    print('9' not in str_content)  # True

## 位运算符

    # 按位与；同为1时结果为1
    print(4 & 8)  # 0

    # 按位或；同为0时结果为0
    print(4 | 8)  # 12

    # 左移位；相当于乘以2
    print(4 << 1)  # 8
    print(4 << 2)  # 16
    # 右移位；相当于除以2
    print(4 >> 1)  # 2
    print(4 >> 2)  # 1
