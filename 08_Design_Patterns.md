# Chapitre 08 --- Design Patterns (Patrons de Conception) / 设计模式

> **来源课件**: `CM_9_Les modeles de Conception (Design Patterns).pdf` (21页)
> **授课教师**: Dr. Fatiha Bousbahi

---

## 章节目录

1. [SOLID原则——设计模式的理论基石](#1-solid原则设计模式的理论基石)
2. [设计模式的定义与目标](#2-设计模式的定义与目标)
3. [设计模式的三大分类](#3-设计模式的三大分类)
4. [创建型模式——对象的"出生"管理](#4-创建型模式对象的出生管理)
5. [结构型模式——类与对象的"排列组合"](#5-结构型模式类与对象的排列组合)
6. [行为型模式——对象间的"通信协议"](#6-行为型模式对象间的通信协议)

---

## 1. SOLID原则——设计模式的理论基石

课件在进入设计模式前,先回顾了SOLID五原则。这些原则是设计模式的"为什么"。

### 1.1 SOLID全解

| 字母 | 原则 | 法文 | 核心含义 |
|------|------|------|---------|
| **S** | 单一职责 | Responsabilite unique (SRP) | 一个类应该只有一个改变的理由 |
| **O** | 开闭原则 | Ouvert/Ferme (OCP) | 对扩展开放,对修改关闭 |
| **L** | 里氏替换 | Substitution de Liskov (LSP) | 子类应该能替换父类而不破坏程序 |
| **I** | 接口隔离 | Segregation des interfaces (ISP) | 不应强迫客户端依赖它们不用的接口 |
| **D** | 依赖反转 | Inversion de dependance (DIP) | 依赖抽象而非具体实现 |

### 1.2 SOLID与设计模式的关系

设计模式是SOLID原则的**具体化**: 每个设计模式都体现了SOLID中的一个或多个原则。例如:
- **策略模式** -> 体现了OCP(开闭原则)和DIP(依赖反转)
- **观察者模式** -> 体现了SRP(单一职责)和OCP
- **工厂模式** -> 体现了DIP(依赖反转)

---

## 2. 设计模式的定义与目标

### 2.1 定义

> *Un patron de conception (Design Pattern) est une solution a un probleme recurrent dans un contexte donne.*
> 设计模式是对**特定上下文中反复出现的问题**的一种解决方案。

### 2.2 四大目标

课件给出了设计模式的四个核心目标:

| 目标 | 法文 | 深层解读 |
|------|------|---------|
| **模块化** | modulaires | 系统被分解为独立、可替换的模块 |
| **可复用** | reutilisables | 同样的解决方案可以在不同场景中使用 |
| **可扩展** | extensibles | 新增功能不需要修改现有代码 |
| **可维护** | maintenables | 代码易于理解和修改 |

### 2.3 额外价值

- 建立**通用词汇表**: 开发者说"这里用Observer"大家都明白
- 促进**UML建模**: 设计模式天然与UML类图匹配

---

## 3. 设计模式的三大分类

GoF (Gang of Four) 将23种经典设计模式分为三类:

| 类别 | 法文 | 关注点 | 典型模式 |
|------|------|--------|---------|
| **创建型** | Creation | 对象创建过程 | Singleton, Factory, Builder, Prototype, Abstract Factory |
| **结构型** | Structure | 类/对象的组合方式 | Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy |
| **行为型** | Comportement | 对象间的交互和职责分配 | Observer, Strategy, Command, State, Template Method, Iterator, Mediator, Memento, Chain of Responsibility, Visitor, Interpreter |

---

## 4. 创建型模式——对象的"出生"管理

### 4.1 5种创建型模式总览

| 模式 | 法文 | 核心问题 | 典型场景 |
|------|------|---------|---------|
| **单例** | Singleton | 如何确保一个类只有一个实例? | 数据库连接、日志管理器、游戏中的玩家对象 |
| **工厂方法** | Factory Method | 如何让子类决定创建哪个具体对象? | GUI框架中不同OS创建不同按钮 |
| **抽象工厂** | Abstract Factory | 如何创建一系列相关对象? | 跨平台UI组件族 |
| **建造者** | Builder | 如何分步骤构建复杂对象? | StringBuilder, 复杂文档生成 |
| **原型** | Prototype | 如何通过克隆创建对象? | 对象的深拷贝、游戏中的怪物生成 |

### 4.2 Singleton深度分析 (课件重点讲解)

**定义**: 确保一个类**只有一个实例**,并提供全局访问点。

**典型应用**:
- 数据库连接 (Connection a la base de donnees)
- 游戏中的玩家对象 (Objet representant le joueur)
- 游戏中的活跃图形对象 (Objets graphiques actifs)

**注意事项 (课件警告)**:
- Singleton类似于**全局变量**,引入了隐式依赖
- "很少是问题的正确答案"(Il est assez rare que ce soit la bonne reponse)
- 在框架中被广泛使用(如JEE),但过度使用会导致**紧耦合**

---

## 5. 结构型模式——类与对象的"排列组合"

### 5.1 7种结构型模式总览

| 模式 | 法文 | 核心问题 | 类比 |
|------|------|---------|------|
| **适配器** | Adapter | 如何让不兼容的接口一起工作? | 电源转换插头 |
| **桥接** | Bridge | 如何分离抽象和实现? | 遥控器(抽象) vs 电视品牌(实现) |
| **组合** | Composite | 如何统一处理单个对象和对象集合? | 文件系统中的文件和文件夹 |
| **装饰器** | Decorator | 如何动态添加职责? | 层层包装: 咖啡 + 牛奶 + 糖 |
| **外观** | Facade | 如何为复杂子系统提供简单接口? | 一键开机(封装了电源/BIOS/OS...的复杂度) |
| **享元** | Flyweight | 如何高效共享大量细粒度对象? | 文字处理中的字符对象池 |
| **代理** | Proxy | 如何控制对对象的访问? | 信用卡(银行账户的代理) |

---

## 6. 行为型模式——对象间的"通信协议"

### 6.1 11种行为型模式 (课件列出)

| 模式 | 法文 | 核心问题 |
|------|------|---------|
| **责任链** | Chain of Responsibility | 如何让多个对象都有机会处理请求? |
| **命令** | Command | 如何将请求封装为对象? |
| **解释器** | Interpreter | 如何为语言定义语法并解释? |
| **迭代器** | Iterator | 如何顺序访问集合而不暴露其内部结构? |
| **中介者** | Mediator | 如何减少对象间的直接耦合? |
| **备忘录** | Memento | 如何捕获并恢复对象状态? |
| **观察者** | Observer | 如何实现一对多的依赖通知? |
| **状态** | State | 如何让对象在状态变化时改变行为? |
| **策略** | Strategy | 如何让算法族可互换? |
| **模板方法** | Template Method | 如何定义算法骨架,让子类实现步骤? |
| **访问者** | Visitor | 如何在不修改类的前提下添加新操作? |

### 6.2 关于"学习所有23种模式"的理性态度

课件列出全部23种模式,但在考试和实践中通常只需掌握最常用的5-8种: Singleton, Factory, Observer, Strategy, Decorator, Adapter, Facade, Command。关键不是记住所有模式的名字,而是理解**每种模式解决的"反复出现的问题"是什么**。

---

## 本章知识图谱

```
         SOLID (五原则)
              |
              v
      设计模式 (Design Patterns)
              |
    +---------+----------+
    |         |          |
  创建型    结构型     行为型
    |         |          |
 Singleton  Adapter   Observer
 Factory    Decorator Strategy
 Builder    Facade    Command
 Prototype  Composite State
 AbstractF  Proxy     Template Method
            Bridge    Iterator
            Flyweight Mediator/Memento
                      Chain/Visitor/Interpreter
```

---

## 关键术语索引

| 法文术语 | 中文翻译 | 章节 |
|---------|---------|------|
| Patron de conception / Design Pattern | 设计模式 | 2 |
| SOLID | SOLID五原则 | 1 |
| Singleton | 单例模式 | 4 |
| Factory Method | 工厂方法模式 | 4 |
| Adapter | 适配器模式 | 5 |
| Decorator | 装饰器模式 | 5 |
| Facade | 外观模式 | 5 |
| Observer | 观察者模式 | 6 |
| Strategy | 策略模式 | 6 |
| MVC | 模型-视图-控制器 | (见第9章) |
| GoF (Gang of Four) | 四人帮(23种模式) | 3 |
| Creation | 创建型 | 3 |
| Structure | 结构型 | 3 |
| Comportement | 行为型 | 3 |
