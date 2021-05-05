# 列表

列表是有序的，支持下标索引的数据结构

## 列表的创建

    list1 = [1, 2, 3]
    print(id(list1))
    print(type(list1))
    print(list1)

    list2 = list(["python", "list", 100])
    print(id(list2))
    print(type(list2))
    print(list2)

## 获取列表索引

    list1 = ['1', '2', '3', '4', '1', '2', '3']
    print(list1.index('3'))  # 返回元素的第一个索引
    # print(list1.index('10'))  # ValueError: 10 is not in list
    print(list1.index('1', 1, 5))  # 在索引1-5的位置查找‘1’

## 获取列表元素

    list1 = ['1', '2', '3', '4']
    print(list1[1])  # 正向索引查找
    print(list1[-1])  # 逆向索引查找
    # print(list1[10]) # IndexError: list index out of range

## 列表的切片

    # 获取列表中多个元素，列表的切片
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    # 切片，start=1,end=6,step=1
    list2 = list1[1:6:1]  # 切片后是一个新的列表，原列表不变
    # list2 = list1[1:6]
    # list2 = list1[:6:]
    print(list1)  # [10, 20, 30, 40, 50, 60, 70, 80]
    print(list2)  # [20, 30, 40, 50, 60]
    # 步长为负数，则倒数开始计算
    list3 = list1[::-1]
    print(list3)
    list4 = list1[6:0:-2]
    print(list4)

## 列表元素的判断和遍历

    # 列表元素的判断
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    print(10 in list1)
    print(100 in list1)
    print(10 not in list1)
    print(100 not in list1)
    # 列表遍历
    for item in list1:
        print(item)

## 列表增加元素

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    # 列表中增加一个元素；不论元素是什么类型，都增加到列表中，且整体作为一个元素添加到末尾
    # list1.append(100)
    list1.append([90, 100])  # [10, 20, 30, 40, 50, 60, 70, 80, 100, [90, 100]]
    print(list1)

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    # 列表中增加一个或多个元素；会将元素拆开，添加到列表末尾
    list1.extend([90, 100])  # [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
    print(list1)

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    # 列表指定位置添加一个元素；指定位置添加元素
    list1.insert(0, [10, 20])  # [10, 10, 20, 30, 40, 50, 60, 70, 80]
    print(list1)

    list1 = [10, 20, 30]
    list2 = ["python", "hello"]
    # 列表指定位置添加多个元素；指定位置添加多个元素；通过切片
    list2[1:] = list1  # ['python', 10, 20, 30]；将list1中元素，添加到list2中切片位置
    print(list2)

## 列表删除元素

    # 列表的删除
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1.remove(30)  # 移除列表中已存在的元素；若重复则移除第一个
    print(list1)
    # list1.remove(100) # ValueError: list.remove(x): x not in list

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1.pop(1)  # 依据索引移除元素
    print(list1)
    # list1.pop(10)  # IndexError: pop index out of range

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1.pop()  # 默认删除最后一个元素
    print(list1)

    # 切片；可用于删除多个元素
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    new_list = list1[1:4]
    print(new_list)

    # 切片；可用于删除多个元素
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1[1:4] = []
    print(list1)

    # 清空列表元素
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1.clear()
    print(list1)

    # 删除列表
    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    del list1
    # print(list1) # NameError: name 'list1' is not defined

## 列表修改元素

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1[1] = 200  # 依据索引修改值
    print(list1)

    list1 = [10, 20, 30, 40, 50, 60, 70, 80]
    list1[1:3] = [200, 300]  # 使用切片修改值
    print(list1)

## 列表的排序

    list1 = [50, 20, 30, 10, 40]
    print(list1)

    list1.sort()  # list.sort() 函数默认升序排序
    print(list1)

    list1.sort(reverse=True)  # reverse参数设置True，降序排序
    print(list1)

    list1 = [50, 20, 30, 10, 40]
    new_list = sorted(list1)  # sorted() 函数默认升序排序；赋值给新列表
    print(new_list)
    new_list = sorted(list1, reverse=True)  # reverse参数设置True，降序排序；赋值给新列表
    print(new_list)

## 列表生成式

通过列表生成式来创建列表

    list1 = [i for i in range(1, 6)]
    print(list1)  # [1, 2, 3, 4, 5]

    list1 = [i * 2 for i in range(1, 6)]
    print(list1)  # [2, 4, 6, 8, 10]
