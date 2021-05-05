# 面向对象

## 自定义对象

    class Student:
        # 定义在类中的变量，类属性
        place = "中国"

        # 初始化方法；内置方法
        def __init__(self, name, age):
            # 初始化方法中定义的变量，实例属性
            self.name = name
            self.age = age

        # 实例方法；实例方法必须带参数 self；self 指的是类实例对象本身
        def fun1(self):
            print("实例方法:fun1")

        # 静态方法；静态方法不带参数 self
        @staticmethod
        def fun2():
            print("静态方法:fun2")

        # 类方法；实例方法必须带参数 cls；cls 指的是类对象本身
        @classmethod
        def fun3(cls):
            print("类方法:fun3")

    # 实例对象
    student = Student("小明", 18)
    print(student)  # <__main__.Student object at 0x0000020C6AC77A60>
    print(id(student))  # 2252354320992
    print(type(student))  # <class '__main__.Student'>
    # 类对象
    print(Student)  # <class '__main__.Student'>
    print(id(Student))  # 2252348279696
    print(type(Student))  # <class 'type'>

## 对象的属性和方法

    class Student:
        # 定义在类中的变量，类属性
        place = "中国"

        # 初始化方法；内置方法
        def __init__(self, name, age):
            # 初始化方法中定义的变量，实例属性
            self.name = name
            self.age = age

        # 实例方法；实例方法必须带参数 self；self 指的是类实例对象本身
        def fun1(self):
            print("实例方法:fun1")

        # 静态方法；静态方法不带参数 self
        @staticmethod
        def fun2():
            print("静态方法:fun2")

        # 类方法；实例方法必须带参数 cls；cls 指的是类对象本身
        @classmethod
        def fun3(cls):
            print("类方法:fun3")

    student = Student("小明", 18)
    # 实例属性
    print(student.name)
    print(student.age)
    # 类属性
    print(student.place)
    print(Student.place)
    # 实例方法
    student.fun1()
    Student.fun1(student)
    # 静态方法
    student.fun2()
    Student.fun2()
    # 类方法
    student.fun3()
    Student.fun3()

## 动态绑定属性和方法

    class Student:
        # 定义在类中的变量，类属性
        place = "中国"

        # 初始化方法；内置方法
        def __init__(self, name, age):
            # 初始化方法中定义的变量，实例属性
            self.name = name
            self.age = age

        # 实例方法；实例方法必须带参数 self；self 指的是类实例对象本身
        def fun1(self):
            print("实例方法:fun1")

        # 静态方法；静态方法不带参数 self
        @staticmethod
        def fun2():
            print("静态方法:fun2")

        # 类方法；实例方法必须带参数 cls；cls 指的是类对象本身
        @classmethod
        def fun3(cls):
            print("类方法:fun3")

    # 动态绑定属性和方法
    student1 = Student("小明", 18)
    student2 = Student("小红", 18)
    # 绑定属性
    student1.phone = "Apple"
    student2.watch = "XiaoTianCai"
    print(student1.name, student1.phone)
    print(student2.name, student2.watch)

    # 绑定方法
    def info():
        print("show info")

    student1.info = info
    student1.info()

## 对象的封装

    # 属性和方法的封装
    class Student:
        def __init__(self, name, age):
            self.name = name
            self.__age = age  # 私有属性，仅类内部调用，外部不允许调用

        def show(self):
            print(self.name, self.__age)

    student1 = Student("小明", 18)
    student1.show()
    print(student1.name)
    # print(student1.__age) 私有属性，外部不允许调用
    print(dir(student1))  # 打印类中的方法和属性
    print(student1._Student__age)  # 类的外部通过 _Student__age 强制访问私有属性

## 对象的继承

### 继承的使用

    # 继承；所有的对象都直接间接继承自 object
    class Person(object):
        def __init__(self, name, age):
            self.name = name
            self.age = age

        def info(self):
            print(self.name, self.age)

    # 括号中为继承自的父类对象；Python支持多继承
    class Student(Person):
        def __init__(self, name, age, number):
            super().__init__(name, age)
            self.number = number

    class Teacher(Person):
        def __init__(self, name, age, level):
            super().__init__(name, age)
            self.level = level

    student = Student("小明", 18, "001")
    student.info()
    teacher = Teacher("语文", 28, "高级")
    teacher.info()

### 多继承

    # 多继承
    class AFun(object):
        pass

    class BFun(object):
        pass

    # CFun同时继承AFun/BFun
    class CFun(AFun, BFun):
        pass

    cfun = CFun()
    print(type(cfun))
    # cfun 是 AFun/BFun/CFun 类型的实例
    print(isinstance(cfun, AFun))  # True
    print(isinstance(cfun, BFun))  # True
    print(isinstance(cfun, CFun))  # True
    # CFun 是 AFun/BFun/CFun 类型的子类
    print(issubclass(CFun, AFun))  # True
    print(issubclass(CFun, BFun))  # True
    print(issubclass(CFun, CFun))  # True

## 对象的多态

    """
    静态语言的多态：
    必须继承；必须方法重写；父类引用指向子类对象
    动态语言的多态：“鸭子类型”
    当一只鸟走路像鸭子，游泳像鸭子，那么这只鸟就可以称为鸭子。
    动态语言的多态，不关心对象的类型，只关心对象的行为。
    """

    class Animal(object):
        def eat(self):
            print("Animal eat")

    class Dog(Animal):
        def eat(self):
            print("Dog eat")

    class Cat(Animal):
        def eat(self):
            print("Cat eat")

    class Person(object):
        def eat(self):
            print("Person eat")

    # fun函数中，调用对象的eat方法
    def fun(animal):
        animal.eat()

    # 多态的具体实现；只要传入的参数带有 eat 方法即可
    fun(Person())
    fun(Animal())
    fun(Dog())
    fun(Cat())

## 对象的特殊属性

    class A:
        pass

    class B:
        pass

    class C(A, B):
        place = "中国"

        def __init__(self, name, age):
            self.name = name
            self.age = age

        @classmethod
        def show(cls):
            return "show:place={0}".format(cls.place)

    subC = C("Java", 18)
    # 实例对象中的所有方法和属性
    print(dir(subC))
    # 类对象中的所有方法和属性
    print(dir(C))

    """
    实例对象的所有实例属性，{'name': 'Java', 'age': 18}
    """
    print(subC.__dict__)
    """
    类对象的所有类属性和方法
    {'__module__': '__main__', 'place': '中国', '__init__': <function C.__init__ at 0x000002940BB4D430>,
    'show': <classmethod object at 0x000002940BB56FD0>, '__doc__': None}
    """
    print(C.__dict__)
    """
    实例对象的类型
    <class '__main__.C'>
    """
    print(subC.__class__)
    """
    类对象的类型
    <class 'type'>
    """
    print(C.__class__)
    """
    C类的父类元组
    (<class '__main__.A'>, <class '__main__.B'>)
    """
    print(C.__bases__)
    """
    C类的层次结构
    (<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>)
    """
    print(C.__mro__)
    """
    A类的子类列表
    [<class '__main__.C'>]
    """
    print(A.__subclasses__())

## 对象的特殊方法

### __add__ 方法和 __len__ 方法

    class Student:
        def __init__(self, name):
            self.name = name

        # 重写 __add__ 对象可实现加法运算
        def __add__(self, other):
            return self.name + other.name

        # 重写 __len__ 对象可计算长度
        def __len__(self):
            return len(self.name)


    stu1 = Student("Java")
    stu2 = Student("Python")
    # 重写 __add__ 对象可实现加法运算
    new_stu = stu1 + stu2
    print(new_stu)
    new_stu = stu2.__add__(stu2)
    print(new_stu)
    # 重写 __len__ 对象可计算长度
    print(len(stu1))
    print(stu2.__len__())

### __new__ 方法和 __init__ 方法

    class Person(object):
        def __init__(self, name, age):
            print("__init__ 开始调用，实例对象的 id:{0}".format(id(self)))
            self.name = name
            self.age = age

        def __new__(cls, *args, **kwargs):
            print("__new__ 开始调用，类对象的 id:{0}".format(id(cls)))
            newCls = super().__new__(cls)
            print("__new__ 调用完成，创建的对象 id:{0}".format(id(newCls)))
            return newCls


    print("object类对象：", id(object))
    print("Person类对象：", id(Person))
    p1 = Person("Java", 18)
    print("Person实例对象：", id(p1))

    """
    执行log：
    object类对象： 140719148129792
    Person类对象： 1775829927024
    __new__ 开始调用，类对象的 id:1775829927024
    __new__ 调用完成，创建的对象 id:1775835839072
    __init__ 开始调用，实例对象的 id:1775835839072
    Person实例对象： 1775835839072
    """

## 对象的浅拷贝与深拷贝

    # 浅拷贝与深拷贝
    import copy

    class CPU:
        pass

    class Disk:
        pass

    class Computer:
        def __init__(self, cpu, disk):
            self.cpu = cpu
            self.disk = disk

    # 变量的赋值
    cpu1 = CPU()
    cpu2 = cpu1
    # 赋值，两个变量指向同一个引用，内存地址相同
    print(cpu1, id(cpu1))
    print(cpu2, id(cpu2))

    # 类的浅拷贝
    myCpu = CPU()
    myDisk = Disk()
    # 浅拷贝，只拷贝Computer，Computer对象不同；但是Computer中的CPU/Disk未拷贝，是相同的
    myComputer = Computer(myCpu, myDisk)
    computer1 = copy.copy(myComputer)
    print(myComputer, myComputer.cpu, myComputer.disk)
    print(computer1, computer1.cpu, computer1.disk)

    # 类的深拷贝
    myCpu = CPU()
    myDisk = Disk()
    # 深拷贝，不光拷贝Computer，也拷贝Computer中的CPU/Disk，Computer/CPU/Disk都不是相同的
    myComputer = Computer(myCpu, myDisk)
    computer2 = copy.deepcopy(myComputer)
    print(myComputer, myComputer.cpu, myComputer.disk)
    print(computer2, computer2.cpu, computer2.disk)