# CM8-9 完整复习资料 — 从软件工程师视角
# Révision Complète CM8-9 — Perspective Ingénieur Logiciel

> **CY Cergy Paris Université — Dr. Fatiha Bousbahi, Dr. Daniela Pamplona**
> **中法双语完整解析 · Analyse Bilingue Complète**
> **涵盖：用例图 · 类图 · 活动图 · 设计模式 · 代码生成 · 架构设计**

---

## 📋 Table des Matières / 目录

| # | Chapitre / 章节 | Contenu / 内容 |
|---|-----------------|---------------|
| 1 | Diagramme de Cas d'Utilisation | 用例图：理论 + 绘图方法 + TD6解答 |
| 2 | Diagramme de Classe | 类图：理论 + 绘图方法 + TD4解答 |
| 3 | Diagramme d'Activités | 活动图：理论 + 绘图方法 + TD7解答 |
| 4 | Design Patterns | 设计模式：SOLID + GoF23 + TD解答 |
| 5 | Génération de Code | 代码生成：UML→Code映射 + Umbrello |
| 6 | Conception Architecturale | 架构设计：模式选择 + TD解答 |
| 7 | Fiches de Révision | 速查表 + 自测清单 |

---

---

# 第1章 — CM8 用例图 / Diagramme de Cas d'Utilisation

---

## 1.0 概述 / Aperçu

> **FR** : Le diagramme de cas d'utilisation (Use Case Diagram) fait partie des **diagrammes de comportement** UML. Il répond à la question fondamentale : **« QUI fait QUOI avec le système ? »** C'est LE diagramme par lequel on commence TOUJOURS un projet — avant même d'écrire une ligne de code.

> **ZH** : 用例图属于UML**行为图**。它回答最根本的问题：**「谁用系统做什么？」** 这是每个项目**必须最先**画的图——甚至在写任何代码之前。

> **🧑‍💻 Perspective SE / 软件工程师视角** : 用例图 = 功能需求的**可视化契约**。它直接映射到：用户故事 (User Stories) → Sprint Backlog → 验收测试 (Acceptance Tests)。画好用例图，你的功能范围就不会跑偏。

---

## 1.1 五大元素 / Les 5 Éléments

### ① Acteur / 参与者 (Actor)

| Aspect | Français | 中文 |
|--------|----------|------|
| **Définition** | Entité EXTERNE qui interagit avec le système. Représente un **RÔLE**, pas une personne spécifique. | 与系统交互的**外部**实体。代表一个**角色**，不是具体的人。 |
| **Notation** | Stick figure (火柴人) + nom du rôle en dessous | 火柴人图标 + 角色名写在下方 |
| **Principal** | Celui qui **INITIE** l'échange | **启动**交互的一方 |
| **Secondaire** | Celui qui est **SOLLICITÉ** par le système | 被系统**调用**的一方 |

`
    o       ← tête / 头
   /|\      ← corps + bras / 身体+手臂
   / \      ← jambes / 腿

  Client    ← nom du rôle / 角色名
`

> **🧠 Comment distinguer Principal vs Secondaire ?**
> Posez la question : « Qui COMMENCE l'action ? » → Principal. « Qui est APPELÉ par le système ? » → Secondaire.
> 问自己：「谁**开始**了动作？」→ 主要。「系统**调用**了谁？」→ 次要。

### ② Cas d'Utilisation / 用例 (Use Case)

| Aspect | Français | 中文 |
|--------|----------|------|
| **Définition** | Fonctionnalité VISIBLE de l'extérieur | 外部**可见**的功能 |
| **Notation** | Ellipse (ovale) | 椭圆 |
| **Nommage** | **TOUJOURS un VERBE À L'INFINITIF** | **必须是动词不定式** |

`
  ┌──────────────────┐
  │  S'authentifier  │   ← JAMAIS « Authentification » (nom) !
  └──────────────────┘
`

> **⚠️ Piège d'examen / 考试陷阱** : JAMAIS de nom (ex: « Paiement »). TOUJOURS un verbe (ex: « Payer »). 千万不要用名词！一定要用动词！

### ③ Association / 关联

Un **trait simple** reliant un acteur à son cas d'utilisation. Signification : « Cet acteur PEUT exécuter ce cas. »
连接参与者与用例的**简单直线**。表示：「该参与者**可以**执行此用例。」

### ④ Frontière du Système / 系统边界

Un **rectangle** délimitant le système. Les cas sont À L'INTÉRIEUR, les acteurs À L'EXTÉRIEUR.
框定系统范围的**矩形**。用例在**里面**，参与者在**外面**。

### ⑤ Relations entre Cas d'Utilisation / 用例间关系

#### A) <<include>> — Inclusion / 包含

| Aspect | Détail |
|--------|--------|
| **Règle** | Le cas A inclut **TOUJOURS** le cas B. B est **OBLIGATOIRE**. |
| **规则** | A **总是**包含B。B是**强制**的。 |
| **Sens flèche** | A —→ B (pointillés, vers le cas INCLUS) |
| **方向** | A —→ B (虚线箭头，指向**被包含**的用例) |

`
 ┌──────────────────┐
 │ Payer cotisation │
 └────────┬─────────┘
          │ <<include>>
          ↓
 ┌──────────────────────┐
 │ Vérifier statut      │
 │ adhérent             │
 └──────────────────────┘
`

#### B) <<extend>> — Extension / 扩展

| Aspect | Détail |
|--------|--------|
| **Règle** | Le cas B étend le cas A de façon **OPTIONNELLE**. B ne s'exécute que sous condition. |
| **规则** | B **可选地**扩展A。B仅在特定条件下执行。 |
| **Sens flèche** | B —→ A (pointillés, vers le cas DE BASE) |
| **方向** | B —→ A (虚线箭头，指向**基础**用例) |

`
 ┌──────────────────┐
 │ Consulter jeux   │
 └────────┬─────────┘
          ↑
          │ <<extend>> (condition: si dispo)
 ┌────────┴─────────┐
 │ Réserver jeu     │
 └──────────────────┘
`

> **⚠️ LA DIFFÉRENCE CRUCIALE Include vs Extend !**

| Critère | <<include>> | <<extend>> |
|---------|---------------|--------------|
| **Obligation** | **TOUJOURS** / 总是 | **OPTIONNEL** / 可选 |
| **Sens flèche** | A → B (vers l'inclus) | B → A (vers la base) |
| **Quand utiliser** | Éviter duplication de code fonctionnel | Ajouter comportement optionnel |

> **🧠 Moyen Mnémotechnique / 记忆方法**:
> - Include = « je vais **CHERCHER** ce dont j'ai besoin » → flèche vers ce qu'on inclut
> - Extend = « je me **BRANCHE** sur la base » → flèche vers la base
> - Include = 「我去**取**需要的东西」→ 箭头指向被包含的
> - Extend = 「我**挂接**到基础上」→ 箭头指向基础

#### C) Généralisation de Cas / 用例泛化

| Aspect | Détail |
|--------|--------|
| **Règle** | Cas SPÉCIALISÉ hérite du cas GÉNÉRAL. Flèche **PLEINE** → vers le général. |
| **规则** | **特化**用例继承**通用**用例。**实心**箭头 → 指向通用。 |

`
 ┌──────────┐
 │ Paiement │  ← général / 通用
 └────┬─────┘
      △ (flèche pleine / 实心箭头)
 ┌────┴─────────┐
 │Paiement carte│  ← spécialisé / 特化
 └──────────────┘
`

#### D) Généralisation d'Acteurs / 参与者泛化

| Aspect | Détail |
|--------|--------|
| **Règle** | Acteur spécialisé hérite de TOUS les cas de l'acteur général. |
| **规则** | 特化参与者继承通用参与者的**所有**用例。 |

---

## 1.2 Méthode de Dessin en 6 Étapes / 六步绘图法

> **🧑‍💻 Perspective SE** : 这套方法是软件工程师拿到需求文档后的标准工作流。

### Étape 1 : Identifier les Acteurs / 识别参与者

Repérez TOUS les rôles. Pour chacun : Principal (il initie) ou Secondaire (il est sollicité) ?
找出**所有**角色。每个判断：主要（启动）还是次要（被调用）？

### Étape 2 : Identifier les Cas d'Utilisation / 识别用例

Pour chaque acteur : « Qu'est-ce qu'il FAIT ? » → Chaque action = un cas (**VERBE À L'INFINITIF**).
对每个参与者：「他**做**什么？」→ 每个动作 = 一个用例（**动词不定式**）。

### Étape 3 : Dessiner la Frontière / 画系统边界

Grand rectangle. Nom du système en haut.
大矩形。顶部写系统名称。

### Étape 4 : Placer Acteurs et Cas / 放置参与者和用例

Acteurs DEHORS, cas DEDANS. Relier par des traits simples.
参与者放**外面**，用例放**里面**。简单直线连接。

### Étape 5 : Ajouter les Relations / 添加关系

Include (toujours) / Extend (optionnel) / Généralisation (héritage).
Include (总是) / Extend (可选) / 泛化 (继承)。

### Étape 6 : Vérifier / 检查

- [ ] Acteurs à l'extérieur ? / 参与者在外部？
- [ ] Cas à l'intérieur ? / 用例在内部？
- [ ] Noms en VERBES ? / 名称是动词？
- [ ] Flèches dans le BON sens ? / 箭头方向正确？

---

## 1.3 Rédaction de Scénario Textuel / 文本场景编写

> **🧑‍💻 Perspective SE** : Le scénario textuel est le pont entre le diagramme UML et le code. Il sert de base pour les **tests d'acceptation** et les **user stories** en Agile.

| Composant | Description (FR) | 描述 (ZH) |
|-----------|-------------------|-----------|
| **Titre** | Nom du cas | 用例名称 |
| **Acteur principal** | Qui initie | 谁启动 |
| **Précondition** | Ce qui est vrai AVANT | 前置条件 |
| **Postcondition** | Ce qui est vrai APRÈS | 后置条件 |
| **Scénario nominal** | Étapes normales (numérotées) | 主流程（编号） |
| **Scénarios alternatifs** | Exceptions, erreurs | 替代流程 |
| **Flot d'exceptions** | Terminaison incorrecte | 异常终止 |

---

## 1.4 Exemple du Cours : La Ludothèque / 课件案例：玩具图书馆

> **FR** : Système de gestion d'une ludothèque (bibliothèque de jeux). Les adhérents empruntent des jeux, participent à des événements, paient leur cotisation en ligne.
> **ZH** : 玩具图书馆管理系统。会员借游戏、参加活动、在线缴费。

### Acteurs identifiés / 识别到的参与者 :
| Acteur | Rôle | Type |
|--------|------|------|
| Internaute / 网民 | Consulter jeux, S'inscrire / 浏览游戏、注册 | Principal |
| Adhérent / 会员 | Emprunter jeux, S'inscrire événement, Payer cotisation / 借游戏、报名活动、缴费 | Principal |
| Conseiller / 顾问 | Gérer emprunts, Organiser événement / 管理借阅、组织活动 | Principal |

### Relations identifiées / 识别到的关系 :
| Relation | Explication |
|----------|-------------|
| **Généralisation acteurs** : Adhérent → Internaute | L'adhérent hérite de tous les cas de l'internaute |
| **Include** : Payer cotisation —→ Vérifier statut adhérent | Le paiement nécessite TOUJOURS la vérification |
| **Extend** : Réserver jeu —→ Consulter jeux | La réservation est OPTIONNELLE (seulement si dispo) |

---

## 1.5 🧑‍💻 Code Mapping / 代码映射

> Le diagramme de cas d'utilisation ne se traduit PAS directement en code, mais il **guide** la structure du projet :

| Élément UML | Équivalent Code/Projet |
|-------------|------------------------|
| Acteur | Rôle utilisateur (RBAC), Persona |
| Cas d'utilisation | Module / Service / API endpoint |
| <<include>> | Fonction utilitaire partagée (DRY principle) |
| <<extend>> | Feature flag / Plugin / Middleware optionnel |
| Scénario nominal | Happy path dans les tests |
| Scénario alternatif | Edge cases / Error handling |

`
Cas d'utilisation           →    API Endpoint
─────────────────────────────────────────────────
S'authentifier              →    POST /auth/login
Consulter jeux              →    GET /games
Payer cotisation            →    POST /payments
`

---

## 1.6 TD 6 — Solutions Complètes / 完整解答

---

### Exercice 1 : Station-Service / 加油站系统

> **Énoncé / 题目** : Système informatique gérant une station-service de distribution d'essence.
> 管理加油站的信息系统。

#### Q1 : Qui est l'acteur — le client, la gâchette ou le pistolet ?
**谁是参与者——客户、扳机还是加油枪？**

| Réponse | |
|---------|---|
| **FR** | **Le client**. Le pistolet et la gâchette sont des parties du système (la pompe), pas des entités externes qui prennent des décisions. L'acteur est celui qui INITIE l'action. |
| **ZH** | **客户**。加油枪和扳机是系统的一部分（加油泵），不是做决策的外部实体。参与者是**启动**动作的人。 |

> **🔑 Leçon** : Un acteur = une entité qui a une INTENTION et qui INITIE une interaction. Un objet inanimé n'est PAS un acteur.
> **教训** : 参与者 = 有**意图**并**启动**交互的实体。无生命物体**不是**参与者。

#### Q2 : Le pompiste peut se servir de l'essence. Est-ce un nouvel acteur ?
**加油工自己加油。他是新参与者吗？**

| Réponse | |
|---------|---|
| **FR** | **Non**. Quand le pompiste se sert de l'essence, il agit comme un **client** — son rôle est le même. Un acteur = un RÔLE, pas une personne. La même personne peut avoir plusieurs rôles, mais ici c'est le même rôle. |
| **ZH** | **不是**。加油工自己加油时，他的行为和一个**客户**一样——角色相同。参与者 = **角色**，不是人。同一个人可以有多个角色，但这里角色相同。 |

> **🔑 Leçon** : « Une personne = un acteur » est FAUX. « Un rôle = un acteur » est VRAI. La même personne physique peut incarner plusieurs acteurs si elle a plusieurs rôles.
> **教训** : 「一个人=一个参与者」是错的。「一个角色=一个参与者」是对的。同一个人如果有多重角色，可以对应多个参与者。

#### Q3 : Le gérant utilise le système pour la gestion. Est-ce un nouvel acteur ?
**经理用系统做管理。他是新参与者吗？**

| Réponse | |
|---------|---|
| **FR** | **Oui**. Le gérant a un rôle DIFFÉRENT du client — il fait de la GESTION (initialisation, rapports, etc.). C'est un nouveau cas d'utilisation → nouvel acteur. |
| **ZH** | **是**。经理的角色与客户**不同**——他做**管理**工作（初始化、报表等）。这是新用例 → 新参与者。 |

> **🔑 Leçon** : Si le RÔLE change → nouvel acteur. Si le rôle est le même → même acteur (même si la personne est différente).
> **教训** : **角色**变了 → 新参与者。角色相同 → 同一参与者（即使不是同一个人）。

#### Q4 : Le chef d'atelier remplace le gérant et est aussi mécanicien. Comment modéliser ?
**车间主任取代经理且也是机械师。如何建模？**

| Réponse | |
|---------|---|
| **FR** | Le chef d'atelier est un nouvel acteur qui se **généralise** en Gérant (il hérite de tous ses cas). Il a le double rôle : gestion + entretien. On utilise la **généralisation d'acteurs** : Chef d'atelier —▷ Gérant. |
| **ZH** | 车间主任是新参与者，**泛化**自经理（继承所有经理的用例）。他拥有双重角色：管理+维修。使用**参与者泛化**：车间主任 —▷ 经理。 |

`
       Gérant
         △
         │ (généralisation / 泛化)
  Chef d'atelier
  (hérite de Gérant + nouveaux cas : entretien véhicules)
  (继承经理用例 + 新增用例：车辆维修)
`

---

### Exercice 2 : Système de Caisse / 收银系统

> **Énoncé / 题目** : Caisse enregistreuse d'un magasin — enregistrement articles, paiement (liquide/chèque/carte), coupons réduction, transmission stock, initialisation.
> 商店收银系统——商品登记、支付（现金/支票/银行卡）、优惠券、库存传输、初始化。

#### ① Identifier les Acteurs et leurs Types / 识别参与者及类型

| Acteur | Type | Justification |
|--------|------|---------------|
| **Caissier / 收银员** | Principal | Il INITIE l'enregistrement des articles et le signalement de fin de vente |
| **Responsable / 负责人** | Principal | Il INITIE l'initialisation des caisses chaque matin |
| **Centre d'autorisation / 授权中心** | Secondaire | SOLLICITÉ par la caisse pour vérifier la solvabilité (chèque/carte) |
| **Gestion de stocks / 库存管理** | Secondaire | SOLLICITÉ par la caisse après la vente pour transmettre les infos |

> **⚠️ Le Client N'EST PAS un acteur !** Il n'agit pas directement sur le système de caisse — c'est le caissier qui manipule la caisse. Le client choisit le mode de paiement mais n'interagit pas avec le logiciel.
> **客户不是参与者！** 他不直接操作收银系统——收银员操作。客户选择支付方式但不与软件交互。

#### ② Identifier les Cas d'Utilisation / 识别用例

| Acteur | Cas d'utilisation (Verbe à l'infinitif !) |
|--------|------------------------------------------|
| Caissier | Enregistrer articles, Signaler fin de vente, Encaisser paiement |
| Responsable | Initialiser caisses |
| (Système) | Transmettre informations au stock |

#### ③ Relations entre Cas / 用例间关系

| Cas A | Relation | Cas B | Pourquoi ? |
|-------|----------|-------|------------|
| Signaler fin de vente | <<include>> → | Paiement | **TOUJOURS** obligatoire : toute vente se termine par un paiement |
| Signaler fin de vente | ← <<extend>> | Appliquer coupons | **OPTIONNEL** : seulement si le client présente des coupons |
| Paiement | ← Généralisation | Paiement Liquide | « est-un » type de paiement |
| Paiement | ← Généralisation | Paiement Chèque | « est-un » type de paiement |
| Paiement | ← Généralisation | Paiement Carte | « est-un » type de paiement |
| Signaler fin de vente | <<include>> → | Transmettre infos au stock | **TOUJOURS** : après chaque vente |

#### ④ Diagramme Complet / 完整用例图

`
                 ┌─────────────────────────────────────────────┐
                 │           SYSTÈME DE CAISSE                 │
                 │                                             │
       o         │  ┌──────────────────┐                      │
      /|\────────┼─→│Enregistrer       │                      │
      / \        │  │articles          │                      │
    Caissier     │  └────────┬─────────┘                      │
                 │           │ <<include>>                     │
                 │           ↓                                 │
                 │  ┌──────────────────┐     <<extend>>       │
                 │  │Signaler fin      │←─────────────┐       │
                 │  │de vente          │              │       │
                 │  └────────┬─────────┘     ┌────────┴──────┐│
                 │           │               │Appliquer      ││
                 │           │ <<include>>   │coupons        ││
                 │           ↓               └───────────────┘│
                 │  ┌──────────────────┐                      │
                 │  │    Paiement      │←── Centre d'autor.   │
                 │  └────────┬─────────┘                      │
                 │           △                                 │
                 │   ┌───────┼───────┐                        │
                 │   │       │       │                         │
                 │ ┌─┴───┐ ┌─┴───┐ ┌─┴──────┐                │
                 │ │Liq. │ │Chèq.│ │Carte   │                │
                 │ └─────┘ └─────┘ └────────┘                │
                 │           │                                 │
                 │           │ <<include>>                     │
                 │           ↓                                 │
                 │  ┌──────────────────┐                      │
                 │  │Transmettre infos │←── Gestion stocks    │
                 │  │au stock          │                      │
                 │  └──────────────────┘                      │
                 │                                             │
       o         │  ┌──────────────────┐                      │
      /|\────────┼─→│Initialiser       │                      │
      / \        │  │caisses           │                      │
  Responsable    │  └──────────────────┘                      │
                 └─────────────────────────────────────────────┘
`

#### ⑤ Description Textuelle du Cas « Paiement » / 用例文本描述

| Champ | Valeur |
|-------|--------|
| **Identification** | 1 |
| **Nom du cas** | Paiement / 支付 |
| **Objectif** | Détailler les étapes permettant au caissier d'accepter le paiement |
| **Acteur principal** | Caissier / 收银员 |
| **Pré-condition** | Signalisation de fin de vente (total affiché) |
| **Post-condition** | Vente enregistrée, ticket imprimé |

**Scénario nominal / 主流程 :**
1. Le client choisit son mode de paiement
2. Le caissier traite le paiement selon le mode choisi
3. La caisse enregistre la vente et imprime un ticket
4. Le caissier donne le ticket au client

**Scénarios alternatifs / 替代流程 :**
- 2a. **Numéraire** : le caissier encaisse l'argent, la caisse calcule la monnaie
- 2b. **Chèque** : vérification solvabilité via centre d'autorisation
- 2c. **Carte de crédit** : terminal bancaire transmet demande d'autorisation

**Flot d'exception / 异常流 :**
- 2b-Err. Chèque refusé par le centre d'autorisation → demande autre mode de paiement
- 2c-Err. Carte refusée → demande autre mode de paiement

---

> ✅ **Chapitre 1 terminé.** Vous savez maintenant identifier les acteurs, dessiner un diagramme de cas d'utilisation complet, et rédiger un scénario textuel prêt pour les tests.
---

# 第2章 — CM8 类图 / Diagramme de Classe

---

## 2.0 概述 / Aperçu

> **FR** : Le diagramme de classe fait partie des **diagrammes de structure** UML. Il montre la structure STATIQUE du système : classes, attributs, méthodes, et leurs relations. C'est le diagramme qui se traduit le PLUS DIRECTEMENT en code orienté objet.

> **ZH** : 类图属于UML**结构图**。它展示系统的**静态**结构：类、属性、方法及其关系。这是**最直接**映射到面向对象代码的图。

> **🧑‍💻 Perspective SE** : 类图 = 代码蓝图。在Java/Python中，类图的一个class直接对应一个class文件。画好类图后，代码生成工具可以自动生成骨架代码。

---

## 2.1 Structure d'une Classe / 类的结构 (3 Compartiments)

```
┌──────────────────────────┐
│     Nom de la Classe     │  ← Compartiment 1 : NOM (obligatoire)
│     类名 (PascalCase)    │
├──────────────────────────┤
│ - attribut1 : Type       │  ← Compartiment 2 : ATTRIBUTS
│ # attribut2 : Type       │
│ + attribut3 : Type       │
├──────────────────────────┤
│ + méthode1() : Type      │  ← Compartiment 3 : MÉTHODES
│ - méthode2() : void      │
└──────────────────────────┘
```

### Visibilité / 可见性

| Symbole | Nom | Accessible par... | 可被...访问 | Équivalent Code |
|---------|-----|-------------------|-------------|-----------------|
| `+` | Public / 公有 | TOUTES les classes | 所有类 | `public` en Java |
| `-` | Privé / 私有 | La classe elle-même UNIQUEMENT | 仅该类自身 | `private` en Java |
| `#` | Protégé / 保护 | La classe + ses SOUS-CLASSES | 该类+子类 | `protected` en Java |

---

## 2.2 Multiplicité / 多重性

| Notation | Signification (FR) | 含义 (ZH) | Équivalent Code |
|----------|---------------------|-----------|-----------------|
| `1` | Exactement UN | 恰好一个 | Objet simple |
| `0..1` | ZÉRO ou UN | 零或一个 | `Optional<T>` / nullable |
| `*` ou `0..*` | ZÉRO ou PLUSIEURS | 零或多个 | `List<T>`, `Set<T>` |
| `1..*` | UN ou PLUSIEURS | 一个或多个 | `List<T>` (non vide) |
| `n..m` | Entre n et m | n到m个 | Validation custom |

---

## 2.3 Les 5 Relations entre Classes / 类间五种关系

> **🧑‍💻 Perspective SE** : 这5种关系直接对应不同的代码实现方式。选错关系 = 代码架构错误。

### Tableau Récapitulatif / 总览表

| # | Relation | Symbole | Mot-Clé | Code Équivalent |
|---|----------|---------|---------|-----------------|
| 1 | **Association** | — (ligne simple) | « utilise » | Attribut de type classe |
| 2 | **Généralisation** | △ (flèche pleine → parent) | « est-un » | `extends` / `inherits` |
| 3 | **Dépendance** | ⇢ (flèche pointillée) | « utilise temporairement » | Paramètre de méthode / import |
| 4 | **Agrégation** | ◇— (losange VIDE côté conteneur) | « a-un » FAIBLE | Collection avec cycle de vie indépendant |
| 5 | **Composition** | ◆— (losange PLEIN côté conteneur) | « partie-de » FORT | Collection avec cycle de vie lié |

---

### ① Association / 关联

```
┌─────────┐              ┌─────────┐
│ Personne│──────────────│ Langage │
└─────────┘   utilise    └─────────┘
```

**Code Java :**
```java
class Personne {
    private Langage langage;  // association simple
}
```

### ② Généralisation / 泛化 (Héritage)

```
       ┌──────────┐
       │ Véhicule │  ← parent / 父类
       └────┬─────┘
            △
     ┌──────┴──────┐
     │             │
┌────┴────┐  ┌─────┴────┐
│ Voiture │  │   Moto   │  ← enfants / 子类
└─────────┘  └──────────┘
```

**Code Java :**
```java
class Voiture extends Véhicule { }
class Moto extends Véhicule { }
```

### ③ Dépendance / 依赖

```
┌─────────┐               ┌──────────┐
│ Service │⇢ ─ ─ ─ ─ ─ ─→│ Logger   │
└─────────┘   utilise     └──────────┘
              temporairement
```

**Code Java :**
```java
class Service {
    void faireQqchose(Logger log) {
        log.write("action");
    }
}
```

### ④ Agrégation / 聚合 (FAIBLE)

```
┌─────────┐ ◇────────── ┌──────────┐
│ Équipe  │             │  Membre  │
└─────────┘   a-un      └──────────┘
```

> Si l'équipe est dissoute, les membres EXISTENT TOUJOURS.
> 团队解散后成员**仍然存在**。

### ⑤ Composition / 组合 (FORT)

```
┌─────────┐ ◆────────── ┌──────────┐
│ Maison  │             │   Pièce  │
└─────────┘  partie-de  └──────────┘
```

> Si la maison est détruite, les pièces sont DÉTRUITES AUSSI.
> 房子被拆，房间也**随之销毁**。

---

### ⚠️ Agrégation vs Composition — Tableau Détaillé

| Critère | Agrégation (◇) / 聚合 | Composition (◆) / 组合 |
|---------|------------------------|--------------------------|
| **Relation** | « a-un » FAIBLE | « partie-de » FORT |
| **Cycle de vie** | Indépendant | Dépendant |
| **Exemple (FR)** | Équipe ◇— Membre | Maison ◆— Pièce |
| **Exemple (ZH)** | 团队◇—成员 | 房子◆—房间 |
| **Symbole UML** | Losange VIDE (◇) | Losange PLEIN (◆) |
| **Suppression parent** | L'enfant survit | L'enfant est supprimé |

> **🧠 Comment choisir ?** Posez la question : « Si je détruis le conteneur, le contenu doit-il aussi disparaître ? »
> - OUI → **Composition**
> - NON → **Agrégation**

---

## 2.4 Classes Abstraites et Énumérations

```
┌──────────────────────────┐
│    <<abstrait>>          │
│      Véhicule            │  ← nom en ITALIQUE
├──────────────────────────┤
│ + drive() : void         │
│ + park() : void          │
└──────────────────────────┘

┌──────────────────────────┐
│   <<énumération>>        │
│      Boolean             │
├──────────────────────────┤
│ True                     │
│ False                    │
└──────────────────────────┘
```

---

## 2.5 🧑‍💻 Code Mapping / 代码映射

### Diagramme de Classe → Java

| UML | Java |
|-----|------|
| Classe `Personne` | `class Personne { }` |
| `- nom : String` | `private String nom;` |
| `+ getNom() : String` | `public String getNom() { return nom; }` |
| `1` (multiplicité) | `private Type attribut;` |
| `*` (multiplicité) | `private List<Type> attributs;` |
| Généralisation (△) | `class A extends B { }` |
| Agrégation (◇) | `private List<Type> enfants;` |
| Composition (◆) | `private List<Type> enfants = new ArrayList<>();` |

### Diagramme de Classe → Python

| UML | Python |
|-----|--------|
| Classe `Personne` | `class Personne:` |
| `- nom : String` | `self.__nom = ""` (name mangling) |
| `+ getNom() : String` | `@property` + `def nom(self):` |
| `*` (multiplicité) | `self.attributs: list[Type] = []` |
| Généralisation (△) | `class A(B):` |
| Composition (◆) | Création dans `__init__` |

---

## 2.6 Exemple du Cours : Système de Commande

```
┌─────────────────────────────────────────────────────┐
│                    Client                           │
├─────────────────────────────────────────────────────┤
│ + name: String                                      │
│ + email: String                                     │
├─────────────────────────────────────────────────────┤
│ + register(): void                                  │
│ + editInfo(): void                                  │
└──────────────────────┬──────────────────────────────┘
                       │ 1
                       │ place
                       │ *
┌──────────────────────┴──────────────────────────────┐
│                    Commande                         │
├─────────────────────────────────────────────────────┤
│ + number: int                                       │
│ + details: String                                   │
├─────────────────────────────────────────────────────┤
│ + addOrder(): void                                  │
│ + modifyOrder(): void                               │
└──────────────────────┬──────────────────────────────┘
                       △
            ┌──────────┴──────────┐
            │                     │
┌───────────┴──────────┐ ┌───────┴──────────────┐
│  Commande spéciale   │ │  Commande normale    │
├──────────────────────┤ ├──────────────────────┤
│ + date: String       │ │                      │
├──────────────────────┤ ├──────────────────────┤
│ + dispatch(): void   │ │ + dispatch(): void   │
│ + receive(): void    │ │                      │
└──────────────────────┘ └──────────────────────┘
```

---

## 2.7 TD Classe & Multiplicité — Solutions Complètes

---

### Exercice 1 : Identifier le Type de Relation

| # | Énoncé (FR) / 题目 (ZH) | Relation | Justification |
|---|--------------------------|----------|---------------|
| 1 | « Une transaction boursière est un achat ou une vente » | **Généralisation** | « est un » → héritage |
| | 股票交易是买入或卖出 | **泛化** | 「是一个」→ 继承 |
| 2 | « Une personne utilise un langage de programmation » | **Association** | Lien simple d'utilisation |
| | 人使用编程语言 | **关联** | 简单的使用关系 |
| 3 | « Les modems et claviers sont des périphériques E/S » | **Généralisation** | « sont des » → héritage |
| | 调制解调器和键盘是输入输出外设 | **泛化** | 「是」→ 继承 |

---

### Exercice 2 : Classe Personne

**Représentation UML :**

```
┌──────────────────────────┐
│        Personne          │
├──────────────────────────┤
│ - nom : String           │
│ - prénom : String        │
│ - sexe : String          │
│ - âge : int              │
│ - salaire : float        │
│ - autresRevenus : float  │
│ - coefSalaire : float    │
│ - coefAutresRevenus:float│
├──────────────────────────┤
│ + getNom() : String      │
│ + getPrénom() : String   │
│ + getÂge() : int         │
│ + calculerRevenus():float│
│ + calculerCharges():float│
└──────────────────────────┘
```

> **🧑‍💻 Note SE** : `calculerRevenus()` = `salaire + autresRevenus`. `calculerCharges()` = `salaire * coefSalaire + autresRevenus * coefAutresRevenus`.

---

### Exercice 3 : Multiplicité Magasin/Article

**Q1 — Explication du diagramme initial :**
Un magasin vend un ou plusieurs articles. Chaque article est vendu par exactement un magasin.
一个商店销售一个或多个商品。每个商品恰好由一个商店销售。

```
Magasin ──────────── Article
   1            1..*
```

**Q2 — Articles vendus par plusieurs magasins :**
```
Magasin ──────────── Article
  1..*          1..*
```

**Q3 — Article peut ne pas être proposé :**
```
Magasin ──────────── Article
  1..*          0..*
```

> **🔑 Logique** : On part de la multiplicité la plus stricte, puis on RELÂCHE les contraintes.
> **修改逻辑** : 从最严格的多重性开始，根据新事实**放宽**约束。

---

### Exercice 4 : Type de Relation

| Énoncé | Relation | Symbole | Diagramme |
|--------|----------|---------|-----------|
| « Un répertoire contient des fichiers » | **Composition** | ◆ | Répertoire ◆— Fichier |
| « Une pièce se compose de murs » | **Composition** | ◆ | Pièce ◆— Mur |
| « Modems et claviers sont des périphériques » | **Généralisation** | △ | Modem —▷ Périphérique |

---

### Exercice 5 : Système de Transport Aérien

**Multiplicités :**
```
Ville ──────────── Aéroport
  1            1..*

Vol ──────────── Aéroport (départ)
  1            1
Vol ──────────── Aéroport (arrivée)
  1            1
```

**Q1** : Une ville a 1..* aéroports. Un aéroport est dans exactement 1 ville.
**Q2** : Noms — Ville→Aéroport: « possède ». Vol→Aéroport: « décolle de » / « atterrit à ».
**Q3** : **Oui**, on peut connaître l'aéroport de départ et d'arrivée car la multiplicité est 1.
**Q4** : **Non**, le modèle ne permet pas les escales. Il faudrait ajouter une classe « Escale ».

---

> ✅ **Chapitre 2 terminé.**

---

# 第3章 — CM9 活动图 / Diagramme d'Activités

---

## 3.0 概述 / Aperçu

> **FR** : Le diagramme d'activités fait partie des **diagrammes de comportement** UML. Il modélise le **FLUX d'un processus** — comme un organigramme (flowchart). Il répond à : **« Comment ça se déroule, étape par étape ? »**

> **ZH** : 活动图属于UML**行为图**。它建模**过程的流程**——就像流程图。回答：**「一步步如何执行？」**

> **🧑‍💻 Perspective SE** : 活动图 = 业务流程的**伪代码可视化版**。它直接映射到代码中的控制流（if/else, while, fork/join）。画好活动图后，你基本上已经有了方法的骨架逻辑。

---

## 3.1 Les Éléments / 绘图元素

| Élément (FR) / 元素 (ZH) | Symbole | Rôle (FR) / 作用 (ZH) | Équivalent Code |
|---|---|---|---|
| **Noeud initial** / 初始节点 | ● | Point de DÉPART unique / 唯一起点 | Début de méthode |
| **Action** / 动作 | [Action] | Une ÉTAPE / 一个步骤 | Instruction / appel fonction |
| **Flot de contrôle** / 控制流 | → | Passage entre actions / 步骤间流转 | Flux séquentiel |
| **Décision** / 决策节点 | ◇ | Branchement (1 entrée, N sorties) / 条件分支 | `if/else`, `switch` |
| **Fusion** / 合并节点 | ◇ | Regrouper branches / 合并分支 | Fin de `if/else` |
| **Fork** / 分叉 | ═══ | Diviser en PARALLÈLE / 拆分为并行 | `Thread.start()`, `async` |
| **Join** / 汇合 | ═══ | Synchroniser (attendre TOUT) / 同步等待 | `join()`, `await Promise.all()` |
| **Fin activité** / 活动终止 | ◎ | Fin de TOUTE l'activité / 全部结束 | `return` / fin méthode |
| **Fin flot** / 流终止 | ⊗ | Fin d'UN flux parallèle / 一个并行流结束 | Fin d'un thread |
| **Swimlane** / 泳道 | ┃ | Regrouper par acteur / 按参与者分组 | Classe / Module différent |

---

## 3.2 🧑‍💻 Méthode de Dessin / 绘图方法

> **Étape 1** : Identifier le processus à modéliser (ex: « Retrait au distributeur »)
> **Étape 2** : Lister TOUTES les étapes dans l'ordre chronologique
> **Étape 3** : Identifier les conditions de branchement (if/else) → nœuds de décision
> **Étape 4** : Identifier ce qui peut se faire EN PARALLÈLE → Fork
> **Étape 5** : Identifier où on ATTEND la fin des parallèles → Join
> **Étape 6** : (Optionnel) Assigner chaque action à un acteur → Swimlanes

---

## 3.3 Exemple Simple : Code PIN / 简单示例

```
     ● (début)
     │
     ↓
┌─────────────┐
│ Saisir code │
└──────┬──────┘
       │
       ↓
      ◇  Code correct ?
      │\
     /  \
[OUI]/    \[NON]
    /      \
   ↓        ↓
┌──────┐   ◇ 3e tentative ?
│Accès │   │\
│ok    │  /  \
└──┬───┘ [NON] [OUI]
   │       │     ↓
   ↓       │  ┌──────┐
   ◎       │  │Carte │
  (fin)    │  │avalée│
           │  └──┬───┘
           │     │
           │     ↓
           │     ◎
           │    (fin)
           │
           └──→ (retour saisie)
```

---

## 3.4 Exemple Complet : ATM / 完整示例：取款机

> **Processus** : Insérer carte → Vérifier validité → Saisir code (3 tentatives max) → Saisir montant → Vérifier solde → Restituer carte + délivrer billets + imprimer reçu.

```
                    ●
                    │
                    ↓
            ┌───────────────┐
            │ Insérer carte │
            └───────┬───────┘
                    │
                    ↓
            ┌───────────────┐
            │ Vérifier      │
            │ validité      │
            └───────┬───────┘
                    │
                    ↓
            ┌───────────────┐
            │ Saisir code   │
            └───────┬───────┘
                    │
                    ↓
                   ◇  Code OK ?
                   │\
                  /  \
            [OUI]/    \[NON]
                /      \
               ↓        ↓
       ┌───────────┐   ◇ 3e tentative ?
       │Saisir     │   │\
       │montant    │  /  \
       └─────┬─────┘ [OUI] [NON]
             │        ↓     │
             ↓    ┌────────┐│
            ◇     │Avaler  ││
        Solde OK? │carte   ││
           │\     └───┬────┘│
          /  \        │     │
    [OUI]/    \[NON]  ↓     │
        /      \      ◎     │
       ↓        ↓           │
┌──────────┐ ┌──────────┐   │
│Restituer │ │"Solde    │   │
│carte     │ │insuffi-  │   │
└────┬─────┘ │sant"     │   │
     │       └─────┬────┘   │
     ↓             │        │
┌──────────┐      └────←───┘
│Délivrer  │
│billets   │
└────┬─────┘
     │
     ↓
┌──────────┐
│Imprimer  │
│reçu      │
└────┬─────┘
     │
     ↓
     ◎
```

---

## 3.5 Fork / Join — Parallélisme / 并行与同步

> **🧑‍💻 Perspective SE** : Fork/Join est l'équivalent UML de la programmation concurrente. C'est crucial pour modéliser des systèmes modernes.

```
        ┌──────────────┐
        │  Action A    │
        └──────┬───────┘
               │
        ═══════╪═══════   ← Fork : diviser
        │      │      │
        ↓      ↓      ↓
   ┌──────┐┌──────┐┌──────┐
   │Act B ││Act C ││Act D │  ← 3 actions EN PARALLÈLE
   └──┬───┘└──┬───┘└──┬───┘
      │       │       │
      ════════╪═══════╪══   ← Join : synchroniser
              │
              ↓
        ┌──────────────┐
        │  Action E    │
        └──────────────┘
```

> **⚠️ Piège** : Fork et Join doivent être ÉQUILIBRÉS. Autant de sorties du Fork = autant d'entrées du Join.
> **陷阱** : Fork和Join必须**平衡**。Fork的出口数 = Join的入口数。

---

## 3.6 Fin Activité (◎) vs Fin Flot (⊗)

| Symbole | Signification | Quand l'utiliser ? |
|---------|---------------|-------------------|
| ◎ | Fin de **TOUTE** l'activité | Dernière étape, tout s'arrête |
| ⊗ | Fin d'**UN** flux parallèle | Un thread se termine, les autres continuent |

---

## 3.7 🧑‍💻 Code Mapping / 代码映射

| Élément Activité | Pseudo-code |
|------------------|-------------|
| Action | `faireAction()` |
| Décision | `if (condition) { ... } else { ... }` |
| Fork | `Thread t1 = new Thread(...); t2 = ...; t1.start(); t2.start();` |
| Join | `t1.join(); t2.join();` |
| Fin activité | `return;` |
| Boucle (retour) | `while (tentatives < 3) { ... }` |

---

## 3.8 TD 7 — Solution Complète / 完整解答

---

### Exercice 1 : Distributeur de Billets / ATM取款机

> **Énoncé / 题目** : Décrire le fonctionnement d'un distributeur de billets via un diagramme d'activités.
> 用活动图描述ATM取款机的工作流程。

**Étape 1 — Identifier les actions / 识别步骤 :**
1. Insérer carte / 插卡
2. Vérifier validité / 验证有效性
3. Saisir code / 输入密码
4. Vérifier code / 验证密码
5. Compter tentatives / 计数尝试
6. Avaler carte / 吞卡
7. Saisir montant / 输入金额
8. Vérifier solde / 验证余额
9. Informer solde insuffisant / 提示余额不足
10. Restituer carte / 退卡
11. Délivrer billets / 出钞
12. Imprimer reçu / 打印收据

**Étape 2 — Identifier les décisions / 识别分支 :**
- Carte valide ? → [OUI] continuer / [NON] fin
- Code correct ? → [OUI] saisir montant / [NON] vérifier tentatives
- 3e tentative ? → [OUI] avaler carte / [NON] ressaisir
- Solde suffisant ? → [OUI] délivrer / [NON] informer + ressaisir

**Étape 3 — Diagramme complet / 完整活动图 :**

```
                    ●
                    │
                    ↓
            ┌───────────────┐
            │ Insérer carte │
            └───────┬───────┘
                    │
                    ↓
            ┌───────────────┐
            │ Vérifier      │
            │ validité      │
            └───────┬───────┘
                    │
                    ↓
            ┌───────────────┐
            │ Saisir code   │  ←──┐
            └───────┬───────┘     │
                    │             │
                    ↓             │
                   ◇  Code OK ?   │
                   │\             │
                  /  \            │
            [OUI]/    \[NON]      │
                /      \         │
               ↓        ↓        │
       ┌───────────┐   ◇ 3e tentative ?
       │Saisir     │   │\         │
       │montant    │  /  \        │
       └─────┬─────┘ [NON][OUI]──┘
             │        │     ↓
             ↓        │  ┌────────┐
            ◇         │  │Avaler  │
        Solde OK?     │  │carte   │
           │\         │  └───┬────┘
          /  \        │      │
    [OUI]/    \[NON]  │      ↓
        /      \     │      ◎
       ↓        ↓    │
┌──────────┐ ┌──────────┐
│Restituer │ │"Solde    │
│carte     │ │insuffi-  │
└────┬─────┘ │sant"     │
     │       └─────┬────┘
     ↓             │
┌──────────┐      └────→ (retour saisie montant)
│Délivrer  │
│billets   │
└────┬─────┘
     │
     ↓
┌──────────┐
│Imprimer  │
│reçu      │
└────┬─────┘
     │
     ↓
     ◎
```

---

> ✅ **Chapitre 3 terminé.** Vous savez maintenant modéliser n'importe quel processus avec un diagramme d'activités.

---

# 第4章 — CM9 设计模式 / Design Patterns (Patrons de Conception)

---

## 4.0 概述 / Aperçu

> **FR** : Un patron de conception (Design Pattern) est une **solution éprouvée** à un **problème récurrent** dans un contexte donné. Popularisé par le « Gang of Four » (GoF) en 1994. Ce n'est PAS du code prêt à copier-coller — c'est un **modèle de solution** que vous adaptez.

> **ZH** : 设计模式是针对特定上下文中**反复出现**的问题的**经过验证**的解决方案。由「四人帮」(GoF)于1994年推广。**不是**复制粘贴的代码——是一个需要你**适配**的**解决方案模板**。

> **🧑‍💻 Perspective SE** : 设计模式 = **代码架构的最佳实践词汇表**。当你跟另一个工程师说「这里用Singleton」或「用Observer解耦」，你们瞬间就达成了共识，不需要解释50行代码。这就是设计模式的力量。

---

## 4.1 Les Principes SOLID / SOLID五原则

> **FR** : SOLID est la BASE des design patterns. Si vous ne comprenez pas SOLID, vous appliquerez les patterns mécaniquement sans comprendre POURQUOI.

> **ZH** : SOLID是设计模式的**基础**。不理解SOLID，你只能机械套用模式而不理解**为什么**。

| L | Principe (FR) | 原则 (ZH) | Explication Simple | Anti-Exemple |
|---|---------------|------------|-------------------|--------------|
| **S** | Responsabilité Unique | 单一职责 | Une classe = UNE raison de changer | Une classe `User` qui gère aussi l'envoi d'emails |
| **O** | Ouvert/Fermé | 开闭原则 | Ouvert à l'extension, Fermé à la modification | Modifier une classe existante pour ajouter une feature |
| **L** | Substitution de Liskov | 里氏替换 | Une sous-classe doit pouvoir remplacer sa classe parent | `Rectangle` et `Carré` (setLargeur casse le contrat) |
| **I** | Ségrégation des Interfaces | 接口隔离 | Plusieurs interfaces spécifiques > une interface générale | Une interface `Worker` avec `work()` ET `eat()` |
| **D** | Inversion de Dépendance | 依赖倒置 | Dépendre d'abstractions, pas de concrétions | `Service` qui fait `new MySQLDatabase()` en dur |

---

## 4.2 Classification GoF / GoF 23种模式分类

| Catégorie (FR/ ZH) | Rôle | Patterns Clés (Cours) |
|---|---|---|
| **Création** / 创建型 (5) | Gérer la CRÉATION d'objets | **Singleton**, Factory Method, Abstract Factory, Builder, Prototype |
| **Structure** / 结构型 (7) | Organiser les RELATIONS entre classes | **Adapter**, **Composite**, Decorator, Facade, Proxy, Bridge, Flyweight |
| **Comportement** / 行为型 (11) | Gérer les INTERACTIONS et responsabilités | **Observer**, Strategy, Command, State, Template Method, Chain of Responsibility |

---

## 4.3 Patterns Clés du Cours / 课件重点模式详解

---

### ① Singleton / 单例模式

> **FR** : Garantit qu'une classe n'a qu'**UNE SEULE instance** et fournit un point d'accès **GLOBAL**. Utilisé pour : connexion DB, logger, configuration.
> **ZH** : 确保一个类只有**一个**实例，提供**全局**访问点。用于：数据库连接、日志、配置。

**Structure UML :**
```
┌─────────────────────────┐
│        Database         │
├─────────────────────────┤
│ - INSTANCE : Database   │  ← instance unique (static)
├─────────────────────────┤
│ - Database()            │  ← constructeur PRIVÉ !
│ + getInstance():Database│  ← point d'accès global
│ + query(sql:String)     │
└─────────────────────────┘
```

**Code Java :**
```java
public class Database {
    private static final Database INSTANCE = new Database();

    private Database() {
        // initialisation
    }

    public static Database getInstance() {
        return INSTANCE;
    }
}
```

**Code Python :**
```python
class Database:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
```

### Singleton vs Classe Statique — Différence CRUCIALE !

| Critère | Singleton | Classe Statique |
|---------|-----------|-----------------|
| **Instance** | Un OBJET | Pas d'instance |
| **Interface** | **PEUT** implémenter | **NE PEUT PAS** |
| **Héritage** | **OUI** | **NON** |
| **Polymorphisme** | **OUI** | **NON** |
| **Testabilité** | Mockable | Difficile |

> **🔑 Leçon** : La différence clé = Singleton peut implémenter une INTERFACE. C'est ça qui le rend testable et flexible.

> **⚠️ Attention** : Le Singleton est souvent ABUSÉ. Il crée un état global = difficulté de test. Utilisez-le UNIQUEMENT quand une seule instance est VRAIMENT nécessaire.

---

### ② Observer / 观察者模式

> **FR** : Permet à un objet (Observer) d'être informé du changement d'état d'un autre objet (Observable) **sans couplage fort**. L'Observable notifie tous ses observateurs automatiquement.
> **ZH** : 允许对象(Observer)在另一对象(Observable)状态变化时被通知，**无需强耦合**。Observable自动通知所有观察者。

**Structure UML :**
```
┌──────────────┐         ┌──────────────────┐
│ <<interface>>│         │   Observable     │
│   Observer   │◄────────│ (Subject)        │
├──────────────┤         ├──────────────────┤
│+update()     │         │+addObserver()    │
└──────────────┘         │+removeObserver() │
        △                │+notifyObservers()│
        │                └──────────────────┘
        │
┌───────┴───────┐
│ConcreteObserver│
├───────────────┤
│+update()      │
└───────────────┘
```

**Exemple du Cours — Détecteur de Fumée / 烟雾探测器 :**

```java
// Observable (le signal)
class Signal extends Observable {
    void setData(byte[] lbData) {
        setChanged();          // marque le changement
        notifyObservers();     // notifie TOUS les observers
    }
}

// Observer (le panneau d'affichage)
class JPanelSignal extends JPanel implements Observer {
    void init(Signal lSigAObserver) {
        lSigAObserver.addObserver(this);  // s'inscrire
    }
    void update(Observable observable, Object objectConcerne) {
        repaint();  // réagir à la notification
    }
}
```

> **🧑‍💻 SE Note** : C'est le pattern derrière tous les systèmes d'événements : DOM events en JS, RxJS, React useEffect, Kafka consumers...

---

### ③ Composite / 组合模式

> **FR** : Crée une structure **arborescente** où chaque élément implémente la même interface. Permet de traiter un objet unique et un groupe d'objets de façon UNIFORME.
> **ZH** : 创建**树形**结构，每个元素实现相同接口。允许**统一**处理单个对象和对象组。

**Exemple : Système de Fichiers / 文件系统**
```
          ┌────────────────┐
          │ <<interface>>  │
          │ FileComponent  │
          ├────────────────┤
          │ +getSize()     │
          └───────┬────────┘
                  △
        ┌─────────┴─────────┐
        │                   │
┌───────┴───────┐   ┌───────┴───────┐
│     File      │   │   Directory   │
├───────────────┤   ├───────────────┤
│ - size: int   │   │ - children:   │
├───────────────┤   │   List<File   │
│ +getSize():int│   │   Component>  │
└───────────────┘   ├───────────────┤
                    │ +getSize():int│
                    │  = sum(children│
                    │    .getSize())│
                    └───────────────┘
```

```java
// Traitement uniforme : getSize() sur un fichier OU un dossier
FileComponent root = new Directory(...);
int totalSize = root.getSize();  // fonctionne pour les deux !
```

---

### ④ Adapter / 适配器模式

> **FR** : Permet d'utiliser deux (ou plus) librairies qui font la même chose mais n'ont PAS la même API, sans modifier le code client.
> **ZH** : 允许使用两个（或多个）功能相同但API**不同**的库，无需修改客户端代码。

**Exemple du Cours — Envoi de SMS :**

```
Problème :
  GoogleSMS.sendSMSBulk(List<String> numbers, String msg)
  AmazonSMS.send(String msg, String[] phones)
  → API DIFFÉRENTES, même fonctionnalité !

Solution : Adapter
  ┌──────────────┐
  │ <<interface>>│
  │  SMSSender   │
  ├──────────────┤
  │+send(msg,    │
  │ numbers)     │
  └──────┬───────┘
         △
   ┌─────┴─────┐
   │           │
┌──┴────────┐ ┌┴───────────┐
│GoogleSMS  │ │AmazonSMS    │
│Adapter    │ │Adapter      │
├───────────┤ ├────────────┤
│+send()    │ │+send()      │
│ appelle   │ │ appelle     │
│ GoogleSMS │ │ AmazonSMS   │
└───────────┘ └────────────┘
```

```java
class GoogleSMSAdapter implements SMSSender {
    private GoogleSMS googleSMS = new GoogleSMS();

    public void send(String msg, List<String> numbers) {
        googleSMS.sendSMSBulk(numbers, msg);  // adaptation !
    }
}

// Le code client ne change JAMAIS :
SMSSender sender = new GoogleSMSAdapter();  // ou AmazonSMSAdapter
sender.send("Hello", numbers);  // toujours la même API
```

> **🧑‍💻 SE Note** : Adapter = le couteau suisse de l'intégration. Chaque fois que vous intégrez une API externe, créez un Adapter pour isoler votre code du vendor lock-in.

---

## 4.4 🧑‍💻 Comment Choisir un Pattern ? / 如何选择设计模式？

| Problème | Pattern Recommandé |
|----------|-------------------|
| Une seule instance globale nécessaire | **Singleton** |
| Besoin de notifier plusieurs objets d'un changement | **Observer** |
| Structure arborescente (fichiers, menus, UI) | **Composite** |
| Deux APIs incompatibles à unifier | **Adapter** |
| Création d'objets complexes avec beaucoup de params | **Builder** |
| Ajouter des comportements dynamiquement | **Decorator** |
| Changer d'algorithme au runtime | **Strategy** |

---

## 4.5 TD Design Patterns — Solutions / 设计模式TD解答

> **Note** : Le TD "Les modèles de conception" contient principalement des QCM. Voici les réponses et explications.

### QCM — Réponses et Justifications

*(Les questions exactes dépendent du document TD; voici les concepts clés testés)*

| Concept Testé | Réponse Typique | Justification |
|---------------|-----------------|---------------|
| Pattern de création garantissant une seule instance | **Singleton** | Constructeur privé + getInstance() |
| Pattern pour notifier des changements d'état | **Observer** | Observable notifie ses Observers |
| Pattern pour structure arborescente | **Composite** | Interface commune, enfants récursifs |
| Pattern pour adapter des APIs incompatibles | **Adapter** | Wrapper qui traduit les appels |
| SOLID : une classe = une responsabilité | **S** (Single Responsibility) | Une raison de changer |
| SOLID : ouvert à l'extension, fermé à la modification | **O** (Open/Closed) | Héritage + polymorphisme |
| SOLID : sous-classe remplace classe parent | **L** (Liskov Substitution) | Contrat respecté |

---

> ✅ **Chapitre 4 terminé.** Vous connaissez maintenant SOLID, les 4 patterns clés du cours (Singleton, Observer, Composite, Adapter) et comment les choisir.

---

# 第5章 — TD 代码生成 / Génération de Code à partir d'UML

---

## 5.0 概述 / Aperçu

> **FR** : La génération de code est le processus de transformation automatique des modèles UML (principalement le diagramme de classe) en code source dans un langage cible (Java, C++, Python, PHP...).
> **ZH** : 代码生成是将UML模型（主要是类图）自动转换为目标语言（Java、C++、Python、PHP等）源代码的过程。

> **🧑‍💻 Perspective SE** : 代码生成 = **从设计到实现的最短路径**。现代IDE（如IntelliJ, VS Code）都支持从UML生成骨架代码，反过来也可以从代码反向生成UML（round-trip engineering）。

---

## 5.1 Règles de Mapping UML → Code / 映射规则

| Élément UML | Java | Python | C++ |
|-------------|------|--------|-----|
| Classe | `class Nom { }` | `class Nom:` | `class Nom { };` |
| Attribut privé `-` | `private Type nom;` | `self.__nom` | `private: Type nom;` |
| Attribut public `+` | `public Type nom;` | `self.nom` | `public: Type nom;` |
| Méthode `+ nom():Type` | `public Type nom() { }` | `def nom(self) -> Type:` | `public: Type nom() { }` |
| Généralisation | `class B extends A` | `class B(A):` | `class B : public A` |
| Association 1→1 | `private A a;` | `self.a: A` | `A* a;` |
| Association 1→* | `private List<A> as;` | `self.as: list[A] = []` | `vector<A*> as;` |
| Agrégation (◇) | `private List<A> as;` | `self.as: list[A] = []` | `vector<A*> as;` |
| Composition (◆) | Création dans constructeur | `self.as = [A()...]` | Objets créés dans constructeur |

---

## 5.2 Outil Umbrello — Workflow / 工作流

> **Umbrello** est un outil open-source de modélisation UML qui supporte la génération de code.

**Étape 1 — Sélection des classes :**
- Menu `Code > Assistant de génération de code`
- Choisir les classes à exporter (toutes par défaut)
- 选择要导出的类（默认全选）

**Étape 2 — Configuration des paramètres :**
- Langage cible : C++, Java, Python, PHP, Perl, Ruby, SQL, C#, etc.
- Dossier de sortie
- Options de formatage
- 配置参数：目标语言、输出文件夹、格式选项

**Étape 3 — Génération :**
- Lancement de la création des fichiers
- Chaque classe → un fichier `.java` / `.py` / `.cpp`
- Inclut : déclarations de classes, attributs, méthodes
- 生成：每个类→一个代码文件，包含类声明、属性、方法

---

## 5.3 Autres Outils Recommandés / 推荐工具

| Outil | Type | Avantage |
|-------|------|----------|
| **PlantUML** | Texte → Diagramme | Gratuit, intégré à VS Code/IntelliJ, versionnable (git) |
| **draw.io** | GUI | Gratuit, interface intuitive, export multiple |
| **Umbrello** | GUI + Génération | Open-source, génération de code intégrée |
| **Papyrus** | Eclipse Plugin | Outil du cours, support complet UML2 |
| **Visual Paradigm** | GUI Pro | Round-trip engineering, documentation automatique |

> **🧑‍💻 Recommandation SE** : Pour un workflow professionnel — **PlantUML** pour le versionnage + **draw.io** pour les présentations.

---

## 5.4 TD Génération de Code — Questions Types / 典型题目

### A) Analyse de Diagramme de Classe

**Questions typiques :**

| Question | Approche de Réponse |
|----------|-------------------|
| 1. Quel type d'application illustre ce diagramme ? | Identifier le domaine : e-commerce, gestion, médical, etc. |
| 2. Lister les classes représentées | Lire chaque boîte dans le diagramme |
| 3. Lister les différentes relations et leurs types | Pour chaque ligne : association/généralisation/agrégation/composition |
| 4. Expliquer la multiplicité utilisée | Pour chaque relation : justifier 1, 0..1, *, 1..* |
| 5. Expliquer la visibilité utilisée | `+` = public (accessible partout), `-` = privé (encapsulation), `#` = protégé (héritage) |

### B) Génération de Code avec Umbrello

**Processus en 3 étapes :**
1. **Sélection** : Choisir les classes à exporter (toutes par défaut)
2. **Configuration** : Définir le langage cible et le dossier de sortie
3. **Génération** : Lancer la création des fichiers de code

---

> ✅ **Chapitre 5 terminé.**

---

# 第6章 — TD 架构设计 / Conception Architecturale

---

## 6.0 概述 / Aperçu

> **FR** : L'architecture logicielle est la structure fondamentale d'un système — ses composants, leurs relations, et les principes qui guident leur conception et évolution.
> **ZH** : 软件架构是系统的基本结构——其组件、关系及指导设计和演化的原则。

> **🧑‍💻 Perspective SE** : L'architecture = les décisions **coûteuses à changer plus tard**. Choix du pattern architectural, distribution, communication, stockage. C'est ce qui sépare un senior d'un junior.

---

## 6.1 Architecture Classique vs Architecture Logicielle

**Similitudes / 相似之处 :**

| Architecture Classique / 经典建筑 | Architecture Logicielle / 软件架构 |
|---|---|
| Multiples vues (extérieur, plans, plomberie) | Multiples vues (contrôle, modules, données) |
| Styles (roman, gothique) | Styles (pipe-filter, OO, procédural) |
| Choix du style → conception physique | Choix du style → structure du code |
| Choix du style → matériaux | Choix du style → structures de données/contrôle |

**Différences / 差异 :**

| Architecture Classique | Architecture Logicielle |
|---|---|
| Architecture physique | Architecture conceptuelle |
| Statique | Dynamique |
| Peu d'évolution | Évolution fréquente |

---

## 6.2 Patrons Architecturaux / 架构模式

| Pattern | Description | Quand l'utiliser ? |
|---------|-------------|-------------------|
| **Client-Serveur** | Clients demandent, serveur fournit | Applications web, APIs, services |
| **Repository (Dépôt)** | Données centralisées, partagées par tous | Dropbox, CMS, data warehouses |
| **MVC** (Modèle-Vue-Contrôleur) | Séparation données / interface / logique | Applications web (Spring, Django, Rails) |
| **Layered (Couches)** | Présentation → Métier → Persistance | Applications d'entreprise |
| **Pipe-Filter** | Données traversent des filtres en séquence | Compilateurs, ETL, Unix pipes |
| **Microservices** | Services indépendants, communicants | Grands systèmes distribués |

---

## 6.3 TD Architecture — Solutions / 架构TD解答

---

### Question 1 : Parallèles Architecture Classique / Logicielle

*(Voir tableau 6.1 ci-dessus pour la réponse complète)*

**Points clés :**
- Les deux utilisent des **vues multiples**, des **styles**, et lient le style à la **conception**
- Différence majeure : l'architecture classique est **physique et statique**, l'architecture logicielle est **conceptuelle et dynamique**, avec une **évolution fréquente**

---

### Question 2 : Système de Vidéoconférence / 视频会议系统

> **Énoncé** : Système permettant à plusieurs participants de visualiser simultanément vidéo, audio et données.

**Réponse : Architecture Client-Serveur**

```
┌──────────┐    ┌──────────┐    ┌──────────┐
│ Client 1 │    │ Client 2 │    │ Client 3 │
│(vidéo,   │    │(vidéo,   │    │(vidéo,   │
│ audio,   │    │ audio,   │    │ audio,   │
│ données) │    │ données) │    │ données) │
└────┬─────┘    └────┬─────┘    └────┬─────┘
     │               │               │
     └───────────────┼───────────────┘
                     │
              ┌──────┴──────┐
              │   Serveur   │
              │ (media hub) │
              │ - streaming │
              │ - mixage    │
              │ - synchro   │
              └─────────────┘
```

**Justification :**
- Traitement important côté client pour gérer les données multimédias complexes
- Serveur central pour la synchronisation et le routage
- Communication bidirectionnelle temps réel

---

### Question 3 : Boutique en Ligne (Type Amazon) / 电商平台

> **Énoncé** : Large gamme de produits, millions d'opérations/jour, 500K+ vendeurs tiers.

**Réponse : Architecture Client-Serveur Distribuée**

**Justification :**
- ✓ Données stockées dans une base de données partagée
- ✓ Accessible simultanément par de nombreux clients répartis géographiquement
- ✓ Le système peut tirer parti de la **réplication** pour améliorer services et performances
- ✓ Load balancing, caching (CDN), microservices pour découpler les domaines (catalogue, commandes, paiements, vendeurs)

---

### Question 4 : Dropbox / 云存储

> **Énoncé** : Stockage cloud, synchronisation de fichiers, accessible via web et mobile.

**Réponse : Modèle de Dépôt (Repository Pattern)**

**Justification :**
- ✓ Volume important de données partagées entre utilisateurs
- ✓ Les modifications faites par un utilisateur sont visibles par tous les autres
- ✓ Gestion centralisée des données partagées (ex: sauvegardes simultanées)
- ✓ Les utilisateurs n'interagissent pas directement entre eux
- ✓ L'ajout ou la suppression d'utilisateurs n'affecte pas le système

```
┌──────────┐    ┌──────────┐    ┌──────────┐
│   User1  │    │   User2  │    │   UserN  │
└────┬─────┘    └────┬─────┘    └────┬─────┘
     │               │               │
     └───────────────┼───────────────┘
                     │
              ┌──────┴──────┐
              │  Dépôt      │
              │  Partagé    │
              │ (Dropbox)   │
              │ - fichiers  │
              │ - versions  │
              │ - synchro   │
              └─────────────┘
```

---

> ✅ **Chapitre 6 terminé.**

---

# 第7章 — 速查表与自测 / Fiches de Révision & Auto-Évaluation

---

## 7.1 Tableau Complet des Relations UML / UML关系完整表

| Relation | Symbole | Mot-Clé (FR) | 关键词 (ZH) | Sens Flèche |
|----------|---------|-------------|------------|-------------|
| `<<include>>` | ⇢ `<<include>>` | TOUJOURS | 总是 | → cas INCLUS |
| `<<extend>>` | ⇢ `<<extend>>` | OPTIONNEL | 可选 | → cas BASE |
| Généralisation UC | △ | Héritage de cas | 用例继承 | → cas GÉNÉRAL |
| Généralisation Classe | △ | « est-un » | 「是一个」 | → classe PARENT |
| Association | — | Lien simple | 简单连接 | (pas de flèche) |
| Dépendance | ⇢ | Usage temporaire | 临时使用 | → classe utilisée |
| Agrégation | ◇— | « a-un » FAIBLE | 弱拥有 | ◇ côté conteneur |
| Composition | ◆— | « partie-de » FORT | 强组成 | ◆ côté conteneur |

---

## 7.2 Multiplicité Rapide / 多重性速查

| Notation | Signification (FR) | 含义 (ZH) |
|----------|---------------------|-----------|
| `1` | Exactement un | 恰好一个 |
| `0..1` | Zéro ou un | 零或一个 |
| `*` ou `0..*` | Zéro ou plusieurs | 零或多个 |
| `1..*` | Au moins un | 至少一个 |

---

## 7.3 Design Patterns — Classification Rapide / 设计模式速查

| Catégorie | Patterns | But |
|-----------|----------|-----|
| **Création** | Singleton, Factory, Builder, Prototype, Abstract Factory | Créer des objets |
| **Structure** | Adapter, Composite, Decorator, Facade, Proxy | Organiser les classes |
| **Comportement** | Observer, Strategy, Command, State, Template Method | Gérer les interactions |

---

## 7.4 SOLID — 5 Principes en 5 Phrases

| L | Principe | En une phrase |
|---|----------|---------------|
| **S** | Single Responsibility | Une classe = un job |
| **O** | Open/Closed | Ajouter, ne pas modifier |
| **L** | Liskov Substitution | Le fils peut remplacer le père |
| **I** | Interface Segregation | Petites interfaces > grosses interfaces |
| **D** | Dependency Inversion | Dépendre d'interfaces, pas d'implémentations |

---

## 7.5 Checklist d'Auto-Évaluation / 自检清单

| # | Je sais... / 我能... | ✓ |
|---|---|---|
| 1 | Identifier les acteurs (principal vs secondaire) | ☐ |
| 2 | Distinguer `<<include>>` (toujours) vs `<<extend>>` (optionnel) | ☐ |
| 3 | Dessiner un diagramme de cas d'utilisation complet | ☐ |
| 4 | Écrire un scénario textuel (nominal + alternatif) | ☐ |
| 5 | Placer correctement les nœuds d'un diagramme d'activités | ☐ |
| 6 | Différencier Fork (diviser) et Join (synchroniser) | ☐ |
| 7 | Dessiner une classe avec attributs, méthodes et visibilité | ☐ |
| 8 | Lire et écrire la multiplicité (1, 0..1, *, 1..*) | ☐ |
| 9 | Distinguer les 5 relations entre classes | ☐ |
| 10 | Différencier Agrégation (◇) vs Composition (◆) | ☐ |
| 11 | Implémenter un Singleton en Java/Python | ☐ |
| 12 | Expliquer le pattern Observer avec un exemple concret | ☐ |
| 13 | Expliquer le pattern Adapter et son lien avec SOLID (OCP) | ☐ |
| 14 | Choisir le bon pattern architectural (Client-Serveur, Repository, MVC) | ☐ |
| 15 | Générer du code à partir d'un diagramme de classe UML | ☐ |

---

## 7.6 🧑‍💻 Outils Recommandés / 推荐工具

| Outil | Lien | Usage |
|-------|------|-------|
| **PlantUML** | plantuml.com | Diagrammes UML versionnables (texte → diagramme) |
| **draw.io** | app.diagrams.net | Interface graphique intuitive, tous types de diagrammes |
| **Umbrello** | umbrello.kde.org | Modélisation UML + génération de code |
| **Papyrus** | eclipse.org/papyrus | Plugin Eclipse, utilisé dans le cours |
| **Visual Paradigm** | visual-paradigm.com | Round-trip engineering professionnel |
| **Mermaid** | mermaid.js.org | Diagrammes dans Markdown, intégré GitHub |

---

## 7.7 Erreurs Fréquentes à l'Examen / 考试常见错误

| # | Erreur | Correction |
|---|--------|------------|
| 1 | Inverser `<<include>>` et `<<extend>>` | Include = TOUJOURS, Extend = OPTIONNEL |
| 2 | Inverser le sens des flèches Include/Extend | Include → cas INCLUS, Extend → cas BASE |
| 3 | Utiliser un NOM pour un cas d'utilisation | TOUJOURS un VERBE À L'INFINITIF |
| 4 | Confondre Agrégation et Composition | Si l'enfant meurt avec le parent → Composition |
| 5 | Mettre le client comme acteur du système de caisse | Le client n'agit PAS directement sur le système |
| 6 | Oublier la multiplicité sur les associations | Toujours vérifier : 1, 0..1, *, 1..* |
| 7 | Confondre Singleton et classe statique | Singleton PEUT implémenter une interface |
| 8 | Utiliser Fork sans Join correspondant | Fork et Join doivent être ÉQUILIBRÉS |

---

> 🎉 **Félicitations ! / 恭喜！**
>
> **FR** : Vous avez maintenant une compréhension complète de CM8 et CM9 — UML (Cas d'utilisation, Classe, Activités), Design Patterns, Génération de Code, et Architecture. Avec ce guide, vous pouvez aborder sereinement l'examen.
>
> **ZH** : 你现在已经完整掌握了CM8和CM9——UML（用例图、类图、活动图）、设计模式、代码生成和架构设计。有了这份指南，从容应对考试。
>
> **🧑‍💻** En tant qu'ingénieur logiciel, rappelez-vous : ces diagrammes ne sont pas juste pour l'examen — ce sont des **outils de communication** que vous utiliserez quotidiennement en entreprise.
>
> **BON COURAGE ! 加油！ 🍀**
