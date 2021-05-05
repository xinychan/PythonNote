# 异常处理

## 异常类型与捕获异常

### try/except 结构

    try:
        arg1 = input("输入参数1：")
        num1 = int(arg1)
        arg2 = input("输入参数2：")
        num2 = int(arg2)
        result = num1 / num2
        print("相除结果：", result)
    except ValueError:
        print("请输入数字")
    except ZeroDivisionError:
        print("除数不能为0")
    except BaseException as e:
        print("异常：", e)
    print("程序结束")

### try/except/else 结构

    try:
        arg1 = input("输入参数1：")
        num1 = int(arg1)
        arg2 = input("输入参数2：")
        num2 = int(arg2)
        result = num1 / num2
    except BaseException as e:  # 发生异常执行的逻辑
        print("出错：", e)
    else:  # 未发生异常执行的逻辑
        print("结果：", result)

### try/except/else/finally 结构

    try:
        arg1 = input("输入参数1：")
        num1 = int(arg1)
        arg2 = input("输入参数2：")
        num2 = int(arg2)
        result = num1 / num2
    except BaseException as e:  # 发生异常执行的逻辑
        print("出错：", e)
    else:  # 未发生异常执行的逻辑
        print("结果：", result)
    finally:  # 不论是否异常，最终总会执行的逻辑
        print("总会执行的代码")

## traceback 模块打印异常信息

    import traceback

    try:
        print(1 / 0)
    except:
        traceback.print_exc()

## 主动抛出异常

    try:
        score = int(input("请输入分数："))
        if 0 <= score <= 100:
            print(f"分数为{score}")
        else:
            raise Exception("分数不正确")  # 主动抛出异常
    except Exception as e:
        print(e)
