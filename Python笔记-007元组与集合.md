# 元组与集合

## 元组的创建

元组是不可变序列，不可以增删改

    # 使用()创建
    tuple1 = ("t1", "t2", 10)
    print(tuple1)
    tuple1 = "t1", "t2", 20  # 省略小括号
    print(tuple1)

    # 使用tuple函数创建
    tuple2 = tuple(("t1", "t2", 30))
    print(tuple2)
    print(type(tuple2))

    # 只包含一个元素的元组
    tuple3 = ("python",)
    print(tuple3)
    print(type(tuple3))

    # 空元组
    tuple4 = ()
    tuple5 = tuple()
    print(tuple4)
    print(type(tuple4))
    print(tuple5)
    print(type(tuple5))

## 元组元素不可变

    t = (10, [20, 30], 40)
    print(t, type(t))
    print(t[0], type(t[0]))  # 10 <class 'int'>
    print(t[1], type(t[1]))  # [20, 30] <class 'list'>
    print(t[2], type(t[2]))  # 40 <class 'int'>

    # 元组的元素不可变；若元素本身是可变对象，其元素中的值可变，但对象本身引用不变
    list1 = t[1]
    print(list1, id(list1))
    list1[0] = 30
    print(list1, id(list1))

## 元组的遍历

    t = (10, 20, 30)
    for i in t:
        print(i)

## 集合的创建

set 集合中元素不重复，且无序

    set1 = {1, "Python", 2, 3, 4, 3, 2}
    print(set1)  # {1, 2, 3, 4, 'Python'};set集合中元素不重复，且无序

    set2 = set(range(6))
    print(set2)
    set2 = set([1, 3, 5, 7])
    print(set2)
    set2 = set((7, 5, 3, 1))
    print(set2)
    set2 = set("python")
    print(set2)  # {'y', 'o', 't', 'h', 'p', 'n'};set集合会把字符串拆分
    set2 = set({7, 5, 3, 10})
    print(set2)
    set2 = set()
    print(set2)  # set()；空集合

## 集合的操作

    # 集合元素的判断
    set1 = {10, 20, 30, 40, 50}
    print(10 in set1)
    print(10 not in set1)

    # 集合元素的新增
    # 一次新增一个元素
    set1 = {10, 20, 30, 40, 50}
    set1.add(60)
    print(set1)
    # 一次新增多个元素
    set1 = {10, 20, 30, 40, 50}
    set1.update([70, 80, 100])
    print(set1)  # {80, 50, 20, 100, 70, 40, 10, 30}
    set1 = {10, 20, 30, 40, 50}
    set1.update({70, 80, 101})
    print(set1)
    set1 = {10, 20, 30, 40, 50}
    set1.update((70, 80, 102))
    print(set1)

    # 集合元素的删除
    set1 = {10, 20, 30, 40, 50}
    set1.remove(10)
    print(set1)  # {50, 20, 40, 30}
    set1 = {10, 20, 30, 40, 50}
    # set1.remove(100)  # KeyError: 100;元素在集合中不存在
    set1.discard(100)  # 删除不存在元素，不会抛异常
    set1 = {10, 20, 30, 40, 50}
    set1.pop()
    print(set1)  # {20, 40, 10, 30};删除其中一个元素
    set1 = {10, 20, 30, 40, 50}
    set1.clear()
    print(set1)  # set()：清空集合元素

    # 集合的遍历
    set1 = {10, 20, 30, 40, 50}
    for i in set1:
        print(i)

## 集合的关系

    # 相等判断，元素相同则相等
    s1 = {10, 20, 30, 40}
    s2 = {40, 20, 30, 10}
    print(s1 == s2)  # True

    # 子集判断
    s1 = {10, 20, 30, 40}
    s2 = {10, 20, 30}
    s3 = {10, 20, 60}
    print(s2.issubset(s1))  # True
    print(s3.issubset(s1))  # False

    # 超集判断
    s1 = {10, 20, 30, 40}
    s2 = {10, 20, 30}
    s3 = {10, 20, 60}
    print(s1.issuperset(s2))  # True
    print(s1.issuperset(s3))  # False

    # 交集判断
    s1 = {10, 20, 30, 40}
    s2 = {100, 200, 300}
    s3 = {10, 20, 60}
    print(s1.isdisjoint(s2))  # True;没有交集返回True
    print(s1.isdisjoint(s3))  # False；

## 集合的数学操作

    s1 = {10, 20, 30, 40}
    s2 = {10, 20, 50, 60}
    # 取交集
    print(s1.intersection(s2))  # {10, 20}
    print(s1 & s2)
    # 取并集
    print(s1.union(s2))  # {40, 10, 50, 20, 60, 30}
    print(s1 | s2)
    # 取差集
    print(s1.difference(s2))  # {40, 30}
    print(s1 - s2)
    # 取对称差集
    print(s1.symmetric_difference(s2))  # {40, 50, 60, 30}
    print(s1 ^ s2)

## 集合生成式

    s1 = {i * 2 for i in range(6)}
    print(s1)  # {0, 2, 4, 6, 8, 10}
