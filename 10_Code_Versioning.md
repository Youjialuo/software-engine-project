# Chapitre 10 --- Production du Code & Gestion des Versions / 代码生产与版本控制

> **来源课件**: `CM_10_Production du code.pdf` (23页) + `Versioning.pdf` (46页)
> **授课教师**: Dr. Fatiha Bousbahi, Dr. Daniela Pamplona

---

## 章节目录

### Partie A: Production du Code / 代码生产
1. [编码规范——统一代码库的语言](#1-编码规范统一代码库的语言)
2. [命名约定——CamelCase, snake_case与SCREAMING_SNAKE](#2-命名约定camelcase-snake_case与screaming_snake)
3. [代码格式化——缩进、行长、空格的艺术](#3-代码格式化缩进行长空格的艺术)
4. [代码审查——质量的集体守护](#4-代码审查质量的集体守护)

### Partie B: Gestion des Versions (Git) / 版本控制
5. [为什么需要版本控制?](#5-为什么需要版本控制)
6. [版本控制的核心概念——仓库、分支、合并](#6-版本控制的核心概念仓库分支合并)
7. [Git基础命令与实践](#7-git基础命令与实践)

---

## Partie A: Production du Code / 代码生产

## 1. 编码规范——统一代码库的语言

### 1.1 为什么需要统一规则?

> *Le code source est le coeur d'un projet logiciel. L'objectif de ces regles est l'uniformisation de la base de code source du projet.*
> 源码是软件项目的核心。规则的目标是统一项目的源代码库。

课件的核心论点: 编码规范不是品味问题,而是**工程需求**。

### 1.2 统一规范的四大收益

| 收益 | 详解 |
|------|------|
| **便于阅读** | 代码被查阅、审查的效率大幅提升 |
| **消除重复与错误** | 不同的实践风格导致的重复和错误被消除 |
| **团队互操作性** | 每个成员能理解和修改他人编写的代码 |
| **新人快速融入** | 新成员无需适应多种风格的差异 |

### 1.3 基础概念回顾

| 概念 | 法文 | 定义 |
|------|------|------|
| **算法** | Algorithme | 描述解决问题的步骤 |
| **源代码** | Code source | 算法在编程语言中的实现(文本文件) |
| **可执行文件** | Executable | 源代码经编译器/解释器转换后的二进制代码 |
| **软件** | Logiciel | 一个或多个程序 + 数据 + 文档 |

---

## 2. 命名约定——CamelCase, snake_case与SCREAMING_SNAKE

### 2.1 三种主流命名风格

| 风格 | 特征 | 典型用法 | 示例 |
|------|------|---------|------|
| **camelCase** | 首字母小写,后续词首大写 | Java/JS变量和函数 | `maFonction`, `monAttribut` |
| **PascalCase** | 所有词首大写 | 类名 | `MaClasse`, `EtudiantUniv` |
| **snake_case** | 全小写+下划线 | Python变量和函数 | `nombre_de_cours`, `calculer_moyenne` |
| **SCREAMING_SNAKE_CASE** | 全大写+下划线 | 常量 | `NOMBRE_MAX_ETUDIANTS` |

### 2.2 语言选择

> *La langue utilisee doit etre unique sur tout le projet.*
> 项目中使用的语言必须统一。

| 选项 | 优势 | 劣势 |
|------|------|------|
| **法语** (idClientSuivant) | 本地团队易理解 | 国际化困难 |
| **英语** (nextClientId) | 行业标准,开源友好 | 非法语母语团队可能不自然 |

**建议**: 大型项目或准备发布到开源社区的项目优先选英语。

---

## 3. 代码格式化——缩进、行长、空格的艺术

### 3.1 六大基本原则

| # | 原则 | 推荐标准 |
|---|------|---------|
| 1 | **缩进** | 4个空格/层级(不用Tab) |
| 2 | **行长** | 80-120字符 |
| 3 | **空格** | 操作符两侧加空格;逗号后加空格 |
| 4 | **花括号** | 统一的放置风格 |
| 5 | **垂直空格** | 逻辑段落间空行 |
| 6 | **自动化** | 使用格式化工具(如Prettier, Black, clang-format) |

### 3.2 深层思考

格式化的核心目的:**消除关于格式的无谓讨论**。当一个团队为"花括号放在哪里"争论时,他们在浪费本应用于设计和实现的精力。自动化格式化工具(Prettier, Black)的出现就是为了彻底终结这些争论——机器决定格式,人专注于逻辑。

---

## 4. 代码审查——质量的集体守护

代码审查(Code Review)是代码生产过程中的质量关卡: 每一段代码在合并到主分支前,都由至少一位同事审查。目标是发现:
- 逻辑错误
- 违反编码规范
- 潜在的性能问题
- 安全漏洞
- 可读性问题

---

## Partie B: Gestion des Versions (Git) / 版本控制

## 5. 为什么需要版本控制?

### 5.1 核心问题

> *Un projet logiciel a une duree de vie de plusieurs annees et subit de nombreuses evolutions.*
> 软件项目生命周期长达数年,经历无数次演变。

课件提出了版本控制要解决的经典场景:
- 如何获取团队成员的代码?
- 如何发布自己的修改?
- 多人同时编辑同一文件怎么办?(冲突)
- 如何回到之前的版本?

### 5.2 VCS的三大核心目标

| 目标 | 详解 |
|------|------|
| **保证代码的持久性** (Perennite) | 即使硬件故障,代码历史仍在仓库中 |
| **支持协作** (Travail collaboratif) | 多人并行开发而不互相覆盖 |
| **历史管理** (Gestion de l'historique) | 追溯"谁在什么时候为什么改了什么" |

---

## 6. 版本控制的核心概念——仓库、分支、合并

### 6.1 仓库 (Repository / Depot de code)

托管项目源代码的中央存储。每个开发者:
1. **拉取** (Pull/Clone) 代码到本地
2. 在本地修改
3. **推送** (Push) 修改回仓库

### 6.2 分支 (Branch) 与合并 (Merge)

> *Un logiciel de gestion des versions permet de travailler en parallele sur plusieurs problematiques en creant des branches.*

分支让团队可以**并行工作**: 一个人修bug(在bugfix分支上),另一个人开发新功能(在feature分支上),互不干扰。完成后通过**合并(Merge)**将分支的修改整合回主线。

### 6.3 核心工作流

```
Clone -> Branch -> Edit -> Commit -> Push -> Pull Request -> Review -> Merge
  |                                                                    |
  +------- 主线 (main/master) 始终保持可部署状态 ------------+
```

---

## 7. Git基础命令与实践

### 7.1 常用Git命令速查

| 命令 | 功能 | 场景 |
|------|------|------|
| `git clone <url>` | 克隆远程仓库到本地 | 首次获取项目 |
| `git pull` | 拉取远程更新 | 开始工作前同步 |
| `git branch <name>` | 创建新分支 | 开始新功能/修复 |
| `git checkout <branch>` | 切换分支 | 在不同任务间切换 |
| `git add <file>` | 暂存修改 | 准备提交 |
| `git commit -m "msg"` | 创建本地提交 | 保存一次修改快照 |
| `git push` | 推送本地提交到远程 | 分享给团队 |
| `git merge <branch>` | 合并分支 | 功能完成后集成 |
| `git log` | 查看提交历史 | 追溯变更 |
| `git status` | 查看当前状态 | 检查修改情况 |

### 7.2 冲突处理

当两个开发者修改了同一个文件的同一部分时,Git无法自动决定保留哪个版本——这就是**冲突(Conflict)**。需要手动选择保留哪些修改,然后标记冲突已解决。

---

## 本章知识图谱

```
     代码生产 (Production du Code)
              |
    +---------+---------+
    |         |         |
 命名规范   格式化    代码审查
    |         |
 camelCase  缩进4空格
 PascalCase 行长80-120
 snake_case 自动化工具

     版本控制 (Versioning)
              |
    +---------+---------+
    |         |         |
  仓库      分支      合并
 (Repo)   (Branch)  (Merge)
    |
   Git命令: clone, pull, add, commit, push, merge, log
```

---

## 关键术语索引

| 法文术语 | 中文翻译 | 章节 |
|---------|---------|------|
| Code source | 源代码 | 1 |
| Algorithme | 算法 | 1 |
| camelCase | 驼峰命名(小写起) | 2 |
| PascalCase | 帕斯卡命名(大写起) | 2 |
| snake_case | 蛇形命名(下划线) | 2 |
| Indentation | 缩进 | 3 |
| Gestion des versions (VCS) | 版本控制 | 5 |
| Depot de code (Repository) | 代码仓库 | 6 |
| Branche (Branch) | 分支 | 6 |
| Merge | 合并 | 6 |
| Commit | 提交 | 7 |
| Push / Pull | 推送/拉取 | 7 |
| Conflit | 冲突 | 7 |
| Revue de code (Code Review) | 代码审查 | 4 |
| Git | Git版本控制系统 | 7 |
