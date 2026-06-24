# Chapitre 07 --- UML: Diagramme de Classe / UML类图

> **来源课件**: `CM_8_UML-Diagramme de Classe.pdf` (23页)
> **授课教师**: Dr. Fatiha Bousbahi
> **参考教材**: Sommerville Section 5.2

---

## 章节目录

1. [结构建模——静态视角下的系统组织](#1-结构建模静态视角下的系统组织)
2. [类图的核心——类、属性、方法](#2-类图的核心类属性方法)
3. [可见性——封装的三级访问控制](#3-可见性封装的三级访问控制)
4. [多重性——关系的量化约束](#4-多重性关系的量化约束)
5. [类间五大关系——关联、泛化、依赖、聚合、组合](#5-类间五大关系关联泛化依赖聚合组合)

---

## 1. 结构建模——静态视角下的系统组织

### 1.1 模型分类回顾

课件首先回顾了系统模型的分层:

| 模型类型 | 法文 | 建模内容 |
|---------|------|---------|
| **上下文模型** | Modeles de Contexte | 系统与环境的边界 |
| **交互模型** | Modeles d'Interaction | 系统与环境或组件之间的交互 |
| **结构模型** | Modeles Structurels | 系统的组成组件及其关系 |
| **行为模型** | Modeles Comportementaux | 系统的动态行为和事件响应 |

### 1.2 结构模型的两种形态

| 形态 | 含义 | 对应UML图 |
|------|------|----------|
| **静态结构模型** | 展示系统设计时的结构 | **类图** (Class Diagram) |
| **动态结构模型** | 展示系统执行时的组织 | 对象图 (Object Diagram) |

### 1.3 类图的定位

> *Le diagramme de classe fait partie des diagrammes de structure qui decrivent les relations statiques entre les composants.*
> 类图属于结构图,描述组件之间的静态关系。

在UML 2.x层次中,类图位于**结构图(Structure Diagram)**类别。

---

## 2. 类图的核心——类、属性、方法

### 2.1 类图的基本结构

课件使用医院咨询系统的例子展示了标准类图结构:

```
+---------------------------+
| Consultation              |  <- 类名
+---------------------------+
| - date: Date              |  <- 属性 (Attributes)
| - motif: String           |
| - duree: int              |
+---------------------------+
| + programmer(): void      |  <- 方法 (Methods/Operations)
| + annuler(): void         |
| + modifierDate(): void    |
+---------------------------+
```

### 2.2 每个部分的作用

| 部分 | 法文 | 含义 | 示例 |
|------|------|------|------|
| **类名** | Nom de la Classe | 实体或概念的抽象标识 | Consultation, Patient, Medecin |
| **属性** | Attributs | 类的数据/状态 | date, motif, duree |
| **方法** | Methodes | 类的行为/操作 | programmer(), annuler() |

### 2.3 类与对象的关系

> *Une classe peut etre consideree comme une definition generale d'un objet systeme.*
> 类被视为系统对象的**通用定义**。

- **类 (Class)**: 蓝图/模板
- **对象 (Object)**: 蓝图的具体实例

---

## 3. 可见性——封装的三级访问控制

### 3.1 三种可见性修饰符

课件定义了三层访问权限:

| 符号 | 名称 | 法文 | 同类访问 | 子类访问 | 外部访问 |
|------|------|------|---------|---------|---------|
| **+** | 公共 | Public | Yes | Yes | Yes |
| **-** | 私有 | Prive | Yes | No | No |
| **#** | 受保护 | Protege | Yes | Yes | No |

### 3.2 深层原理

可见性是面向对象**封装(Encapsulation)**原则的直接体现:
- **public (+)**: "任何人都可以调用我" —— 构成类的公共API
- **private (-)**: "只有我自己能访问" —— 隐藏实现细节
- **protected (#)**: "我和我的子类能访问" —— 为继承体系保留

**注意**: 课件明确指出可见性标记不是强制性的(pas obligatoire),但在考试和规范设计中是必需的。

---

## 4. 多重性——关系的量化约束

### 4.1 多重性的定义

> *Combien d'objets de chaque classe participent a la relation.*
> 每个类的多少个对象参与了该关系。

### 4.2 标准多重性符号

| 符号 | 含义 | 示例场景 |
|------|------|---------|
| **1** | 恰好一个 | 一个人有恰好一个护照号 |
| **0..1** | 零个或一个 | 一个人最多有一个配偶 |
| **0..* 或 *** | 0个或多个 | 一个课程有0个或多个选课学生 |
| **1..*** | 1个或多个 | 一个订单至少有1个商品 |
| **2..3 或 2** | 精确数字 | 一个停车位恰好容纳1辆车 |

### 4.3 放置规则

```
ClassA  1 ----------- 0..*  ClassB
```
- ClassA这边的数字表示: 一个ClassB对象对应多少个ClassA对象
- ClassB这边的数字表示: 一个ClassA对象对应多少个ClassB对象

---

## 5. 类间五大关系——关联、泛化、依赖、聚合、组合

课件将类间关系分为5种,按耦合度从低到高排列:

### 5.1 五大关系对比

| 关系 | 法文 | 符号 | 语义 | 耦合度 |
|------|------|------|------|--------|
| **依赖** | Dependance | 虚线+箭头 -----> | A使用了B(临时关系) | 最低 |
| **关联** | Association | 实线 ----- | A知道B(持久关系) | 低 |
| **聚合** | Aggregation | 空心菱形+实线 <>----- | A拥有B(弱整体-部分) | 中 |
| **组合** | Composition | 实心菱形+实线 <*>----- | A拥有B(强整体-部分) | 高 |
| **泛化** | Generalisation | 空心三角+实线 -----|> | A是B的一种(继承) | 最高 |

### 5.2 关系详解

**关联 (Association)**:
- 两个类之间有连接
- 最简单的语义: "A知道B的存在"
- 可以带方向箭头,也可以不带(双向)

**泛化 (Generalisation)**:
- "是一种"(is-a)关系
- 子类继承父类的属性和方法
- 如: CompteEpargne 和 CompteCourant 都是 Compte 的特化

**依赖 (Dependance)**:
- 最短命的关系
- "A的变化可能影响B"
- 如: A类的方法参数类型是B

**聚合 (Aggregation)**:
- "有一个"(has-a)关系,但**弱**拥有
- 被聚合的对象可以**独立存在**
- 如: 班级 聚合 学生(学生离开班级仍然存在)

**组合 (Composition)**:
- "有一个"(has-a)关系,但**强**拥有
- 被组合的对象的生命周期**依赖**于整体
- 如: 房子 组合 房间(房子拆了,房间也不存在了)

### 5.3 聚合 vs 组合——关键区分

| 维度 | 聚合 (Aggregation) | 组合 (Composition) |
|------|-------------------|-------------------|
| **拥有强度** | 弱持有 | 强持有 |
| **生命周期** | 部分可以独立于整体存在 | 部分随整体创建和销毁 |
| **共享性** | 部分可以被多个整体共享 | 部分只能属于一个整体 |
| **课件关键描述** | "lorsque des classes qui sont des collections sont composees d'autres classes" | "lorsqu'un cycle de vie fort est present" |

---

## 本章知识图谱

```
              类图 (Class Diagram)
                    |
        +-----------+-----------+
        |           |           |
    类结构        可见性       类间关系
    (属性+方法)   (+/-/#)       |
                    |    +------+------+------+------+
                    |    |      |      |      |      |
                    |  关联  泛化  依赖  聚合  组合
                    |   |     |      |     |      |
                    |  -----  -----|> ----- <>----- <*>-----
                    |
              多重性 (1, 0..1, 0..*, 1..*)
```

---

## 关键术语索引

| 法文术语 | 中文翻译 | 章节 |
|---------|---------|------|
| Diagramme de classe | 类图 | 1,2 |
| Classe | 类 | 2 |
| Attribut | 属性 | 2 |
| Methode | 方法 | 2 |
| Visibilite | 可见性 | 3 |
| Public (+) | 公共 | 3 |
| Prive (-) | 私有 | 3 |
| Protege (#) | 受保护 | 3 |
| Multiplicite | 多重性 | 4 |
| Association | 关联 | 5 |
| Generalisation | 泛化 | 5 |
| Dependance | 依赖 | 5 |
| Aggregation | 聚合 | 5 |
| Composition | 组合 | 5 |
| Encapsulation | 封装 | 3 |
| Modele structurel | 结构模型 | 1 |
