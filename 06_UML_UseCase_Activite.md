# Chapitre 06 --- UML: Diagrammes de Cas d'Utilisation et d'Activites / UML用例图与活动图

> **来源课件**: `CM_8_UML_diagramme_cas_utilisation.pptx` (39张幻灯片) + `CM_9_diagramme_activites.pptx` (20张幻灯片)
> **授课教师**: Dr. Daniela Pamplona

---

## 章节目录

### Partie A: Diagramme de Cas d'Utilisation / 用例图
1. [UML概述——为什么需要统一建模语言?](#1-uml概述为什么需要统一建模语言)
2. [用例图的五大元素](#2-用例图的五大元素)
3. [参与者关系——泛化/特化](#3-参与者关系泛化特化)
4. [用例间关系——Include, Extend, Generalisation](#4-用例间关系include-extend-generalisation)
5. [场景编写——从用例图到文本描述](#5-场景编写从用例图到文本描述)
6. [综合示例——玩具图书馆(La Ludotheque)](#6-综合示例玩具图书馆la-ludotheque)

### Partie B: Diagramme d'Activites / 活动图
7. [活动图的元素与语义](#7-活动图的元素与语义)
8. [活动图与用例图的关系](#8-活动图与用例图的关系)

---

## 1. UML概述——为什么需要统一建模语言?

### 1.1 UML的定义与目标

> *UML = Unified Modeling Language*
> *L'objectif de UML est d'assister le design et le developpement du logiciel.*

UML是一个**建模语言**,而非方法论。关键区别:
- **建模语言**: 提供符号和表达方式(语法+语义)
- **方法论**: 规定"怎么用"这些符号(过程)

### 1.2 为什么需要UML?

课件给出7个理由:

| # | 理由 | 深层解读 |
|---|------|---------|
| 1 | **建模需求** | 构造软件前需要建模,就像建楼前需要蓝图 |
| 2 | **静态+动态** | UML同时支持结构(静态)和行为(动态)建模 |
| 3 | **多层次多视图** | 在不同抽象层次上从不同视角建模 |
| 4 | **过程独立** | 不绑定特定开发过程(瀑布或敏捷都能用) |
| 5 | **标准化** | 半形式化(semi-formel)语言,提供通用沟通标准 |
| 6 | **面向对象思维** | 促进面向对象的思考方式 |
| 7 | **编程语言独立** | 即使使用非面向对象语言,也能用UML进行设计 |

### 1.3 UML 2.x的三大图类

课件指出UML图分为三大类:

| 图类 | 法文 | 包含的图 |
|------|------|---------|
| **结构图** | Structure Diagram | 类图、对象图、组件图、部署图... |
| **行为图** | Behavior Diagram | **用例图**、**活动图**、状态机图 |
| **交互图** | Interaction Diagram | 序列图、通信图、时序图... |

用例图和活动图都属于**行为图**。

---

## Partie A: Diagramme de Cas d'Utilisation / 用例图

## 2. 用例图的五大元素

### 2.1 元素清单

> *Les diagrammes de cas d'utilisation modelisent a quoi sert le systeme. Vision du systeme centree sur l'utilisateur.*
> 用例图建模的是**系统用来做什么**,是一种**以用户为中心**的系统视角。

| # | 元素 | 法文 | 表示法 | 含义 |
|---|------|------|--------|------|
| 1 | **参与者** | Acteur | 小人图标 | 与系统交互的外部实体(人、物、其他软件) |
| 2 | **用例** | Cas d'utilisation | 椭圆 | 外部可见的系统功能 |
| 3 | **关联** | Association | 实线 | 参与者与用例之间的交互关系 |
| 4 | **系统边界** | Frontiere du systeme | 矩形框 | 系统范围的界定 |
| 5 | **文本描述** | Description textuelle | 文本 | 用例的补充说明/场景 |

### 2.2 参与者 (Acteur) 深度解析

> *Entite qui interagit avec le systeme. Personne, chose, logiciel, exterieur au systeme decrit. Represente un role (plusieurs roles possibles pour une meme entite).*

**关键要点**:
- 参与者**不是具体的人**,而是**角色**(一个人可以扮演多个角色)
- 参与者存在于系统**外部**
- 参与者用角色名标识(名词)

**主参与者 vs 次参与者**:
| 类型 | 法文 | 特征 |
|------|------|------|
| **主参与者** | Acteur principal | 主动发起交互以实现用例 |
| **次参与者** | Acteur secondaire | 被系统调用;通常是外部系统 |

### 2.3 用例 (Cas d'utilisation) 深度解析

> *Motif coherent de comportement realise par le systeme. Une sequence d'actions connectees, effectuees par un dialogue entre des acteurs et le systeme, qui a de la valeur pour un ou plusieurs acteurs, qui produit un resultat observable.*

用例的定义包含四个关键要素:
1. **行为模式**: 连贯的行为模式
2. **对话序列**: 参与者与系统之间的交互序列
3. **价值**: 对一个或多个参与者有价值
4. **可观察结果**: 产生可观察的结果

用例用**动词不定式**(infinitif)标识,如"S'authentifier"(登录)、"Passer commande"(下单)。

---

## 3. 参与者关系——泛化/特化

### 3.1 唯一的关系类型

课件明确指出: 参与者之间**只有一种关系**——**泛化(Generalisation)**。

```
           Personne  (泛化元素——箭头指向)
          /             Adherent   Conseiller  (特化元素)
```

泛化关系等同于面向对象编程中的**继承**: Adherent是一种Personne,Conseiller也是一种Personne。

---

## 4. 用例间关系——Include, Extend, Generalisation

### 4.1 三种关系总览

| 关系 | 法文 | 符号 | 方向 | 语义 |
|------|------|------|------|------|
| **包含** | Inclusion / <<include>> | 虚线+箭头+<<include>> | 基础用例 -> 被包含用例 | 基础用例**必定**调用被包含用例 |
| **扩展** | Extension / <<extend>> | 虚线+箭头+<<extend>> | 扩展用例 -> 基础用例 | 扩展用例**可选地**增强基础用例 |
| **泛化** | Generalisation | 实线+空心三角 | 特化用例 -> 泛化用例 | 特化是泛化的一种具体形式 |

### 4.2 Include vs Extend——最易混淆的辨析

| 维度 | <<include>> | <<extend>> |
|------|-------------|------------|
| **强制性** | **必须**(obligatoire) | **可选**(optionnel) |
| **箭头方向** | 基础 -> 被包含 | 扩展 -> 基础 |
| **语义** | "我每次执行都必须先执行你" | "我在特定条件下可以增强你" |
| **类比** | 函数调用(必调用) | 插件钩子(可选激活) |
| **复用** | 提取公共行为 | 添加可选行为 |

**判断口诀**:
- Include: "要完成A,**必须**先完成B" -> B <<include>> by A
- Extend: "A在特定条件下**可以**附加B" -> B <<extend>> A

### 4.3 Include/Extend的两大工程价值

课件明确指出:

1. **可复用性**: 如"<<include>> S'authentifier"使得认证模块无需重复开发
2. **分解**: 当一个用例过于复杂(涉及过多动作)时,分解为更简单的子用例

---

## 5. 场景编写——从用例图到文本描述

### 5.1 场景的定义

> *Sequence particuliere de messages dans le cas d'utilisation pendant une interaction particuliere.*
> *Chemin dans le cas d'utilisation.*

场景是用例内部的一条**具体执行路径**。一个用例可以有多个场景。

### 5.2 用例描述的组成

| 组件 | 含义 |
|------|------|
| **主流事件** (Flot nominal) | 一切正常时的执行路径 |
| **备选事件** (Flot alternatif) | 正常但不常见的分支路径 |
| **异常流** (Flot d'exception) | 错误/异常终止路径 |

**工程价值**: 场景描述将作为**测试用例**(jeux d'essais)的基础。

---

## 6. 综合示例——玩具图书馆 (La Ludotheque)

### 6.1 业务描述

> 我们想将一家玩具图书馆信息化,以促进其提供的玩具的查询。会员只能在会费已更新的情况下借玩具。会员可以向管理员借玩具,管理员记录借出。借出的玩具归还给管理员。会员可以预约玩具。预约需指明借阅者、玩具和预约请求日期。当玩具回架时通知会员。要组织活动,专业管理员须提供以下信息: 要测试的玩具、预期参与者的最大和最小人数、日期和活动开始时间。会员可以报名参加活动,前提是还有名额。会员可以通过外部支付系统在线支付会费。网络用户可以查询玩具并注册。

### 6.2 分析过程 (课件引导的7步法)

1. **谁**是参与者? -> Internaute(网民), Adherent(会员), Conseiller(管理员)
2. 有哪些用例?
   - Internaute: S'inscrire(注册), Consulter jeux(查询玩具)
   - Adherent: Emprunter jeux(借玩具), S'inscrire evenement(报名活动), Payer cotisation(支付会费)
   - Conseiller: Gerer les emprunts(管理借阅), Organiser evenement(组织活动)
3. 参与者间有泛化吗? -> Adherent 是 Internaute 的特化
4. 用例间有泛化吗?
5. 有 <<include>> 吗? -> 支付中包含认证
6. 有 <<extend>> 吗?
7. 哪些关联和哪些参与者相关?

---

## Partie B: Diagramme d'Activites / 活动图

## 7. 活动图的元素与语义

### 7.1 核心元素

活动图建模的是**流程**(业务流程、算法流程)。课件展示的核心元素包括:

| 元素 | 表示 | 含义 |
|------|------|------|
| **起始节点** (Noeud initial) | 实心圆 | 流程起点 |
| **活动** (Action/Activite) | 圆角矩形 | 一个具体的操作或步骤 |
| **判定节点** (Decision) | 菱形 | 分支条件判断 |
| **合并节点** (Merge) | 菱形 | 多个分支汇合 |
| **分岔** (Fork) | 粗横线 | 并行流程的分叉(同时开始多个活动) |
| **汇合** (Join) | 粗横线 | 并行流程的汇合(等待所有活动完成后继续) |
| **终止节点** (Noeud final) | 实心圆+外环 | 流程终点 |
| **泳道** (Swimlane/Partition) | 矩形分区 | 划分职责(谁做什么) |
| **控制流** (Control Flow) | 实线箭头 | 活动之间的顺序关系 |

### 7.2 决策 vs 合并

| 特性 | 决策 (Decision) | 合并 (Merge) |
|------|----------------|-------------|
| **方向** | 1个入,多个出 | 多个入,1个出 |
| **语义** | "根据条件选择一个分支" | "任何一条路径到达即可继续" |

### 7.3 分岔 vs 汇合

| 特性 | 分岔 (Fork) | 汇合 (Join) |
|------|------------|------------|
| **方向** | 1个入,多个出 | 多个入,1个出 |
| **语义** | "**同时**启动所有并行活动" | "等待**所有**并行活动完成后才继续" |

---

## 8. 活动图与用例图的关系

用例图和活动图在建模中互补:

| 维度 | 用例图 | 活动图 |
|------|--------|--------|
| **建模什么** | 系统对外提供哪些功能 | 某个功能内部如何执行 |
| **粒度** | 系统级(黑盒) | 流程级(白盒) |
| **关注者** | 客户、用户、产品经理 | 开发者、架构师 |
| **与需求的关系** | 需求的功能分解 | 具体需求的流程实现 |

**典型使用模式**: 先画用例图确定系统边界和功能,再为复杂的用例绘制活动图详细描述其内部流程。

---

## 本章知识图谱

```
            UML (统一建模语言)
                  |
    +-------------+--------------+
    |             |              |
 结构图        行为图          交互图
              /     \
    用例图 (Cas d'Util)    活动图 (Activites)
       |                       |
  +----+----+              +---+---+
  |    |    |              |       |
Acteur  UC  Relations    Decision  Fork/Join
  |    |    |              |       |
  |    |  include        分支     并行
  |    |  extend
  |    |  generalisation
  |
generalisation
(参与者间唯一关系)
```

---

## 关键术语索引

| 法文术语 | 中文翻译 | 章节 |
|---------|---------|------|
| UML | 统一建模语言 | 1 |
| Acteur | 参与者 | 2 |
| Cas d'utilisation | 用例 | 2 |
| Association | 关联 | 2 |
| Frontiere du systeme | 系统边界 | 2 |
| Generalisation | 泛化 | 3,4 |
| <<include>> | 包含关系 | 4 |
| <<extend>> | 扩展关系 | 4 |
| Scenario | 场景 | 5 |
| Flot nominal | 主流事件 | 5 |
| Flot alternatif | 备选事件 | 5 |
| Flot d'exception | 异常流 | 5 |
| Diagramme d'activites | 活动图 | 7 |
| Noeud initial / final | 起始/终止节点 | 7 |
| Decision / Merge | 判定/合并 | 7 |
| Fork / Join | 分岔/汇合 | 7 |
| Swimlane | 泳道 | 7 |
| Acteur principal / secondaire | 主/次参与者 | 2 |
| Ludotheque | 玩具图书馆(案例) | 6 |
