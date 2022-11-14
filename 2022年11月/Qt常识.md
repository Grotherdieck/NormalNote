

# 一、Qt Creator快捷键

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221113214810.png)

&emsp;&emsp;个人觉得比较常用的快捷键：``command shift r``（MacOs下）换掉所有用到这个符号的地方；``ctrl i``格式化文档。

# 二、qt主事件循环

&emsp;&emsp;所谓主事件循环，就是处理和分发来自操作系统和其他源的所有事件。它还处理应用程序的初始化与终结，以及系统范围和应用程序范围的设置。

- QcoreApplication:为非gui程序提供主事件循环；
- QGuiApplication:为gui程序提供主事件循环；
- QApplication：为qt widgets模块提供主事件循环。

&emsp;&emsp;qGuiApp：应用程序对象的全局指针，只有当应用程序对象是QGuiApplication时才有效。

&emsp;&emsp;不过更多情况还是用QApplication，它除了继承了QGuiApplication的功能外，还需负责初始化Qt Widget模块所需的资源，并且提供更多的接口，同样的也有一个qApp，是应用程序对象的全局指针，只有当应用程序对象是QApplication时才有效。

# 三、元对象系统

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221113224809.png)

&emsp;&emsp;就Qt可以在运行时获得QObject的类型与方法，并且还对这些内容可读可写，这就是它超越本来对象的地方。

&emsp;&emsp;这个内存管理中，Qt还提供了类似父子管理的方法，删除了父节点所有字节点的内存都会回首。

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221113225529.png)

&emsp;&emsp;moc处理后，会生成mocs开头的一些.cpp文件：

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221113225939.png)

&emsp;&emsp;注意：QObject不支持拷贝，因为QObject做了很多的事情，拷贝的话有很多东西就要考虑，为简单起见，就不支持了，所以经常我们在Qt中就是用指针指来指去。

```cpp
#include <QCoreApplication>

class A : public QObject
{
public:
    A(QObject* parent = nullptr);
    ~A() { qDebug() << this << "被销毁";}
};

A::A(QObject* parent) : QObject(parent)
{
    qDebug() << this << "被构造";
}

int main(int argc, char *argv[])
{
    // QCoreApplication a(argc, argv);
    A obja;
    obja.setObjectName("A1");
    A* pa1 = new A(&obja);
    pa1->setObjectName("A2");
    A* pa2 = new A(pa1);
    pa2->setObjectName("A3");
    obja.dumpObjectTree();
    // qDebug() << pa1;
    return 0;
    // return a.exec();
}
```

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221113231216.png)

# 四、事件与信号

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221114141048.png)

