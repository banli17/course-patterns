---
title: 设计模式简介
sidebar_label: 简介
---

设计模式是一套让代码可重用，可读，可靠的经验总结。它可以分为三类：

-   创建型模式：对象实例化的模式，创建型模式用于解耦对象的实例化过程。
-   结构型模式：把类或对象结合在一起形成一个更大的结构。
-   行为型模式：类和对象如何交互，及划分责任和算法。

## 面向对象和 UML 类图

### 面向对象的意义

面向对象的本质实际是对数据进行结构化，即归类，这是为了更加方便的管理代码。对于计算机来说，结构化的才是最简单的。

面向对象的三要素: 继承、封装、多态

继承

js 里通过 extends 来继承类。

```javascript
class Person {
    constructor(name) {
        this.name = name;
    }
}

class Student extends Person {
    constructor(name, classroom) {
        super(name);
        this.classroom = classroom;
    }
    study() {
        //...
    }
}
```

封装

面向对象语言中的封装是通过下面三个关键词来限定属性、方法的访问权限。

-   `public`: 公开的，父类、子类、实例都可以访问。
-   `protected`: 保护的，父类、子类可以访问。
-   `private`: 私有的，只有当前类可以访问。

在 js 中没有这种语法，可以使用 typescript 来规范。

多态

多态是子类可以重写父类的方法，或者同名方法可以根据参数个数或类型的不同表示不同功能。

### UML 类图

UML 类图用来描述类和类之间的关系。

每个类有类名，属性和方法。

-   `public`使用 + 号
-   `protected`使用 # 号
-   `private`使用 - 号

**关系**

-   泛化：表示继承，使用空心箭头。
-   关联：表示引用，使用实心箭头

上面的这张图表示 A,B 类继承自 Person 类，Person 中引用了 House 类。

## 设计原则与编程技巧

### 什么是设计

unix/linux 设计哲学一书的总结：

1. 小即是美。
2. 让每个程序只做好一件事。
3. 快速建立原型，给用户用，使用过程中根据反馈和自己的规划继续完成。
4. 舍弃高效率而取可移植性，可移植性>高效率，因为计算机配置是不断升高的。
5. 采用纯文本来存储数据，即可读性，让适合人阅读，不要用二进制之类。
6. 充分利用软件的杠杆效应(软件复用)。
7. 使用 shell 脚本来提高杠杆效应和可移植性。
8. 避免强制性的用户界面。
9. 让每个程序都称为过滤器。

小准则：

1. 允许用户定制环境。
2. 尽量使操作系统内核小而轻量化。
3. 使用小写字母并尽量简短。
4. 沉默是金。
5. 各部分之和大于整体。
6. 寻求 90% 的解决方案。不要什么都做到完美，因为会耗费很大精力。

### SOLID 五大设计原则

-   S: 单一职责原则：一个程序只做好一件事，如果功能复杂就拆分开
-   O: 开放封闭原则：对扩展开放，对修改封闭。增加需求时，扩展新代码，而非修改已有代码。
-   L: 李氏置换原则：子类能覆盖父类，父类能出现的地方子类就能出现，js 使用较少（继承使用较少）。
-   I: 接口独立原则：保持接口的单一独立，避免出现胖接口。js 没有接口，使用较少。
-   D: 依赖倒置原则：面向接口编程，依赖于抽象而不依赖于具体，使用方只关注接口而不关注具体类的实现。js 中使用较少(没有接口&弱类型)。

### 第二题

1. 某停车场，分 3 层，每层 100 车位
2. 每个车位能监控到车辆的驶入和离开
3. 车辆进入前，显示每层的空余车位数量
4. 车辆进入时，摄像头可识别车辆号和时间
5. 车辆出来时，出口显示器显示车牌号和停车时长