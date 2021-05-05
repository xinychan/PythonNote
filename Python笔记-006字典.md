# 字典

## 字典的创建

    # 大括号直接创建
    dict1 = {"张三": 20, "李四": 30}
    print(dict1)

    # 使用dict函数创建
    dict1 = dict(name="zhangsan", age=18)
    print(dict1)

    # 创建空字典
    dict1 = {}
    print(dict1)

## 字典元素的获取

    dict1 = {"张三": 20, "李四": 30}

    # 使用[]获取，没有key则返回抛KeyError
    print(dict1["张三"])  # 20
    # print(dict1["王五"]) # KeyError: '张四'

    # 使用get方法，没有key则返回None
    print(dict1.get("张三"))  # 20
    print(dict1.get("王五"))  # None
    print(dict1.get("赵六", 60))  # 60；查不到，返回默认值

## 字典的增删改查

    # 字典的 key 判断
    dict1 = {"张三": 20, "李四": 30}
    print("张三" in dict1)  # True
    print("张三" not in dict1)  # False

    # 删除指定键值对
    dict1 = {"张三": 20, "李四": 30}
    del dict1["张三"]
    print(dict1)  # {'李四': 30}

    # 清空字典所有元素
    dict1 = {"张三": 20, "李四": 30}
    dict1.clear()
    print(dict1)  # {}

    # 新增字典元素，修改字典元素
    dict1 = {"张三": 20, "李四": 30}
    dict1["王五"] = 60
    print(dict1)  # {}
    dict1["王五"] = 80
    print(dict1)  # {}

    # 获取字典所有的key
    dict1 = {"张三": 20, "李四": 30}
    keys = dict1.keys()
    print(keys)
    print(type(keys))
    print(list(keys))

    # 获取字典所有的value
    dict1 = {"张三": 20, "李四": 30}
    values = dict1.values()
    print(values)
    print(type(values))
    print(list(values))

    # 获取字典所有的键值对
    dict1 = {"张三": 20, "李四": 30}
    items = dict1.items()
    print(items)
    print(type(items))
    print(list(items))

## 字典元素遍历

    dict1 = {"张三": 20, "李四": 30}
    for item in dict1:
        print(item, dict1[item], dict1.get(item))

## 字典的 key 必须是不可变对象

    # 字典的特点
    # key不重复，value可以重复
    # 字典元素是无序的
    # 字典的key必须是不可变对象
    list1 = [100, 200]
    dict1 = {"key1": 10, "key2": 20}
    # dict1 = {list1: 30} # TypeError: unhashable type: 'list'
    print(dict1)

## 字典生成式

    # 字典生成式；使用zip函数
    key1 = ["k1", "k2", "k3"]
    value1 = [10, 20, 30]
    dict1 = {my_key: my_value for my_key, my_value in zip(key1, value1)}
    print(dict1)
