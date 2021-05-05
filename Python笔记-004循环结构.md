# 循环结构

## 函数 range()

    # 函数 range()：生成一个整数序列
    # 返回值是一个迭代器对象
    # range类型优点：不管range序列有多长，所有range对象的内存空间相同；仅仅需要存储start,stop,step；
    # 只有用到range对象时，才会计算序列中的元素。

    # range的定义
    range1 = range(10)
    range2 = range(1, 11)
    range3 = range(1, 10, 2)

    # 查看range中的序列，使用list函数包装range
    print(range1)  # range(0, 10)
    print(list(range1))  # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    print(range2)  # range(1, 11)
    print(list(range2))  # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    print(range3)  # range(1, 10, 2)
    print(list(range3))  # [1, 3, 5, 7, 9]
    # in/not in 判断是否在range中
    print(5 in range1)  # True
    print(5 not in range1)  # False
    print(11 in range1)  # False
    print(11 not in range1)  # True

## while 循环

    # 求和
    sum = 0
    a = 0
    while a < 5:
        sum += a
        a += 1
    print(sum)

## for-in 循环

    for item in "python":
        print(item)

    for index in range(10):
        print(index)

    # 循环体中不需要使用自定义的变量，自定义变量可使用下划线"_"
    for _ in range(5):
        print("人生苦短，我用Python")

## break 语句

    # break 语句用于跳出循环体
    a = 0
    while a < 3:
        content = input("密码：")
        if content == "666":
            print("密码正确")
            break
        else:
            print("密码错误")
        a += 1

## continue 语句

    # continue 语句用于跳出当前循环
    """输出1-50之间5的倍数"""
    for item in range(1, 51):
        if item % 5 != 0:
            continue
        print(item)

## else 语句

    for item in range(3):
        content = input("密码：")
        if content == "666":
            print("密码正确")
            break
        else:
            print("密码错误")
    else:
        print("已经输入三次")
