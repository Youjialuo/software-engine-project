# 软件工程复习文档 4：UML建模
# GÉNIE LOGICIEL — Document de Révision 4 : Modélisation UML

> CY Cergy Paris Université — Dr. Fatiha Bousbahi, Dr. Daniela Pamplona
> **中法双语完整复习 · Révision Bilingue Complète**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

### 4.0 Aperçu UML / UML概述

> **FR** : UML (Unified Modeling Language) est un langage graphique standardisé pour modéliser les systèmes logiciels. Il a été créé par Grady Booch, James Rumbaugh et Ivar Jacobson (les « trois amis ») dans les années 1990. UML 2.5 définit 14 types de diagrammes répartis en 3 catégories.

> **ZH** : UML（统一建模语言）是用于建模软件系统的标准化图形语言。由Grady Booch、James Rumbaugh和Ivar Jacobson（「三友」）于1990年代创建。UML 2.5定义了14种图，分为3大类。

| Catégorie (FR) / 大类 (ZH) | Type de Diagrammes | Usage Principal |
|---|---|---|
| **Diagrammes de Structure** / 结构图 | Classe, Objet, Composant, Déploiement, Paquetage | Modéliser l'organisation STATIQUE du système |
| **Diagrammes de Comportement** / 行为图 | Cas d'utilisation, Activités, États-transitions | Modéliser le comportement DYNAMIQUE |
| **Diagrammes d'Interaction** / 交互图 | Séquence, Communication, Temps, Vue d'ensemble | Modéliser les ÉCHANGES entre objets |

---

## A — DIAGRAMME DE CAS D'UTILISATION / 用例图

---

### 4.1 Éléments du Diagramme / 用例图元素

> **FR** : Le diagramme de cas d'utilisation répond à la question « QUI fait QUOI ? ». Il montre les acteurs (externes au système) et les fonctionnalités visibles (cas d'utilisation). C'est le diagramme le plus simple — on commence toujours par lui.

> **ZH** : 用例图回答「**谁**做**什么**？」的问题。它展示参与者（系统外部）和可见功能（用例）。这是最简单的图——总是从它开始。

| Élément (FR) / 元素 (ZH) | Notation | Définition (FR) | 定义 (ZH) |
|---|---|---|---|
| **Acteur** / 参与者 | Stick figure (火柴人) | Entité EXTERNE qui interagit avec le système. Représente un RÔLE, pas une personne spécifique. | 与系统交互的**外部**实体。代表一个**角色**，不是具体的人。 |
| **Acteur Principal** / 主要参与者 | — | Celui qui INITIE l'échange avec le système | **启动**与系统交互的一方 |
| **Acteur Secondaire** / 次要参与者 | — | Celui qui est SOLLICITÉ par le système (ex : système de paiement externe) | 被系统**调用**的一方（如：外部支付系统） |
| **Cas d'utilisation** / 用例 | Ellipse (椭圆) | Fonctionnalité visible de l'extérieur. Nommé par un VERBE À L'INFINITIF. | 外部可见的功能。用**动词不定式**命名。 |
| **Association** / 关联 | Ligne droite | Lien entre un acteur et un cas d'utilisation | 参与者与用例之间的连接 |
| **Frontière du système** / 系统边界 | Rectangle | Délimite ce qui fait partie du système | 框定系统的范围 |

---

### 4.2 Les Relations dans le Diagramme de Cas d'Utilisation / 用例图关系

> **FR** : Les relations sont la partie la plus technique du diagramme de cas d'utilisation. Il y a 3 types de relations entre cas d'utilisation ET 1 relation entre acteurs. La confusion entre `<<include>>` et `<<extend>>` est l'erreur la plus fréquente à l'examen.

> **ZH** : 关系是用例图中技术性最强的部分。用例之间有3种关系，参与者之间有1种关系。混淆 `<<include>>` 和 `<<extend>>` 是考试中最常见的错误。

#### Relations entre Cas d'Utilisation / 用例之间的关系

| Relation (FR) / 关系 (ZH) | Notation | Règle d'Or (FR) | 黄金法则 (ZH) | Sens de la Flèche |
|---|---|---|---|---|
| **`<<include>>`** / 包含 | Pointillés + `<<include>>` | Le cas A inclut **TOUJOURS** le cas B. B est OBLIGATOIRE pour A. | A **总是**包含B。B对A是**强制**的。 | A → B (vers le cas inclus) |
| **`<<extend>>`** / 扩展 | Pointillés + `<<extend>>` | Le cas B étend le cas A de façon **OPTIONNELLE**. B ne s'exécute que sous condition. | B**可选地**扩展A。B仅在特定条件下执行。 | B → A (vers le cas de base) |
| **Généralisation** / 泛化 | Flèche pleine → parent | Le cas spécialisé HÉRITE du cas général. Même principe que l'héritage en POO. | 特化用例**继承**通用用例。与面向对象继承原理相同。 | Spécialisé → Général |

#### Relation entre Acteurs / 参与者之间的关系

| Relation (FR) / 关系 (ZH) | Notation | Signification |
|---|---|---|
| **Généralisation** / 泛化 | Flèche pleine → parent | L'acteur spécialisé hérite de TOUS les cas d'utilisation de l'acteur général. Exemple : `Adhérent` hérite de `Internaute` — l'adhérent peut faire tout ce que fait l'internaute, PLUS ses propres cas. |

> **⚠️ Piège d'Examen / 考试陷阱** :
> - **FR** : `<<include>>` = flèche vers le cas INCLUS. `<<extend>>` = flèche vers le cas DE BASE. C'est CONTRE-INTUITIF — beaucoup d'étudiants inversent les flèches !
> - **ZH** : `<<include>>` = 箭头指向**被包含**的用例。`<<extend>>` = 箭头指向**基础**用例。这是**反直觉的**——很多学生会把箭头方向弄反！

**🧠 Moyen Mnémotechnique / 记忆方法** :
- **FR** : Include = « je vais CHERCHER ce dont j'ai besoin » → flèche vers ce qu'on inclut. Extend = « je me BRANCHE sur la base » → flèche vers la base.
- **ZH** : Include = 「我去**取**需要的东西」→ 箭头指向被包含的。Extend = 「我**挂接**到基础上」→ 箭头指向基础。

---

### 4.3 Rédaction de Scénarios / 场景编写

> **FR** : Un scénario décrit le déroulement DÉTAILLÉ d'un cas d'utilisation. Il existe deux types de flux : le flot nominal (tout se passe bien) et les flots alternatifs (exceptions, erreurs).

> **ZH** : 场景描述用例的**详细**执行过程。有两种流程：主流程（一切顺利）和替代流程（异常、错误）。

| Composant (FR) / 组成部分 (ZH) | Description |
|---|---|
| **Titre** / 标题 | Nom du cas d'utilisation |
| **Acteur principal** / 主要参与者 | Qui initie l'action |
| **Précondition** / 前置条件 | Ce qui doit être vrai AVANT le début |
| **Postcondition** / 后置条件 | Ce qui est vrai APRÈS la fin |
| **Scénario nominal** / 主流程 | Étapes numérotées du déroulement normal |
| **Scénarios alternatifs** / 替代流程 | Gestion des exceptions et erreurs |

---

### 4.4 Exemple : La Ludothèque / 案例：玩具图书馆

| Acteur (FR) / 参与者 (ZH) | Cas d'utilisation |
|---|---|
| **Internaute** / 网民 (visiteur non inscrit) | S'inscrire, Consulter le catalogue de jeux |
| **Adhérent** / 会员 (hérite d'Internaute) | Emprunter des jeux, S'inscrire à un événement, Payer sa cotisation |
| **Conseiller** / 顾问 (employé) | Gérer les emprunts, Organiser des événements |

**Relations notables** :
- `Adhérent` —Généralisation→ `Internaute` (l'adhérent peut tout faire comme un internaute)
- `Payer cotisation` —`<<include>>`→ `Vérifier statut adhérent` (toujours)
- `Consulter jeux` ←`<<extend>>`— `Réserver un jeu` (optionnel)

---

## B — DIAGRAMME D'ACTIVITÉS / 活动图

---

### 4.5 Éléments du Diagramme d'Activités / 活动图元素

> **FR** : Le diagramme d'activités modélise le FLUX de CONTRÔLE et de DONNÉES d'un processus. Il est utilisé pour décrire la logique d'un cas d'utilisation, un processus métier, ou le fonctionnement d'une opération complexe.

> **ZH** : 活动图建模过程的**控制流**和**数据流**。用于描述用例逻辑、业务流程或复杂操作的运作方式。

| Élément (FR) / 元素 (ZH) | Notation | Rôle |
|---|---|---|
| **Nœud initial** / 初始节点 | Cercle plein noir ⬤ | Point de départ UNIQUE |
| **Action** / 动作 | Rectangle arrondi | Une étape du processus |
| **Flot de contrôle** / 控制流 | Flèche → | Passage d'une action à l'autre |
| **Nœud de décision** / 决策节点 | Losange ◇ | Branchement conditionnel (1 entrée, N sorties) |
| **Nœud de fusion** / 合并节点 | Losange ◇ | Regroupe plusieurs branches alternatives |
| **Fork (分叉)** / 分叉 | Barre horizontale épaisse | 1 entrée → N sorties PARALLÈLES. Toutes les branches démarrent en même temps. |
| **Join (汇合)** / 汇合 | Barre horizontale épaisse | N entrées → 1 sortie. Attend la fin de TOUTES les branches parallèles. |
| **Nœud final d'activité** / 活动终止 | Cercle + point ◎ | Fin de TOUTE l'activité |
| **Nœud final de flot** / 流终止 | Cercle + X ⊗ | Fin d'UN flux (les autres continuent) |
| **Partition (Swimlane)** / 泳道/分区 | Couloir vertical | Regroupe les actions par ACTEUR ou par RESPONSABILITÉ |

> **⚠️ Fork vs Join** :
> - **FR** : Fork = DIVISER le travail en parallèle. Join = ATTENDRE que tout le travail parallèle soit terminé.
> - **ZH** : Fork = **拆分**工作到并行。Join = **等待**所有并行工作完成。

**Exemple Classique : Distributeur Automatique (ATM)** :
```
⬤ → Insérer carte → Vérifier code → ◇ Bon code? → [OUI] Choisir opération
                                     → [NON] Avaler carte → ◎
                       Choisir opération → Retrait → Délivrer billets → ◎
                                         → Dépôt  → Accepter enveloppe → ◎
```

---

## C — DIAGRAMME DE CLASSE / 类图

---

### 4.6 Structure d'une Classe / 类结构

> **FR** : Le diagramme de classe est le diagramme STRUCTUREL le plus important. Il montre les classes du système, leurs attributs, leurs méthodes, et les relations entre elles. Il correspond directement au code dans un langage orienté objet.

> **ZH** : 类图是最重要的**结构**图。它展示系统的类、属性、方法以及它们之间的关系。它直接对应面向对象语言中的代码。

```
┌──────────────────────┐
│   Nom de la Classe   │  ← Obligatoire
├──────────────────────┤
│   - attribut1: Type  │  ← Attributs (optionnel)
│   # attribut2: Type  │
│   + attribut3: Type  │
├──────────────────────┤
│   + méthode1(): Type │  ← Méthodes (optionnel)
│   - méthode2(): void │
└──────────────────────┘
```

#### Visibilité / 可见性

| Symbole | Nom (FR) | 名称 (ZH) | Accessible par... |
|---------|----------|-----------|-------------------|
| `+` | **Public** | 公有 | Toutes les classes / 所有类 |
| `-` | **Privé** | 私有 | La classe elle-même uniquement / 仅该类自身 |
| `#` | **Protégé** | 保护 | La classe + ses sous-classes (héritage) / 该类及其子类 |
| `~` | **Package** | 包 | Les classes du même package / 同包的类 |

---

### 4.7 Multiplicité / 多重性

> **FR** : La multiplicité indique COMBIEN d'objets participent à une relation. Elle se lit dans les DEUX sens.

> **ZH** : 多重性表示**多少**个对象参与关系。需要**双向**解读。

| Notation | Signification (FR) | 含义 (ZH) | Exemple |
|----------|---------------------|-----------|---------|
| `1` | Exactement un | 恰好一个 | Un client a exactement 1 compte principal |
| `0..1` | Zéro ou un | 零或一个 | Un employé a 0 ou 1 manager |
| `*` ou `0..*` | Zéro ou plusieurs | 零或多个 | Un client a 0 ou plusieurs commandes |
| `1..*` | Un ou plusieurs | 一个或多个 | Une commande contient 1 ou plusieurs articles |
| `n..m` | Entre n et m | n到m个 | Une équipe a 2..5 joueurs |

---

### 4.8 Les 5 Relations entre Classes / 类间五种关系

| Relation (FR) / 关系 (ZH) | Notation | Sémantique | Exemple |
|---|---|---|---|
| **Association** / 关联 | Ligne simple | Connexion sémantique entre deux classes | `Client` — `Compte` |
| **Généralisation** / 泛化 | Flèche pleine → parent | « est-un » (héritage). La sous-classe hérite de tout. | `CompteÉpargne` → `Compte` |
| **Dépendance** / 依赖 | Flèche pointillée → | Usage temporaire. Un changement dans A affecte B. | `Service` ..> `Repository` |
| **Agrégation** / 聚合 | ◇ losange VIDE + ligne | « a-un » FAIBLE. L'enfant PEUT exister sans le parent. | `Université` ◇— `Étudiant` |
| **Composition** / 组合 | ◆ losange PLEIN + ligne | « partie-de » FORT. L'enfant NE PEUT PAS exister sans le parent. | `Dossier` ◆— `Document` |

---

#### ⚠️ Agrégation vs Composition / 聚合 vs 组合

> **FR** : C'est la distinction la plus subtile — et la plus fréquemment testée — des relations entre classes.

> **ZH** : 这是类关系中最微妙——也是最常被考到——的区分。

| Critère | Agrégation (FR) / 聚合 (ZH) | Composition (FR) / 组合 (ZH) |
|---------|------------------------------|------------------------------|
| **Symbole** | Losange **VIDE** ◇ | Losange **PLEIN** ◆ |
| **Force du lien** | **FAIBLE** | **FORTE** |
| **Relation** | « a-un » / 拥有 (has-a) | « partie-de » / 组成部分 (part-of) |
| **Indépendance** | L'enfant **PEUT** exister sans le parent | L'enfant **NE PEUT PAS** exister sans le parent |
| **Destruction** | Détruire le parent NE détruit PAS l'enfant | Détruire le parent DÉTRUIT l'enfant |
| **Exemple concret** | `Playlist` ◇— `Chanson` (la chanson existe sans la playlist) | `Maison` ◆— `Pièce` (pas de pièce sans maison) |

**🧠 Test Rapide / 快速测试** : « Si je supprime le conteneur, le contenu survit-il ? » OUI → Agrégation / NON → Composition.

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Type 1 : Include vs Extend

| Énoncé (FR) / 题干 (ZH) | Relation |
|---|---|
| « Pour payer, il faut TOUJOURS vérifier le statut du compte » | `<<include>>` |
| « On peut recevoir une notification APRÈS un achat, si l'utilisateur le souhaite » | `<<extend>>` |
| « L'authentification est OBLIGATOIRE pour toute action » | `<<include>>` |

---

### Type 2 : Agrégation vs Composition

| Énoncé (FR) / 题干 (ZH) | Réponse |
|---|---|
| « Une bibliothèque contient des livres. Si la bibliothèque ferme, les livres sont transférés ailleurs. » | **Agrégation** (les livres survivent) |
| « Une facture contient des lignes. Sans la facture, les lignes n'ont pas de sens. » | **Composition** (les lignes sont détruites avec la facture) |

---

### Type 3 : Déterminer la Multiplicité

| Situation (FR) / 场景 (ZH) | Multiplicité |
|---|---|
| Un employé a exactement un supérieur hiérarchique | `1` |
| Un client peut passer 0, 1 ou plusieurs commandes | `0..*` ou `*` |
| Une commande doit contenir au moins un article | `1..*` |

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

### Tableau des Relations UML / UML关系速查

| Relation | Notation | Mot-clé (FR) | 关键词 (ZH) |
|----------|----------|-------------|------------|
| `<<include>>` | …→ inclus | TOUJOURS, OBLIGATOIRE | 总是、强制 |
| `<<extend>>` | …→ base | OPTIONNEL | 可选 |
| Généralisation | → parent | « est-un », héritage | 继承 |
| Agrégation | ◇— | « a-un », lien FAIBLE | 弱关联 |
| Composition | ◆— | « partie-de », lien FORT | 强关联 |

### Checklist d'Auto-Évaluation

| # | Je sais... | ✓ |
|---|---|---|
| 1 | Distinguer acteur principal vs secondaire | ☐ |
| 2 | Différencier `<<include>>` (toujours) vs `<<extend>>` (optionnel) | ☐ |
| 3 | Écrire un scénario nominal + alternatif | ☐ |
| 4 | Lister les éléments d'un diagramme d'activités (nœuds, fork, join...) | ☐ |
| 5 | Lire et écrire la multiplicité (1, 0..1, *, 1..*) | ☐ |
| 6 | Comprendre les symboles de visibilité (+, -, #) | ☐ |
| 7 | Distinguer Agrégation (◇ vide) vs Composition (◆ plein) | ☐ |
| 8 | Citer les 5 relations entre classes | ☐ |

---

> 📄 **Fin du Document 4** · Suite → [Document 5 : Design Patterns & Architecture](./05_DesignPatterns_Architecture.md)
