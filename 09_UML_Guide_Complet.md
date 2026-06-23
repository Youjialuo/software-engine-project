# UML 完全指南：从零开始绘制三大类图 + TD作业详解
# Guide UML Complet : Dessiner les 3 Diagrammes Pas à Pas + Solutions TD

> CY Cergy Paris Université
> **中法双语 · Débutant-Friendly · 零基础友好**

---

## 📌 前言 / Avant-Propos

> **FR** : Ce guide est conçu pour les DÉBUTANTS COMPLETS en UML. Nous allons apprendre à dessiner les trois diagrammes UML les plus importants — Cas d'Utilisation, Activités, et Classe — ÉTAPE PAR ÉTAPE. Chaque concept est expliqué en français ET en chinois. À la fin, nous résoudrons ensemble les exercices TD pour mettre en pratique.

> **ZH** : 本指南专为UML**零基础**学习者设计。我们将**一步一步**学习绘制三种最重要的UML图——用例图、活动图和类图。每个概念都有法语和中文双语解释。最后，我们将一起解答TD练习题来实践。

---

## 📋 Table des Matières / 目录

| # | Section | 章节 |
|---|---------|------|
| 1 | Diagramme de Cas d'Utilisation | 用例图 |
| 2 | Diagramme d'Activités | 活动图 |
| 3 | Diagramme de Classe | 类图 |
| 4 | Solutions TD Complètes | TD作业完整解答 |

---

## 1. DIAGRAMME DE CAS D'UTILISATION / 用例图

---

### 1.0 Qu'est-ce que c'est ? / 这是什么？

> **FR** : Le diagramme de cas d'utilisation répond à la question : **« QUI fait QUOI avec le système ? »** C'est le diagramme UML le plus SIMPLE — on commence TOUJOURS par lui pour comprendre les besoins des utilisateurs.

> **ZH** : 用例图回答的问题是：**「谁用系统做什么？」** 这是UML中最**简单**的图——我们**总是**从它开始来理解用户需求。

---

### 1.1 Le Matériel de Dessin / 绘图工具箱

> **FR** : Pour dessiner un diagramme de cas d'utilisation, vous avez besoin de 5 éléments. Apprenons-les un par un.

> **ZH** : 绘制用例图需要5个元素。让我们逐一学习。

---

#### Élément ① : L'Acteur / 参与者 (Acteur)

> **FR** : Un acteur est une **entité EXTERNE au système** qui interagit avec lui. Il représente un **RÔLE**, pas une personne spécifique. On le dessine comme un **stick figure** (bonhomme bâton).

> **ZH** : 参与者是与系统交互的**外部实体**。它代表一个**角色**，不是具体的人。用**火柴人**图标表示。

`
    o       ← tête / 头
   /|\      ← corps + bras / 身体+手臂
   / \      ← jambes / 腿

  Client    ← nom du rôle écrit en dessous / 角色名写在下方
`

**Types d'Acteurs / 参与者类型** :

| Type (FR) | 类型 (ZH) | Définition (FR) | 定义 (ZH) |
|-----------|-----------|-----------------|-----------|
| **Principal** | 主要参与者 | Celui qui **INITIE** l'interaction | **启动**交互的一方 |
| **Secondaire** | 次要参与者 | Celui qui est **SOLLICITÉ** par le système | 被系统**调用**的一方 |

> **🧠 Comment distinguer ? / 如何区分？**
> - **FR** : Posez la question : « Qui COMMENCE l'action ? » → Principal. « Qui est APPELÉ par le système ? » → Secondaire.
> - **ZH** : 问自己：「谁**开始**了动作？」→ 主要。「系统**调用**了谁？」→ 次要。

---

#### Élément ② : Le Cas d'Utilisation / 用例 (Use Case)

> **FR** : Un cas d'utilisation est une **fonctionnalité visible** du système. On le dessine comme une **ellipse** (ovale). Son nom est TOUJOURS un **VERBE À L'INFINITIF**.

> **ZH** : 用例是系统的一项**可见功能**。用**椭圆**表示。名称**必须**用**动词不定式**。

`
  ┌──────────────────┐
  │  S'authentifier  │   ← verbe à l'infinitif / 动词不定式
  └──────────────────┘
`

> **⚠️ Piège / 陷阱** :
> - **FR** : JAMAIS « Authentification » (NOM). TOUJOURS « S'authentifier » (VERBE).
> - **ZH** : **绝不要**写「认证」(名词)。**始终**写「进行认证」(动词)。

---

#### Élément ③ : L'Association / 关联

> **FR** : Un **trait simple** qui relie un acteur à son cas d'utilisation. Signifie : « Cet acteur PEUT exécuter ce cas. »

> **ZH** : 连接参与者与用例的**简单直线**。表示：「该参与者**可以**执行此用例。」

`
    o
   /|\  ────────────  ┌──────────────────┐
   / \                │  S'authentifier  │
  Client              └──────────────────┘
`

---

#### Élément ④ : La Frontière du Système / 系统边界

> **FR** : Un **rectangle** qui délimite le système. Les cas sont À L'INTÉRIEUR. Les acteurs sont À L'EXTÉRIEUR.

> **ZH** : 框定系统范围的**矩形**。用例在**里面**，参与者在**外面**。

`
 ┌──────────────────────────────────────┐
 │           SYSTÈME / 系统              │
 │                                      │
 │  ┌──────────────┐  ┌──────────────┐  │
 │  │S'authentifier│  │Consulter     │  │
 │  └──────────────┘  │compte        │  │
 │                    └──────────────┘  │
 └──────────────────────────────────────┘
`

---

#### Élément ⑤ : Les Relations entre Cas / 用例间关系

##### A) <<include>> / 包含 (Inclusion)

> **FR** : A **INCLUT TOUJOURS** B. B est **OBLIGATOIRE**. Flèche pointillée → vers le cas INCLUS.

> **ZH** : A **总是包含** B。B 是**强制**的。虚线箭头 → 指向被包含的用例。

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

##### B) <<extend>> / 扩展 (Extension)

> **FR** : B **ÉTEND** A de façon **OPTIONNELLE**. Flèche pointillée → vers le cas DE BASE.

> **ZH** : B **可选地扩展** A。虚线箭头 → 指向基础用例。

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

> **⚠️ Include vs Extend — La Différence CRUCIALE !**

| Critère | <<include>> | <<extend>> |
|---------|---------------|--------------|
| **Obligation (FR)** | **TOUJOURS** | **OPTIONNEL** |
| **Obligation (ZH)** | **总是** | **可选** |
| **Sens flèche (FR)** | A → B (inclus) | B → A (base) |
| **方向 (ZH)** | A → B (指向被包含) | B → A (指向基础) |

##### C) Généralisation / 泛化

> **FR** : Cas SPÉCIALISÉ hérite du cas GÉNÉRAL. Flèche **PLEINE** → vers le général.

> **ZH** : **特化**用例继承**通用**用例。**实心**箭头 → 指向通用。

`
 ┌──────────┐
 │ Paiement │  ← général
 └────┬─────┘
      △ (flèche pleine)
 ┌────┴─────────┐
 │Paiement carte│  ← spécialisé
 └──────────────┘
`

---

### 1.2 Méthode Complète en 6 Étapes / 六步完整画法

#### Étape 1 : Identifier les Acteurs / 识别参与者

> **FR** : Repérez TOUS les rôles. Pour chacun : Principal (il initie) ou Secondaire (il est sollicité) ?

> **ZH** : 找出**所有**角色。每个判断：主要（启动）还是次要（被调用）？

**Exemple — Système de Caisse / 收银系统** :
- Caissier → **Principal** (il initie l'enregistrement)
- Responsable → **Principal** (il initie l'initialisation)
- Centre d'autorisation → **Secondaire** (sollicité par la caisse)
- Client → **PAS un acteur !** (n'agit pas directement sur le système)

---

#### Étape 2 : Identifier les Cas d'Utilisation / 识别用例

> **FR** : Pour chaque acteur : « Qu'est-ce qu'il FAIT ? » → Chaque action = un cas (VERBE À L'INFINITIF).

> **ZH** : 对每个参与者：「他**做**什么？」→ 每个动作 = 一个用例（动词不定式）。

---

#### Étape 3 : Dessiner la Frontière / 画系统边界

> **FR** : Grand rectangle. Nom du système en haut.

> **ZH** : 大矩形。顶部写系统名称。

---

#### Étape 4 : Placer Acteurs et Cas / 放置参与者和用例

> **FR** : Acteurs DEHORS, cas DEDANS. Relier par des traits simples.

> **ZH** : 参与者放**外面**，用例放**里面**。简单直线连接。

---

#### Étape 5 : Ajouter les Relations / 添加关系

> **FR** : Include (toujours) / Extend (optionnel) / Généralisation (héritage).

> **ZH** : Include (总是) / Extend (可选) / 泛化 (继承)。

---

#### Étape 6 : Vérifier / 检查

- [ ] Acteurs à l'extérieur ? / 参与者在外部？
- [ ] Cas à l'intérieur ? / 用例在内部？
- [ ] Noms en VERBES ? / 名称是动词？
- [ ] Flèches dans le BON sens ? / 箭头方向正确？

---

### 1.3 Scénario Textuel / 文本场景

> **FR** : Pour chaque cas d'utilisation, on écrit un SCÉNARIO détaillé.

> **ZH** : 为每个用例写详细的**场景**。

| Composant | Description (FR) | 描述 (ZH) |
|-----------|-------------------|-----------|
| **Titre** | Nom du cas | 用例名称 |
| **Acteur principal** | Qui initie | 谁启动 |
| **Précondition** | Ce qui est vrai AVANT | 前置条件 |
| **Postcondition** | Ce qui est vrai APRÈS | 后置条件 |
| **Scénario nominal** | Étapes normales (numérotées) | 主流程（编号） |
| **Scénarios alternatifs** | Exceptions, erreurs | 替代流程 |

---

## 2. DIAGRAMME D'ACTIVITÉS / 活动图

---

### 2.0 Qu'est-ce que c'est ? / 这是什么？

> **FR** : Le diagramme d'activités modélise le **FLUX d'un processus** — comme un organigramme. Il répond à : **« Comment ça se déroule, étape par étape ? »**

> **ZH** : 活动图建模**过程的流程**——就像流程图。回答：「**一步步如何执行？**」

---

### 2.1 Les Éléments / 绘图元素

| Élément (FR) / 元素 (ZH) | Symbole | Rôle (FR) / 作用 (ZH) |
|---|---|---|
| **Nœud initial** / 初始节点 | ⬤ | Point de DÉPART unique / 唯一起点 |
| **Action** / 动作 | [Action] | Une ÉTAPE / 一个步骤 |
| **Flot** / 控制流 | → | Passage entre actions / 步骤间流转 |
| **Décision** / 决策节点 | ◇ | Branchement (1 entrée, N sorties) / 条件分支 |
| **Fusion** / 合并节点 | ◇ | Regrouper branches / 合并分支 |
| **Fork** / 分叉 | ═══ | Diviser en PARALLÈLE / 拆分为并行 |
| **Join** / 汇合 | ═══ | Synchroniser (attendre TOUT) / 同步等待全部 |
| **Fin activité** / 活动终止 | ◎ | Fin de TOUTE l'activité / 全部结束 |
| **Fin flot** / 流终止 | ⊗ | Fin d'UN flux parallèle / 一个并行流结束 |
| **Swimlane** / 泳道 | ┃ | Regrouper par acteur / 按参与者分组 |

---

### 2.2 Exemple Complet : ATM / 完整示例：取款机

`
                    ⬤
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
┌──────────┐      └────←────┘
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
`

---

## 3. DIAGRAMME DE CLASSE / 类图

---

### 3.0 Qu'est-ce que c'est ? / 这是什么？

> **FR** : Le diagramme de classe montre la STRUCTURE STATIQUE du système : classes, attributs, méthodes, et relations. Il correspond DIRECTEMENT au code orienté objet.

> **ZH** : 类图展示系统的**静态结构**：类、属性、方法及关系。它**直接**对应面向对象代码。

---

### 3.1 Structure d'une Classe / 类的结构

`
┌──────────────────────────┐
│     Nom de la Classe     │  ← Compartiment 1 : NOM (obligatoire)
│     类名                 │
├──────────────────────────┤
│ - attribut1 : Type       │  ← Compartiment 2 : ATTRIBUTS (optionnel)
│ # attribut2 : Type       │
│ + attribut3 : Type       │
├──────────────────────────┤
│ + méthode1() : Type      │  ← Compartiment 3 : MÉTHODES (optionnel)
│ - méthode2() : void      │
└──────────────────────────┘
`

---

### 3.2 Visibilité / 可见性符号

| Symbole | Nom (FR) / 名称 (ZH) | Accessible par... / 可被...访问 |
|---------|----------------------|-------------------------------|
| + | Public / 公有 | TOUTES les classes / 所有类 |
| - | Privé / 私有 | La classe elle-même UNIQUEMENT / 仅该类自身 |
| # | Protégé / 保护 | La classe + ses SOUS-CLASSES / 该类+子类 |

---

### 3.3 Multiplicité / 多重性

| Notation | Signification (FR) | 含义 (ZH) |
|----------|---------------------|-----------|
| 1 | Exactement UN | 恰好一个 |
|  ..1 | ZÉRO ou UN | 零或一个 |
| * ou  ..* | ZÉRO ou PLUSIEURS | 零或多个 |
| 1..* | UN ou PLUSIEURS | 一个或多个 |

---

### 3.4 Les 5 Relations entre Classes / 类间五种关系

| # | Relation (FR) / 关系 (ZH) | Symbole | Mot-Clé (FR) / 关键词 (ZH) |
|---|---------------------------|---------|---------------------------|
| 1 | **Association** / 关联 | Ligne simple | Connexion simple / 简单连接 |
| 2 | **Généralisation** / 泛化 | △ (flèche pleine → parent) | « est-un » / 「是一个」 |
| 3 | **Dépendance** / 依赖 | ⇢ (flèche pointillée) | Usage temporaire / 临时使用 |
| 4 | **Agrégation** / 聚合 | ◇— (losange VIDE) | « a-un » FAIBLE / 弱拥有 |
| 5 | **Composition** / 组合 | ◆— (losange PLEIN) | « partie-de » FORT / 强组成 |

---

#### ⚠️ Agrégation vs Composition — Tableau Détaillé

| Critère | Agrégation (FR/ ZH) | Composition (FR/ ZH) |
|---------|---------------------|----------------------|
| **Symbole** | ◇ losange **VIDE** | ◆ losange **PLEIN** |
| **Force** | **FAIBLE** / 弱 | **FORTE** / 强 |
| **Relation** | « a-un » / 拥有 | « partie-de » / 组成部分 |
| **Enfant sans parent** | **PEUT** exister / 可以独立 | **NE PEUT PAS** exister / 不能独立 |
| **Destruction parent** | N'affecte PAS l'enfant | DÉTRUIT l'enfant |
| **Exemple (FR)** | Université ◇— Étudiant | Maison ◆— Pièce |
| **示例 (ZH)** | 大学◇—学生 | 房子◆—房间 |

> **🧠 Test Rapide / 快速测试** : « Si je supprime le conteneur, le contenu survit-il ? »
> OUI → Agrégation (◇) | NON → Composition (◆)

---

### 3.5 Méthode Complète en 7 Étapes / 七步画法

| Étape | Action (FR) | 动作 (ZH) |
|-------|-------------|-----------|
| 1 | Identifier les NOMS importants → classes candidates | 找重要名词 → 候选类 |
| 2 | Trouver les informations stockées → attributs | 找存储信息 → 属性 |
| 3 | Trouver les actions possibles → méthodes | 找可执行动作 → 方法 |
| 4 | Dessiner les rectangles à 3 compartiments | 画三隔间矩形 |
| 5 | Relier les classes (quel type de relation ?) | 连接类（什么关系类型？） |
| 6 | Ajouter la multiplicité (combien ?) | 添加多重性（多少？） |
| 7 | Vérifier : tout l'énoncé est-il représenté ? | 检查：题目所有信息都表达了吗？ |

---

## 4. SOLUTIONS TD COMPLÈTES / TD作业完整解答

---

### 4.1 TD Cas d'Utilisation : Station-Service / 用例图TD

**Exercice 1 — Identifier les Acteurs** :

| Question (FR) / 问题 (ZH) | Réponse / 答案 | Raison / 理由 |
|---|---|---|
| Le client, la gâchette ou le pistolet ? | **Le client** | La gâchette et le pistolet sont des OBJETS |
| Le pompiste qui se sert de l'essence ? | **Non** (même rôle : Client) | Même rôle = même acteur |
| Le gérant pour la gestion ? | **Oui** (nouveau rôle : Gérant) | Rôle DIFFÉRENT = nouvel acteur |

> **🔑 Leçon** : Un acteur = un RÔLE, pas une personne. / 参与者=角色，不是人。

---

**Exercice 2 — Système de Caisse / 收银系统**

**① Acteurs / 参与者** :

| Acteur | Type | Justification (FR) / 理由 (ZH) |
|--------|------|-------------------------------|
| Caissier | Principal | Il INITIE l'enregistrement / 启动登记 |
| Responsable | Principal | Il INITIE l'initialisation / 启动初始化 |
| Centre d'autorisation | Secondaire | SOLLICITÉ pour valider / 被调用验证 |
| Gestion de stocks | Secondaire | SOLLICITÉ après vente / 销售后被调用 |

> **⚠️ Le Client N'EST PAS un acteur** — il n'agit pas directement sur la caisse.
> **客户不是参与者**——他不直接操作收银系统。

**② Cas d'Utilisation et Relations** :

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
                 │           │ Généralisation│coupons        ││
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
                 │                                             │
       o         │  ┌──────────────────┐                      │
      /|\────────┼─→│Transmettre infos │←── Gestion stocks    │
      / \        │  │au stock          │                      │
    Caissier     │  └──────────────────┘                      │
                 │                                             │
       o         │  ┌──────────────────┐                      │
      /|\────────┼─→│Initialiser       │                      │
      / \        │  │caisses           │                      │
  Responsable    │  └──────────────────┘                      │
                 └─────────────────────────────────────────────┘
`

**③ Relations expliquées / 关系说明** :

| Cas A | Relation | Cas B | Pourquoi ? / 为什么？ |
|-------|----------|-------|----------------------|
| Signaler fin vente | <<include>> → | Paiement | TOUJOURS obligatoire / 总是强制 |
| Signaler fin vente | ← <<extend>> | Appliquer coupons | OPTIONNEL / 可选 |
| Paiement | ← Généralisation | Paiement liquide/chèque/carte | « est-un » type de paiement |

---

### 4.2 TD Activités : Distributeur de Billets / 活动图TD

> **FR** : Le client insère sa carte → vérification → saisie code (3 tentatives max, sinon avalée) → saisie montant → vérification solde → restitution carte + billets + reçu.

> **ZH** : 客户插卡 → 验证 → 输密码(最多3次，否则吞卡) → 输金额 → 查余额 → 退卡+出钞+收据。

**Diagramme Complet / 完整图** :

`
                    ⬤
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
                   ◇  Valide ?
                   │\
              [OUI]/  \[NON]
                  /    \
                 ↓      ◎
          ┌───────────┐
          │Saisir code│
          └─────┬─────┘
                │
                ↓
               ◇  Code OK ?
               │\
              /  \
        [OUI]/    \[NON]
            /      \
           ↓        ↓
    ┌───────────┐  ◇ 3e tentative ?
    │Saisir     │  │\
    │montant    │ /  \
    └─────┬─────┘[OUI][NON]
          │       ↓    │
          ↓   ┌──────┐ │
         ◇    │Avaler│ │
     Solde OK?│carte │ │
        │\    └──┬───┘ │
       /  \      │     │
 [OUI]/    \[NON]↓     │
     /      \   ◎     │
    ↓        ↓        │
┌───────┐┌────────┐   │
│Restit.││"Solde  │   │
│carte  ││insuff."│   │
└───┬───┘└───┬────┘   │
    │        │        │
    ↓        └────←───┘
┌───────┐
│Délivrer│
│billets │
└───┬───┘
    │
    ↓
┌───────┐
│Imprimer│
│reçu    │
└───┬───┘
    │
    ↓
    ◎
`

---

### 4.3 TD Classe : Relations et Multiplicité / 类图TD

**Exercice 1 — Identifier le Type de Relation** :

| Énoncé (FR) / 题目 (ZH) | Relation |
|---|---|
| « Une transaction boursière est un achat ou une vente » | **Généralisation** (« est-un ») |
| « Une personne utilise un langage de programmation » | **Association** (lien simple) |
| « Les modems et claviers sont des périphériques E/S » | **Généralisation** (« sont des ») |

**Exercice 2 — Classe Personne** :

`
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
`

**Exercice 3 — Multiplicité Magasin/Articles** :

`
Q1: Magasin ─────── Article     (1 magasin vend 1..* articles)
          1     1..*

Q2: Magasin ─────── Article     (articles vendus par +sieurs magasins)
         1..*   1..*

Q3: Magasin ─────── Article     (article peut n'être proposé nulle part)
         1..*   0..*
`

**Exercice 4 — Type de Relation** :

| Énoncé | Relation | Diagramme |
|--------|----------|-----------|
| « Un répertoire contient des fichiers » | **Composition** ◆ | Répertoire ◆— Fichier |
| « Une pièce se compose de murs » | **Composition** ◆ | Pièce ◆— Mur |
| « Modems et claviers sont des périphériques » | **Généralisation** | Modem → Périphérique |

---

## 📋 FORMULAIRE RAPIDE / 公式速查

### Tableau Complet des Relations UML / UML关系完整表

| Relation | Symbole | Mot-Clé (FR) | 关键词 (ZH) | Sens Flèche |
|----------|---------|-------------|------------|-------------|
| <<include>> | ⇢ <<include>> | TOUJOURS | 总是 | → cas INCLUS |
| <<extend>> | ⇢ <<extend>> | OPTIONNEL | 可选 | → cas BASE |
| Généralisation UC | △ | Héritage de cas | 用例继承 | → cas GÉNÉRAL |
| Généralisation Classe | △ | « est-un » | 「是一个」 | → classe PARENT |
| Association | — | Lien simple | 简单连接 | (pas de flèche) |
| Dépendance | ⇢ | Usage temporaire | 临时使用 | → classe utilisée |
| Agrégation | ◇— | « a-un » FAIBLE | 弱拥有 | ◇ côté conteneur |
| Composition | ◆— | « partie-de » FORT | 强组成 | ◆ côté conteneur |

---

### Multiplicité Rapide / 多重性速查

| Notation | Signification |
|----------|---------------|
| 1 | Exactement un / 恰好一个 |
|  ..1 | Zéro ou un / 零或一个 |
| * | Zéro ou plusieurs / 零或多个 |
| 1..* | Au moins un / 至少一个 |

---

### Checklist d'Auto-Évaluation / 自检清单

| # | Je sais... / 我能... | ✓ |
|---|---|---|
| 1 | Identifier les acteurs (principal vs secondaire) | ☐ |
| 2 | Distinguer <<include>> (toujours) vs <<extend>> (optionnel) | ☐ |
| 3 | Dessiner un diagramme de cas d'utilisation complet | ☐ |
| 4 | Écrire un scénario textuel (nominal + alternatif) | ☐ |
| 5 | Placer correctement les nœuds d'un diagramme d'activités | ☐ |
| 6 | Différencier Fork (diviser) et Join (synchroniser) | ☐ |
| 7 | Dessiner une classe avec attributs, méthodes et visibilité | ☐ |
| 8 | Lire et écrire la multiplicité (1, 0..1, *, 1..*) | ☐ |
| 9 | Distinguer les 5 relations entre classes | ☐ |
| 10 | Différencier Agrégation (◇) vs Composition (◆) | ☐ |

---

> 🎉 **Félicitations ! / 恭喜！**
> **FR** : Vous avez maintenant une compréhension complète des trois diagrammes UML. Avec ce guide, vous pouvez aborder sereinement n'importe quel exercice ou examen.
> **ZH** : 你现在已经完整掌握了三种UML图。有了这份指南，从容应对任何练习或考试。
>
> **BON COURAGE ! 加油！ 🍀**