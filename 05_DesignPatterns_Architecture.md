# 软件工程复习文档 5：设计模式与架构模式
# GÉNIE LOGICIEL — Document de Révision 5 : Design Patterns & Architecture

> CY Cergy Paris Université — Dr. Fatiha Bousbahi
> **中法双语完整复习 · Révision Bilingue Complète**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

### 5.1 Les Principes SOLID / SOLID五原则

> **FR** : SOLID est un acronyme pour 5 principes de conception en programmation orientée objet. Ces principes, popularisés par Robert C. Martin (Uncle Bob), visent à rendre le code plus compréhensible, modulaire, flexible et maintenable. Ils sont la base des design patterns.

> **ZH** : SOLID是面向对象编程中5个设计原则的首字母缩写。由Robert C. Martin（Uncle Bob）推广，旨在使代码更易理解、更模块化、更灵活、更易维护。它们是设计模式的基础。

| L | Principe (FR) | 原则 (ZH) | Explication (FR) | 解释 (ZH) |
|---|---------------|------------|-------------------|------------|
| **S** | **Responsabilité Unique** (Single Responsibility) | 单一职责 | Une classe ne doit avoir qu'UNE SEULE raison de changer. Chaque classe a UNE responsabilité bien définie. | 一个类只应有**一个**变更理由。每个类有明确定义的**一个**职责。 |
| **O** | **Ouvert/Fermé** (Open/Closed) | 开闭原则 | Une classe doit être OUVERTE à l'extension mais FERMÉE à la modification. On ajoute des fonctionnalités sans toucher au code existant. | 对扩展**开放**，对修改**封闭**。添加功能时不修改已有代码。 |
| **L** | **Substitution de Liskov** | 里氏替换 | Une classe dérivée doit pouvoir REMPLACER sa classe de base SANS altérer le comportement du programme. | 子类必须能够**替换**其基类而**不改变**程序行为。 |
| **I** | **Ségrégation des Interfaces** | 接口隔离 | Mieux vaut plusieurs interfaces SPÉCIFIQUES qu'une seule interface GÉNÉRALE. Un client ne doit pas dépendre de méthodes qu'il n'utilise pas. | 多个**专用**接口优于一个**通用**接口。客户端不应依赖其不使用的方法。 |
| **D** | **Inversion de Dépendance** | 依赖倒置 | Les modules de haut niveau ne doivent PAS dépendre des modules de bas niveau. Les DEUX doivent dépendre d'ABSTRACTIONS. | 高层模块不应依赖低层模块。**两者**都应依赖**抽象**。 |

---

### 5.2 Les Design Patterns (Patrons de Conception) / 设计模式

> **FR** : Les design patterns sont des solutions ÉPROUVÉES à des problèmes RÉCURRENTS en conception logicielle. Ils ont été popularisés par le livre « Design Patterns: Elements of Reusable Object-Oriented Software » (le « GoF » — Gang of Four) en 1994. Les 23 patterns originaux sont classés en 3 catégories.

> **ZH** : 设计模式是针对软件设计中**反复出现**的问题的**经过验证**的解决方案。由1994年的《设计模式：可复用面向对象软件的基础》（GoF——四人帮）推广。最初的23种模式分为3类。

| Catégorie (FR) / 类别 (ZH) | Rôle (FR) | 作用 (ZH) | Patterns Clés |
|---|---|---|---|
| **Création** / 创建型 | Gérer la CRÉATION d'objets de façon flexible | 灵活管理对象的**创建** | Singleton, Factory, Builder, Prototype |
| **Structure** / 结构型 | Organiser les RELATIONS entre classes et objets | 组织类和对象之间的**关系** | Adapter, Decorator, Facade, Composite, Proxy |
| **Comportement** / 行为型 | Gérer les INTERACTIONS et la répartition des responsabilités | 管理对象间的**交互**和职责分配 | Observer, Strategy, Command, State |

---

#### Patterns Clés en Détail / 重点模式详解

##### ① Singleton / 单例模式

> **FR** : Garantit qu'une classe n'a qu'UNE SEULE instance et fournit un point d'accès GLOBAL à cette instance. Utilisé pour les ressources partagées : connexion à la base de données, logger, configuration.

> **ZH** : 确保一个类只有**一个**实例，并提供该实例的**全局**访问点。用于共享资源：数据库连接、日志记录器、配置。

| Aspect | Détail |
|--------|--------|
| **Catégorie** | Création |
| **Principe** | Constructeur PRIVÉ + méthode statique `getInstance()` |
| **Quand ?** | Une seule instance est nécessaire (BD, logger, config) |

**⚠️ Singleton vs Classe Statique / 单例 vs 静态类** :

| Critère | Singleton | Classe Statique |
|---------|-----------|-----------------|
| **Instance** | Un OBJET (instance) | Pas d'instance (la classe elle-même) |
| **Interface** | **PEUT** implémenter une interface | **NE PEUT PAS** implémenter |
| **Polymorphisme** | **OUI** | **NON** |
| **Héritage** | **OUI** (peut hériter) | **NON** |
| **Testabilité** | Plus facile à mocker | Difficile à mocker |

> **🔑 Différence Clé** : Singleton peut implémenter une INTERFACE — c'est la différence la plus importante !

---

##### ② Factory / 工厂模式

> **FR** : Délègue la création d'objets à une classe spécialisée (la Factory). Le code client ne connaît PAS les classes concrètes — il ne connaît que l'interface. Cela permet de changer les classes concrètes sans modifier le code client.

> **ZH** : 将对象的创建委托给专门的类（工厂）。客户端代码不**知道**具体类——只知道接口。这允许在不修改客户端代码的情况下更换具体类。

| Aspect | Détail |
|--------|--------|
| **Catégorie** | Création |
| **Principe** | Une méthode factory crée et retourne des objets |
| **Avantage** | DÉCOUPLAGE : le client ne dépend pas des classes concrètes |

---

##### ③ Observer / 观察者模式

> **FR** : Définit une dépendance UN-À-PLUSIEURS entre objets. Quand un objet (le SUJET) change d'état, tous ses dépendants (les OBSERVATEURS) sont notifiés AUTOMATIQUEMENT. C'est le pattern derrière les événements, les notifications push, les flux RSS.

> **ZH** : 定义对象间的**一对多**依赖关系。当一个对象（**主题**）状态改变时，所有依赖它的对象（**观察者**）**自动**收到通知。这是事件、推送通知、RSS流背后的模式。

---

##### ④ Adapter / 适配器模式

> **FR** : Convertit l'interface d'une classe en UNE AUTRE interface que le client attend. Permet à des classes incompatibles de travailler ensemble. Comme un adaptateur de prise électrique qui permet de brancher une prise française dans une prise anglaise.

> **ZH** : 将类的接口转换为客户端期望的**另一种**接口。使不兼容的类能够一起工作。就像电源适配器让你把法式插头插入英式插座。

---

##### ⑤ Decorator / 装饰器模式

> **FR** : Attache DYNAMIQUEMENT des responsabilités supplémentaires à un objet. Alternative flexible à l'héritage pour ÉTENDRE les fonctionnalités. On « enveloppe » un objet dans un autre qui ajoute des comportements.

> **ZH** : **动态地**给对象附加额外职责。是继承之外的灵活替代方案，用于**扩展**功能。将一个对象「包裹」在另一个添加行为的对象中。

---

### 5.3 Patrons d'Architecture Logicielle / 软件架构模式

> **FR** : Un patron d'architecture définit l'organisation GLOBALE d'un système logiciel. Contrairement aux design patterns (niveau classe), les patrons d'architecture opèrent au NIVEAU DU SYSTÈME ENTIER.

> **ZH** : 架构模式定义软件系统的**全局**组织。不同于设计模式（类级别），架构模式在**整个系统级别**运作。

---

#### ① MVC (Modèle-Vue-Contrôleur)

> **FR** : Sépare l'application en TROIS composants interconnectés. C'est le patron d'architecture le plus utilisé pour les applications web (Django, Ruby on Rails, Spring MVC, ASP.NET MVC).

> **ZH** : 将应用程序分为**三个**互联组件。是Web应用程序最常用的架构模式（Django、Ruby on Rails、Spring MVC、ASP.NET MVC）。

```
┌──────────┐  (met à jour)  ┌───────────┐  (manipule)  ┌──────────┐
│  MODÈLE   │ ←─────────── │CONTRÔLEUR │ ───────────→ │   VUE    │
│ (Données) │               │ (Logique) │              │(Affichage)│
└──────────┘               └───────────┘              └──────────┘
      ↑                                                     │
      └─────────────────────────────────────────────────────┘
                         (notifie les changements)
```

| Composant (FR) | 组件 (ZH) | Rôle |
|---|---|---|
| **Modèle** | 模型 | Gère les données et la logique métier. Indépendant de l'interface. |
| **Vue** | 视图 | Affiche les données. Reçoit les actions utilisateur. |
| **Contrôleur** | 控制器 | Interprète les actions utilisateur, met à jour le Modèle et la Vue. |

---

#### ② Architecture en Couches / 分层架构

```
┌─────────────────────────┐
│  Présentation / 表示层   │  ← Interface utilisateur (GUI, Web)
├─────────────────────────┤
│  Logique Métier / 业务层 │  ← Règles de gestion, traitements
├─────────────────────────┤
│  Accès Données / 数据层  │  ← Persistance (ORM, SQL)
├─────────────────────────┤
│  Base de Données / 数据库 │  ← Stockage (MySQL, PostgreSQL)
└─────────────────────────┘
```

| Avantage | Inconvénient |
|----------|--------------|
| Chaque couche est indépendante et testable séparément | Performance : traverser toutes les couches a un coût |
| Maintenance facilitée | Rigidité si trop de couches |

---

#### ③ Client-Serveur / 客户端-服务器

> **FR** : Un serveur CENTRAL fournit des services à de MULTIPLES clients. Le serveur détient les données et la logique métier. Les clients sont « légers » (navigateur, app mobile).

> **ZH** : 一个**中央**服务器向**多个**客户端提供服务。服务器持有数据和业务逻辑。客户端是「轻量级」的（浏览器、移动应用）。

---

#### ④ Référentiel (Centrée Données) / 数据中心架构

> **FR** : Tous les composants partagent un DÉPÔT CENTRAL de données. Avantage : cohérence parfaite des données. Risque : le dépôt central est un point unique de défaillance.

> **ZH** : 所有组件共享一个**中央数据仓库**。优点：数据完全一致。风险：中央仓库是单点故障。

---

#### ⑤ Pipe & Filter (Tube & Filtre) / 管道-过滤器

> **FR** : Les données traversent une SÉRIE de filtres (étapes de traitement) connectés par des tubes. Chaque filtre fait UNE transformation. Exemple classique : les pipelines Unix (`cat fichier | grep mot | sort | uniq`).

> **ZH** : 数据通过一系列由管道连接的过滤器（处理步骤）。每个过滤器做**一种**转换。经典示例：Unix管道（`cat file | grep word | sort | uniq`）。

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Identifier le Design Pattern

| Énoncé (FR) / 题干 (ZH) | Pattern |
|---|---|
| « Une classe ne doit avoir qu'une seule instance » | **Singleton** |
| « Créer des objets sans exposer la logique de création » | **Factory** |
| « Notifier automatiquement quand un objet change d'état » | **Observer** |
| « Adapter l'interface d'une classe à une autre » | **Adapter** |
| « Ajouter dynamiquement des fonctionnalités sans modifier la classe » | **Decorator** |

---

### Choisir le Patron d'Architecture

| Contexte (FR) / 场景 (ZH) | Architecture |
|---|---|
| Application web interactive | **MVC** |
| Grande application d'entreprise | **Architecture en couches** |
| Service central + utilisateurs distants | **Client-Serveur** |
| Traitement de données par étapes successives | **Pipe & Filter** |
| Plusieurs outils partagent une source de données | **Référentiel** |

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

### Checklist d'Auto-Évaluation

| # | Je sais... | ✓ |
|---|---|---|
| 1 | Citer les 5 principes SOLID et les expliquer | ☐ |
| 2 | Classer les patterns en 3 catégories (Création/Structure/Comportement) | ☐ |
| 3 | Expliquer Singleton vs classe statique | ☐ |
| 4 | Décrire 5 patterns clés (Singleton, Factory, Observer, Adapter, Decorator) | ☐ |
| 5 | Lister 5 patrons d'architecture (MVC, Couches, Client-Serveur, Référentiel, Pipe&Filter) | ☐ |
| 6 | Associer un contexte à l'architecture appropriée | ☐ |

---

> 📄 **Fin du Document 5** · Suite → [Document 6 : Gestion de Projet](./06_GestionProjet_PERT.md)
