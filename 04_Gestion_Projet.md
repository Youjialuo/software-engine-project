# Chapitre 04 --- Gestion de Projet / 项目管理基础

> **来源课件**: `CM_4_gestion_projet.pptx` + `CM_5_gestion_projet.pptx` (42张幻灯片)
> **授课教师**: Dr. Daniela Pamplona

---

## 章节目录

1. [为什么软件工程师需要懂项目管理?](#1-为什么软件工程师需要懂项目管理)
2. [项目管理的五大阶段](#2-项目管理的五大阶段)
3. [SMART目标与项目计划结构](#3-smart目标与项目计划结构)
4. [风险管理——软件项目的八类风险](#4-风险管理软件项目的八类风险)
5. [PERT图——关键路径的数学之美](#5-pert图关键路径的数学之美)
6. [甘特图——时间维度的可视化](#6-甘特图时间维度的可视化)
7. [其他管理工具——产品分解、任务分解、风险矩阵](#7-其他管理工具产品分解任务分解风险矩阵)

---

## 1. 为什么软件工程师需要懂项目管理?

### 1.1 课件的核心论点

> *Tous les equipes sont gerees. Il faut apprendre les taches et difficultes des gestionnaires, pour bien travailler avec eux.*
> 所有团队都被管理。你需要学习管理者的任务和困难,以便与他们良好协作。

> *Le role du chef de projet est de veiller a ce que le projet logiciel respecte et surmonte les contraintes tout en livrant un logiciel de haute qualite. Une bonne gestion ne peut pas garantir le succes du projet. Cependant, une mauvaise gestion conduit generalement a l'echec du projet.*
> 项目经理的角色是确保软件项目遵守并克服约束,同时交付高质量软件。好的管理不能保证项目成功,但糟糕的管理通常导致项目失败。

### 1.2 软件项目管理的独特挑战

课件指出了IT项目管理的特殊困难:
- **需求模糊**: 客户往往说不清要什么
- **技术不确定性**: 新技术的学习曲线和不可预见的问题
- **团队协调**: 多角色协作的复杂性
- **不可见的进度**: 软件不像建筑,进度无法通过肉眼判断

---

## 2. 项目管理的五大阶段

课件将项目管理分解为五个明确的阶段:

| # | 阶段 | 法文 | 核心活动 |
|---|------|------|---------|
| 1 | **可行性验证** | Verification de faisabilite | 检查团队和公司整体是否有能力完成项目 |
| 2 | **计划编写** | Ecriture d'un plan | 制定项目计划文档 |
| 3 | **执行** | Realisation | 团队完成交付物;项目经理分配任务并促进沟通 |
| 4 | **监控** | Surveillance | 监控时间、成本、范围、质量和风险 |
| 5 | **收尾** | Cloture | 确认所有工作已完成、批准和移交;总结经验教训 |

### 深层解读

这五阶段与Deming的PDCA循环(Plan-Do-Check-Act)高度对应:
- Plan = 阶段1+2 (可行性+计划)
- Do = 阶段3 (执行)
- Check = 阶段4 (监控)
- Act = 阶段5 (收尾,包含经验教训反馈到下一个项目)

---

## 3. SMART目标与项目计划结构

### 3.1 SMART原则

课件在项目计划的"引言"部分引入了SMART框架:

| 字母 | 英文 | 法文 | 含义 |
|------|------|------|------|
| S | Specific | Specifique | 具体的,而非模糊的 |
| M | Measurable | Mesurable | 可度量的,有明确成功标准 |
| A | Achievable | Realisable | 可实现的,在资源和时间约束内 |
| R | Relevant | Pertinent | 相关的,与业务目标对齐 |
| T | Time-bound | Temporellement limite | 有时限的,有明确截止日期 |

**示例**: "改善用户体验"不是SMART的; "在3个月内将课程预订时间减少30%"是SMART的。

### 3.2 项目计划的最小结构

课件提供了一个高质量项目计划的最低建议结构:

| 章节 | 内容要点 |
|------|---------|
| **引言** | 目标(SMART)和约束(预算、时间、人员);执行摘要 |
| **组织** | 开发团队组织结构;人员与角色识别 |
| **风险分析** | 风险描述、发生概率、缓解策略 |
| **资源** | 硬件、软件和人力资源规格;采购/租赁估算 |
| **活动/交付物/时间表** | 工作分解;依赖关系;时间估算;人员分配 |
| **评估与成功指标** | 管理报告定义;项目评估;成功KPI |

---

## 4. 风险管理——软件项目的八类风险

### 4.1 风险分类

课件列出了软件开发项目面临的八类风险:

| # | 风险类别 | 法文 | 示例 |
|---|---------|------|------|
| 1 | **商业风险** | Commerciaux | 产品市场定位错误、竞争对手 |
| 2 | **财务风险** | Financiers | 资金不足以完成产品 |
| 3 | **技术风险** | Techniques | 所选技术不成熟或未经验证 |
| 4 | **开发风险** | Developpement | 团队经验不足 |
| 5 | **进度风险** | Calendrier | 任务超时 |
| 6 | **缺陷与错误** | Bogues et erreurs | 软件缺陷累积 |
| 7 | **需求误解** | Exigences mal entendues | 做出来的不是用户想要的 |
| 8 | **需求频繁变更** | Changement frequent des exigences | 需求不稳定导致返工 |

### 4.2 风险矩阵 (Matrice des risques)

课件介绍了一个二维风险评估工具:
- **轴1**: 发生概率 (Probabilite)
- **轴2**: 影响程度 (Impact)

风险等级 = 概率 x 影响, 分为: 极低 -> 低 -> 中 -> 高 -> 极端

**关键原则**: 任务划分越细,风险评估越准确 (Le plus petite est la tache, le meilleure est l'estimation du risque)。

---

## 5. PERT图——关键路径的数学之美

### 5.1 PERT的定义

> PERT (Program Evaluation and Review Techniques) 是一种项目规划和管理工具,通过**节点和箭头**的连接来:
> - 确定项目的关键阶段
> - 必要时优化时间表
> - 项目启动后检查进展

### 5.2 核心定义 (必背)

课件给出了PERT计算的完整术语体系:

| 符号 | 全称 | 含义 |
|------|------|------|
| **DTO** | Debut d'une tache au plus Tot | 最早开始时间 (最早何时可开始) |
| **FTO** | Fin d'une tache au plus Tot | 最早完成时间 (最早何时可完成) |
| **DTA** | Debut d'une tache au plus Tard | 最晚开始时间 (最晚何时必须开始) |
| **FTA** | Fin d'une tache au plus Tard | 最晚完成时间 (最晚何时必须完成) |
| **D** | Duree | 持续时间 (D = FTA - DTA = FTO - DTO) |
| | Marge libre | 自由浮动: 不延迟后续任务的前提下可推迟的时间 |
| | Marge totale | 总浮动: 不延迟项目完成日期的前提下可推迟的时间 (FTA - FTO) |

### 5.3 关键路径 (Chemin critique)

> **定义**: 关键路径是实现项目所需的**最长任务序列**,决定了项目的最短完成时间。

**关键性质**:
- 关键路径上的任务**总浮动 = 0**
- 关键路径上的任何延迟**直接**导致项目整体延迟

### 5.4 PERT计算算法 (前推+后推)

课件给出了完整的逐步算法:

**前推 (Forward Pass)**——计算DTO和FTO:
1. 无前驱节点的DTO = 0
2. 从左到右遍历: DTO(N) = max(FTO(所有前驱节点))
3. FTO = DTO + D

**后推 (Backward Pass)**——计算FTA和DTA:
1. 无后继节点的FTA = max(FTO(所有无后继节点))
2. 从右到左遍历: FTA(N) = min(DTA(所有后继节点))
3. DTA = FTA - D

### 5.5 四种依赖关系

| 类型 | 法文 | 含义 | 示例 |
|------|------|------|------|
| **完成-开始 (FD)** | Fin a Debut | A完成后B才能开始 | 需求分析完成后才能开始设计 |
| **完成-完成 (FF)** | Fin a Fin | B完成前A必须完成 | 文档编写完成前代码审查必须完成 |
| **开始-开始 (DD)** | Debut a Debut | A开始后B才能开始 | 开发开始后测试用例编写可以并行开始 |
| **开始-完成 (DF)** | Debut a Fin | B开始后A才能完成 | 新系统上线后旧系统才能下线 |

### 5.6 PERT节点结构

课件展示的PERT节点包含:
```
+------------------+
| DTO  |  D  | FTO |
| Tache X           |
| DTA  |     | FTA |
+------------------+
```

---

## 6. 甘特图——时间维度的可视化

### 6.1 定义与用途

> 甘特图允许在时间轴上可视化项目的各项任务。它是一个**连通、加权、有向**的图,以图形方式表示项目进展。

### 6.2 甘特图 vs PERT

| 维度 | PERT | 甘特图 |
|------|------|--------|
| **优势** | 显示任务间关系;分析浮动(容差);管理与关键任务的关系 | 显示任务间关系;显示绝对日历时间 |
| **侧重** | 依赖关系的逻辑分析 | 时间维度的直观展示 |
| **配合** | 通常先生成PERT,再转换为甘特图 | |

### 6.3 甘特图构建步骤

1. 为每个任务确定DTO (可先准备PERT图)
2. 为每个任务创建正确长度的条形
3. 按DTO递增顺序排列任务
4. 调整条形位置,考虑工作日和非加班约束
5. 连接相关任务(显示依赖关系)

---

## 7. 其他管理工具

### 7.1 产品分解结构 (Organigramme de produit)

按交付物和中间产出对产品进行分层分解。目的: **控制最终产品的功能完整性**。

### 7.2 任务分解结构 (Organigramme des taches / WBS)

按管理、技术研究、实现、测试、现场研究等类别分解工作。目的: **控制活动分布**。

### 7.3 组织分解结构 (Organigramme de l'organisation)

定义组织如何执行任务: 技能、职责、关系。目的: **控制成本和资源**。

---

## 本章知识图谱

```
项目管理五阶段
      |
+-----+------+------+------+
|     |      |      |      |
可行性  计划   执行   监控   收尾
      |
      v
   SMART目标
      |
      v
  风险管理 (8类风险 -> 风险矩阵)
      |
      v
  +---+---+
  |       |
PERT图   甘特图
(逻辑)   (时间)
  |
  v
关键路径 (总浮动=0)
```

---

## 关键术语索引

| 法文术语 | 中文翻译 | 章节 |
|---------|---------|------|
| Gestion de projet | 项目管理 | 1 |
| SMART | SMART目标 | 3 |
| Risque | 风险 | 4 |
| PERT | 项目评估与审查技术 | 5 |
| Chemin critique | 关键路径 | 5 |
| DTO / FTO | 最早开始/最早完成 | 5 |
| DTA / FTA | 最晚开始/最晚完成 | 5 |
| Marge totale | 总浮动 | 5 |
| Marge libre | 自由浮动 | 5 |
| Diagramme de Gantt | 甘特图 | 6 |
| Organigramme de produit | 产品分解结构 | 7 |
| Organigramme des taches (WBS) | 工作分解结构 | 7 |
| Matrice des risques | 风险矩阵 | 4 |
| Dependance Fin-Debut (FD) | 完成-开始依赖 | 5 |
| Dependance Fin-Fin (FF) | 完成-完成依赖 | 5 |
| Dependance Debut-Debut (DD) | 开始-开始依赖 | 5 |
| Dependance Debut-Fin (DF) | 开始-完成依赖 | 5 |
