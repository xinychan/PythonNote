# 文件操作

## 文件的读写操作

    # 文件的读取；r 为读取模式；没有文件则抛出异常 FileNotFoundError
    file_name = open("name.txt", "r", encoding="UTF-8")
    print(file_name.readlines())
    file_name.close()

    # 文件的写入；w 为写入模式，文件不存在则创建；写入内容覆盖原内容
    file_name = open("name2.txt", "w", encoding="UTF-8")
    file_name.write("Python")
    file_name.close()

    # 文件的追加；a 为追加模式，文件不存在则创建；文件存在则新增内容
    file_name = open("name2.txt", "a", encoding="UTF-8")
    file_name.write("Python")
    file_name.close()

    # 二进制方式打开文件；b 为二进制打开文件；与写入或读取模式一起使用；可用于文件的拷贝
    file_name = open("name.txt", "rb")
    file_name_copy = open("name_copy.txt", "wb")
    file_name_copy.write(file_name.read())
    file_name.close()
    file_name_copy.close()

    # 以读写的/方式打开；+ 为读写方式打开；与写入或读取模式一起使用
    file_name = open("name2.txt", "r+", encoding="UTF-8")
    # 可以同时调用读取和写入的方法，不会抛出异常
    print(file_name.readlines())
    file_name.write("Python_r+")
    file_name.close()

## 文件操作的常用函数

    # file_name = open("name.txt", "r", encoding="UTF-8")
    # print(file_name.read())  # 读取指定size长度的内容；省略size则读取文件全部内容
    # print(file_name.readline())  # 读取一行内容
    # print(file_name.readlines())  # 读取全部内容，每次读取一行，返回一个列表
    # file_name.close()


    # file_name = open("name.txt", "w", encoding="UTF-8")
    # file_name.write("Python")  # 写入指定的内容
    # file_name.writelines(["Python", "Java"])  # 写入列表中的内容
    # file_name.close()


    file_name = open("name.txt", "r", encoding="UTF-8")
    file_name.seek(2)  # 移动指针到指定位置
    print(file_name.tell())  # 2；返回指针当前位置
    print(file_name.read())  # 读取指定size长度的内容；省略size则读取文件全部内容
    print(file_name.tell())  # 返回指针当前位置
    file_name.seek(0)  # 已经读取内容之后，需要调整指针位置到初始位置，才能继续读取内容
    print(file_name.tell())  # 返回指针当前位置
    print(file_name.readline())  # 读取一行内容
    print(file_name.tell())  # 返回指针当前位置
    file_name.seek(0)
    print(file_name.readlines())  # 读取全部内容，每次读取一行，返回一个列表
    file_name.flush()  # 缓冲区内容写入文件，但不关闭文件
    file_name.close()  # 关闭文件

## with 语句的使用

    # print(type(open("name.txt", "r", encoding="UTF-8")))  # <class '_io.TextIOWrapper'>；TextIOWrapper实例对象是上下文管理器
    # with open("name.txt", "r", encoding="UTF-8") as file_name:
    #     print(file_name.read())

    # 使用 with 语句可以自动管理上下文资源，上下文资源离开 with 语句范围，会自动释放资源
    # 使用 with 语句来释放资源的对象，必须遵守上下文管理器协议，对象内部都实现了 __enter__ 和 __exit__ 方法
    class MyContextManager(object):
        def __enter__(self):
            print("MyContextManager __enter__ called")
            return self

        def __exit__(self, exc_type, exc_val, exc_tb):
            print("MyContextManager __exit__ called")

        def show(self):
            print("MyContextManager show called")


    with MyContextManager() as context_mgr:
        context_mgr.show()

    """
    log信息：
    MyContextManager __enter__ called
    MyContextManager show called
    MyContextManager __exit__ called
    """

## os 模块的使用

    import os

    # # 打开记事本
    # os.system("notepad.exe")
    # # 打开计算器
    # os.system("calc.exe")
    # # 调用可执行文件
    # os.startfile(r"D:\ToolList\VSCode-win32-x64-1.44.2\Code.exe")

    # 返回当前工作目录
    print(os.getcwd())
    # 返回指定路径下的文件和目录
    print(os.listdir("../chap14"))
    # print(os.listdir(os.getcwd()))

    # # 创建目录
    # os.mkdir("mkdir_new")
    # # 创建多级目录
    # os.makedirs("mkdir/dir")
    # # 删除目录
    # os.rmdir("mkdir_new")
    # # 删除多级目录
    # os.removedirs("mkdir/dir")
    # # 将path设置为当前工作目录
    # os.chdir("../chap13")
    # print(os.getcwd())

## os.path 模块的使用

    import os

    # 获取文件或目录的绝对路径
    print(os.path.abspath("demo5.py"))

    # 判断文件或目录是否存在
    print(os.path.exists("demo5.py"))
    print(os.path.exists("demo50.py"))

    # 把目录与目录或文件名拼接
    print(os.path.join(r"E:\PyCharmProjects", "demo5.py"))

    # 分离文件名和目录名
    print(os.path.split(os.path.abspath("demo5.py")))

    # 分离文件名和扩展名
    print(os.path.splitext("demo5.py"))

    # 从文件路径中提取文件名
    print(os.path.basename(os.path.abspath("demo5.py")))

    # 从文件路径中提取文件目录路径，不包括文件名
    print(os.path.dirname(os.path.abspath("demo5.py")))

    # 判断是否是文件路径
    print(os.path.isdir(os.path.basename(os.path.abspath("demo5.py"))))
    print(os.path.isdir(os.path.dirname(os.path.abspath("demo5.py"))))

    # 使用 walk 遍历目录下所有文件，包括子目录和子目录中的子文件
    print("++++++++++++++++++++++++++++++++++++++++")
    file_list = os.walk(os.getcwd())
    for dirpath, dirname, filename in file_list:
        for dir in dirname:
            print(os.path.join(dirpath, dir))
        for file in filename:
            print(os.path.join(dirpath, file))
        print("*************************************")
