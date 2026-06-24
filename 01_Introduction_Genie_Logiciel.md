# Chapitre 01 --- Introduction au Genie Logiciel / 软件工程导论

> **来源课件**: `chap_0_syllabus.pptx` + `chap_1_introduction.pptx` (共31张幻灯片)
> **授课教师**: Dr. Daniela Pamplona, Dr. Fatiya Bousbahi

---

## 章节目录

1. [什么是软件?——从程序到产品的认知跃迁](#1-什么是软件从程序到产品的认知跃迁)
2. [软件的类型——按应用领域与许可协议的分类体系](#2-软件的类型按应用领域与许可协议的分类体系)
3. [好软件的四大属性——可维护性、可靠性、效率、可接受性](#3-好软件的四大属性可维护性可靠性效率可接受性)
4. [软件危机——为什么软件质量如此难以保证?](#4-软件危机为什么软件质量如此难以保证)
5. [软件工程的定义——理论、方法与工具的学科体系](#5-软件工程的定义理论方法与工具的学科体系)
6. [软件工程师的角色与道德准则](#6-软件工程师的角色与道德准则)
7. [课程概览与考核方式](#7-课程概览与考核方式)

---

## 1. 什么是软件?——从程序到产品的认知跃迁

### 1.1 概念辨析: 程序 vs 软件 / Programme vs Logiciel

在计算机科学的日常话语中,"程序"和"软件"常被混用,但它们在工程学意义上有着本质区别:

| 维度 | 程序 (Programme) | 软件 (Logiciel) |
|------|-----------------|----------------|
| **定义** | 一组按序执行的指令序列 | 包含程序、配置文件、数据、自动化流程的完整集合 |
| **范围** | 单一功能模块 | 系统级产品 |
| **交付物** | 源代码/可执行文件 | 完整的可运行系统 + 文档 + 部署脚本 |
| **生命周期** | 通常无明确定义 | 有完整的开发 -> 维护 -> 退役周期 |

**原课件定义(法语原文)**:
> *Programmation informatique*: Ensemble et suite sequentielle d'operations qui vont etre executees de facon automatique sur un support informatique.
> 
> *Logiciel*: Ensemble d'instructions permettant d'executer differentes taches sur un appareil informatique. Typiquement compose de plusieurs programmes, ainsi que tous les elements necessaires qui le rendent operationnel (fichiers de configuration, donnees, procedures automatiques...).

**深层解读**: 为什么这个区分重要?因为"软件 = 程序 + 一切让程序可运行的东西",这一定义直接决定了软件工程的组织方式——不仅要管理代码,还要管理配置、数据、文档、部署流程。这也解释了为什么现代DevOps强调"基础设施即代码"(IaC): 配置文件、部署脚本本身就是软件的一部分。

### 1.2 软件的本质特征

软件与硬件相比有几个根本性差异:

1. **非物质性(Immateriel)**: 软件没有物理实体,不存在磨损问题。但"不会磨损"不等于"不会退化"——软件会因环境变化(操作系统升级、依赖库过时)而逐渐失效,这种现象称为 **软件老化(Software Aging)**。

2. **可复制性(Reproductibilite)**: 软件的边际复制成本趋近于零,这使得软件的经济模型与制造业完全不同——研发成本极高但分发成本极低。

3. **复杂性(Complexite)**: 软件是人类建造过的最复杂的工程产物之一。一个中等规模的操作系统代码行数可达数百万,其状态空间远超任何物理系统。

---

## 2. 软件的类型——按应用领域与许可协议的分类体系

### 2.1 按应用领域分类 / Par Domaine d'Application

| 类别 | 典型产品 | 核心特征 |
|------|---------|---------|
| **系统软件** | 操作系统、编译器、驱动程序 | 管理硬件资源,提供基础设施 |
| **应用软件** | 办公套件、ERP、社交网络 | 直接面向终端用户需求 |
| **嵌入式软件** | 汽车ECU、医疗设备、智能家电 | 与硬件深度耦合,可靠性要求极高 |
| **科学计算软件** | 仿真平台、数据分析工具 | 高性能计算,算法密集 |
| **Web/移动应用** | 电商平台、即时通讯 | 网络依赖,持续部署 |
| **人工智能软件** | 推荐系统、自动驾驶决策 | 数据驱动,模型即软件 |

### 2.2 按许可协议分类 / Par Contrat de Licence

| 类型 | 法文名称 | 核心特征 |
|------|---------|---------|
| **专有软件** | Proprietaire | 作者保留所有权利,源码不公开 |
| **自由软件** | Libre | 可执行、可研究源码、可修改、可再分发(四大自由) |
| **免费软件** | Gratuit (Freeware) | 免费使用,但源码不开放,属于专有软件子类 |
| **共享软件** | Partagiciel (Shareware) | 允许分发,通常有时间/功能限制 |

**深层解读**: 自由软件(Libre)与免费软件(Gratuit)的混淆是一个常见误区。Richard Stallman的名言精确概括了二者的区别: "Free as in freedom, not free as in free beer"(自由如言论,而非免费如啤酒)。在工程实践中,许可证选择会影响:
- 开发团队的代码可见性策略
- 第三方依赖的合规审查
- 商业模式的可行性(如SaaS + 开源核心)

---

## 3. 好软件的四大属性——可维护性、可靠性、效率、可接受性

> 课件原文: *Un bon logiciel doit fournir a l'utilisateur les fonctionnalites et les performances requises et doit etre facile a entretenir, fiable, efficace et acceptable.*

### 3.1 可维护性 (Maintenabilite)

**定义**: 软件可被修改(修复缺陷、适应环境变化、增加功能)的容易程度。

**为什么重要?** 软件生命周期中,维护成本通常占总成本的 **60%-80%**。一个"能运行但无法修改"的软件本质上是"技术债务的定时炸弹"。

**影响因素**:
- 代码可读性(命名规范、注释质量)
- 模块化程度(高内聚、低耦合)
- 文档完整性
- 自动化测试覆盖率

**工程启示**: 可维护性不是"写完代码后补文档"就能获得的,它必须在 **架构设计阶段** 就被纳入考量。SOLID原则、设计模式、Clean Architecture都是为了提升可维护性。

### 3.2 可靠性与安全性 (Fiabilite et Securite)

**定义**: 软件在给定条件下、给定时间内,无故障运行的能力。

**可靠性 != 安全性**:
- 可靠性关注"系统是否按预期工作"
- 安全性关注"系统是否防御恶意攻击"
- 但二者深度关联: 不安全的状态本质上也是一种不可靠的状态

**量化指标**:
- **MTBF**(Mean Time Between Failures, 平均故障间隔)
- **MTTR**(Mean Time To Repair, 平均修复时间)
- **Availability**(可用性) = MTBF / (MTBF + MTTR)

**工程实践**: 冗余设计、故障隔离、优雅降级(Graceful Degradation)、混沌工程(Chaos Engineering)都是提升可靠性的手段。

### 3.3 效率 (Efficacite)

**定义**: 软件对系统资源(CPU、内存、存储、网络带宽、电量)的利用程度。

**两个维度**:
- **时间效率**: 响应时间、吞吐量
- **空间效率**: 内存占用、存储占用

**深层思考**: 效率与其他属性之间存在 **trade-off**:
- 效率 vs 可维护性: 手写汇编极高效率但几乎不可维护
- 效率 vs 可移植性: 平台特化优化提升效率但牺牲跨平台能力
- 效率 vs 开发速度: "过早优化是万恶之源"(Donald Knuth)

### 3.4 可接受性 (Acceptabilite)

**定义**: 软件被目标用户理解、学习、使用并产生满意度的程度。

这包含了 **可用性(Usability)**、**可理解性(Comprehensibility)** 和 **兼容性(Compatibility)**。可接受性在课件中被置于与功能正确性同等的高度,体现了现代软件工程"以用户为中心"的转向。

---

## 4. 软件危机——为什么软件质量如此难以保证?

### 4.1 历史脉络

课件描述了软件工程诞生的历史动力:

| 时期 | 特征 | 问题 |
|------|------|------|
| **1950s** | 高级编程语言诞生,"欣快期" | 乐观主义,低估软件复杂性 |
| **1960s** | 应用领域爆炸式扩展(科学计算 -> 企业管理 -> 工业控制 -> 嵌入式) | 交付延迟、预算超支、需求不匹配、难以使用和维护 |
| **1968** | NATO召开第一届"软件工程"工作会议 | 正式提出"Software Engineering"一词,标志学科诞生 |

### 4.2 软件质量低下的根本原因 / Raisons de la Faible Qualite

课件总结了三个根本原因:

1. **本质复杂性(Complexite intrinseque)**: 软件要建模的现实世界本身复杂,且没有物理约束(不像建筑受重力约束),意味着状态空间可以无限膨胀。

2. **方法与严谨性的缺失(Manque de methodes et rigueur)**: 在没有系统方法论的情况下开发软件,犹如没有蓝图的建筑工程。这也是软件工程学科存在的价值——提供可复用的方法论。

3. **需求理解错误(Mauvaise comprehension des besoins)**: 客户说不清想要什么,开发者听不懂客户在说什么。**需求工程的失败是软件项目失败的第一大原因**。

### 4.3 软件成本结构的演变

课件指出硬件成本与软件成本的消长关系:
- 1950年前: 硬件主导成本
- 1950-2000: 计算机普及,软件开发成本上升
- 2000年后: 数据库系统成为核心,维护成本超过开发成本

这一趋势解释了为什么 **可维护性** 被列为好软件的第一属性——在总成本中,维护占了绝大多数。

---

## 5. 软件工程的定义——理论、方法与工具的学科体系

### 5.1 经典定义

> 课件原文: *Le genie logiciel est interesse par les theories, les methodes et les outils de developpement des logiciels professionnels.*

软件工程关注的是 **专业软件** 的开发——这意味着:
- 有质量的系统化保证
- 有纪律的开发过程
- 有可度量的产出标准
- 有可问责的伦理框架

### 5.2 三要素模型

```
           Theories / 理论
                |
                v
Methodes / 方法 -> Genie Logiciel / 软件工程 -> Logiciel Professionnel / 专业软件
                ^
                |
           Outils / 工具
```

| 要素 | 内涵 | 举例 |
|------|------|------|
| **理论 (Theories)** | 形式化基础、数学模型 | 计算复杂性理论、类型理论、形式化验证 |
| **方法 (Methodes)** | 开发过程的组织方式 | 瀑布模型、敏捷、Scrum、TDD |
| **工具 (Outils)** | 支持开发活动的自动化手段 | IDE、版本控制、CI/CD管道、测试框架 |

**深层思考**: 三要素是相互促进的。理论的进展催生新方法(如类型系统理论 -> 静态分析工具),工具的成熟使方法得以规模化(如Git -> Git Flow/GitHub Flow),方法的实践又反馈给理论(如敏捷实践 -> 精益软件开发理论)。

---

## 6. 软件工程师的角色与道德准则

### 6.1 开发团队角色图谱

课件定义了开发团队中的四类关键角色及其职责边界:

| 角色 | 法文 | 职责 | 核心关注点 |
|------|------|------|-----------|
| **客户** | Client | 出资方,提出需求 | 投资回报率 (ROI) |
| **管理者** | Manager | 制定规则和指导方针,确保组织韧性 | 风险管理 |
| **软件工程师** | Ingenieur logiciel | 编写和测试代码 | 技术质量 |
| **最终用户** | Utilisateur final | 使用产品,提供反馈 | 用户体验 |

### 6.2 软件工程师的完整活动链

课件列出软件工程师从始至终承担的全部活动——**10项核心任务**:

1. **需求捕获** (Capture des besoins) -> 需求规格说明书
2. **分析与建模** (Analyse, modelisation) -> 架构定义、模块与接口定义
3. **算法设计** (Definition des algorithmes)
4. **编码实现** (Codage dans un langage cible)
5. **集成组装** (Assemblage des differentes parties)
6. **文档编写** (Manuel d'utilisation, aide en ligne)
7. **测试验证** (Tests fonctionnels, de fiabilite, de surete)
8. **验收交付** (Recette, conformite aux exigences)
9. **部署培训** (Livraison, installation, formation)
10. **维护演进** (Corrections et evolutions)

**关键洞察**: 在这10项活动中,只有第4项(编码实现)是"写代码"。一个软件工程师的时间只有约20%-30%花在编码上,其余的都在需求分析、设计、测试、沟通、文档上。这也是为什么 **软件工程 != 编程**。

### 6.3 ACM/IEEE 软件工程道德准则

课件引用了ACM发布的《软件工程道德与专业实践准则》(8条):

| # | 准则 (Francais) | 中文 | 核心原则 |
|---|----------------|------|---------|
| 1 | **Le Public** | 公众利益 | 任何时候以公众利益为先 |
| 2 | **Le Client et l'Employeur** | 客户与雇主 | 在公众利益前提下,服务客户与雇主利益 |
| 3 | **Le Produit** | 产品 | 确保产品符合最高专业标准 |
| 4 | **Le Jugement** | 专业判断 | 保持专业判断的独立性与完整性 |
| 5 | **La Gestion** | 管理 | 推广道德化的开发与维护管理 |
| 6 | **La Profession** | 职业 | 维护职业诚信与声誉 |
| 7 | **Les Collegues** | 同事 | 公平对待并支持同事 |
| 8 | **Soi-meme** | 自我 | 终身学习,推广职业道德实践 |

**工程伦理案例**:
- **准则1的应用**: 2015年大众汽车"排放门"——软件工程师实现了排放测试作弊逻辑,违反了公众利益优先原则。
- **准则3的应用**: 波音737 MAX的MCAS系统——软件设计缺陷导致两起空难,体现了"最高专业标准"缺失的后果。

---

## 7. 课程概览与考核方式

### 7.1 课程目标 (Objectives)

课件列出了5项核心教学目标:

1. **描述**不同的软件过程模型、系统规格说明和分析设计方法
2. **分析**用户需求,使用面向对象方法论绘制UML分析图
3. **设计与开发**系统模型,使用UML进行软件建模
4. **实施与评估**系统,使用测试策略和产品质量度量
5. **团队协作**: 定义和达成团队目标,分享信息,调和意见分歧

### 7.2 考核方式 (Evaluation)

| 项目 | 占比 |
|------|------|
| 期末考试 (Examen) | 60% |
| 平时成绩 (Controle continu) | 40%(含测验 Test、项目 Projet) |

### 7.3 参考书目

| 作者 | 书名 |
|------|------|
| John Dooley | *Software Development and Professional Practice* |
| Ian Sommerville | *Software Engineering* |
| Roger S. Pressman | *Software Engineering: A Practitioner's Approach* (7th ed.) |
| Raphael Grevisse Yende | *Support de Cours de Genie Logiciel* |

---

## 本章知识图谱

```
认知基础                    质量维度
软件 != 程序 ----------------> 可维护性
软件类型                     可靠性/安全
       |                     效率
       |                     可接受性
       v                        ^
软件危机 --> 软件工程 --> 工程师角色 --> 道德准则
(1968)      (三要素)     (10项活动)    (8条准则)
```

---

## 关键术语索引

| 法文术语 | 中文翻译 | 章节 |
|---------|---------|------|
| Logiciel | 软件 | 1 |
| Programme | 程序 | 1 |
| Maintenabilite | 可维护性 | 3 |
| Fiabilite | 可靠性 | 3 |
| Efficacite | 效率 | 3 |
| Acceptabilite | 可接受性 | 3 |
| Crise du logiciel | 软件危机 | 4 |
| Genie Logiciel | 软件工程 | 5 |
| Code d'Ethique | 道德准则 | 6 |
| Licence Proprietaire | 专有许可 | 2 |
| Logiciel Libre | 自由软件 | 2 |
| IEEE/ACM | 电气电子工程师学会/计算机协会 | 6 |
| Ingenieur | 工程师 | 6 |
