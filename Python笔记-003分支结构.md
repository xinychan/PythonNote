# 分支结构

## 顺序结构

    """把大象放冰箱分几步？"""
    print("1-冰箱门打开")
    print("2-大象放冰箱")
    print("3-冰箱门关闭")

## 布尔值的判断

Python 一切皆对象，所有对象都有一个布尔值
获取对象的布尔值：内置函数 bool()

    print(bool(False))
    print(bool(0))
    print(bool(0.0))
    print(bool(None))
    print(bool(''))
    print(bool(""))
    # 空列表
    print(bool([]))
    print(bool(list()))
    # 空元组
    print(bool(()))
    print(bool(tuple()))
    # 空字典
    print(bool({}))
    print(bool(dict()))
    # 空集合
    print(bool(set()))
    print("------------以上对象的布尔值为False-----------------")
    print("------------其余对象的布尔值为True-----------------")
    print(bool(20))

## 选择结构

    money = 1000
    getMoney = int(input("取款金额："))
    if getMoney <= money:
        money = money - getMoney
        print("剩余余额：", money)
    else:
        print("余额不足")

    score = int(input("分数："))
    if score >= 90 and score <= 100:
        print("优秀")
    elif score >= 70 and score < 90:
        print("良好")
    elif score >= 60 and score < 70:
        print("及格")
    else:
        print("不及格")

    # 简化写法：90 <= score <= 100
    score = int(input("分数："))
    if 90 <= score <= 100:
        print("优秀")
    elif 70 <= score < 90:
        print("良好")
    elif 60 <= score < 70:
        print("及格")
    else:
        print("不及格")

    # 条件表达式；满足条件结果为前面的值，不满足条件结果为 else 后面的值
    print("整数1比整数2大" if num1 >= num2 else "整数1比整数2小")

## pass 语句

    # pass 语句什么都不做，只是一个占位符，用在语法上需要语句的地方
    is_vip = input("是会员吗？ y/n")
    # 当未具体实现功能时，使用 pass 占位，避免语法错误
    if is_vip == "y":
        pass
    else:
        pass
