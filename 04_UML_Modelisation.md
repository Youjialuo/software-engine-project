# 软件工程复习文档 4：UML建模

> **GÉNIE LOGICIEL — Document de Révision 4 : Modélisation UML**
> CY Cergy Paris Université — Dr. Fatiha Bousbahi, Dr. Daniela Pamplona
> 中法双语完整复习

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

### 4.0 UML 概述 / Aperçu UML

**UML** = Unified Modeling Language / 统一建模语言

| Catégorie / 大类 | 中文 | Diagrammes / 图类型 |
|---|---|---|
| **Structurels** | 结构图 | Classe, Objet, Composant, Déploiement |
| **Comportementaux** | 行为图 | Cas d'utilisation, Activités, États-transitions |
| **Interaction** | 交互图 | Séquence, Communication, Temps |

---

## 第一部分A：用例图 / Diagramme de Cas d'Utilisation

---

### 4.1 用例图核心元素 / Éléments Essentiels

| Élément | 中文 | Description | Notation |
|---------|------|-------------|----------|
| **Acteur** | 参与者 | Entité externe qui interagit avec le système | Stick figure (火柴人) |
| **Cas d'utilisation** | 用例 | Fonctionnalité visible de l'extérieur | Ellipse (椭圆) |
| **Association** | 关联 | Lien acteur ↔ cas d'utilisation | Ligne droite |
| **Frontière du système** | 系统边界 | Cadre qui délimite le système | Rectangle |
| **Description textuelle** | 文本描述 | Scénarios, pré/post conditions | Texte |

#### 参与者类型 / Types d'Acteurs

| Type | 中文 | Rôle |
|------|------|------|
| **Principal** | 主要参与者 | **Initie** l'échange avec le système / 启动与系统的交互 |
| **Secondaire** | 次要参与者 | **Sollicité** par le système / 被系统调用 |

> **🔑 关键点** : Un acteur représente un **RÔLE**, pas une personne spécifique. Une même entité peut avoir plusieurs rôles.
> 参与者代表一个**角色**，不是具体的人。同一实体可以有多个角色。

---

### 4.2 用例图关系 / Relations

#### A) 参与者之间的关系

| Relation | 中文 | Notation | Signification |
|----------|------|----------|---------------|
| **Généralisation** | 泛化 | Flèche pleine → parent | Acteur spécialisé hérite du général |

#### B) 用例之间的关系

| Relation | 中文 | Notation | Quand ? | Sens flèche |
|----------|------|----------|---------|-------------|
| **`<<include>>`** | 包含 | Flèche pointillée + `<<include>>` | A inclut **TOUJOURS** B | A → B (vers le cas inclus) |
| **`<<extend>>`** | 扩展 | Flèche pointillée + `<<extend>>` | B étend A (OPTIONNEL) | B → A (vers le cas de base) |
| **Généralisation** | 泛化 | Flèche pleine → général | Cas spécialisé hérite du général | Spécialisé → Général |

> **⚠️ 考试陷阱 / Piège d'examen** :
> - `<<include>>` → **TOUJOURS** exécuté, flèche vers le cas **INCLUS**
> - `<<extend>>` → **OPTIONNEL**, flèche vers le cas **DE BASE**

---

### 4.3 场景编写 / Rédaction de Scénarios

**Scénario** = Séquence particulière de messages dans un cas d'utilisation
场景 = 用例中的特定消息序列

| Type de scénario | 中文 | Description |
|---|---|---|
| **Flot nominal** | 主流程 | Déroulement normal, sans erreur |
| **Flot alternatif** | 替代流程 | Exceptions, erreurs, cas particuliers |

**结构 d'un scénario / 场景结构**：
1. **Titre** / 标题
2. **Acteur principal** / 主要参与者
3. **Précondition** / 前置条件
4. **Postcondition** / 后置条件
5. **Scénario nominal** (étapes numérotées) / 主流程（编号步骤）
6. **Scénarios alternatifs** (numérotés avec référence) / 替代流程

---

### 4.4 案例 / Exemple : La Ludothèque (玩具图书馆)

| Acteur | 中文 | Cas d'utilisation |
|--------|------|-------------------|
| **Internaute** | 网民 | S'inscrire, Consulter jeux |
| **Adhérent** (hérite d'Internaute) | 会员 | Emprunter jeux, S'inscrire événement, Payer cotisation |
| **Conseiller** | 顾问 | Gérer emprunts, Organiser événement |

**Relations clés / 关键关系**：
- `Adhérent` → Généralisation → `Internaute` (l'adhérent est aussi un internaute)
- `Payer cotisation` → `<<include>>` → `Vérifier statut adhérent`
- `Consulter jeux` → `<<extend>>` → `Réserver jeu` (optionnel)

---

## 第一部分B：活动图 / Diagramme d'Activités

---

### 4.5 活动图元素 / Éléments du Diagramme

| Élément | 中文 | Notation | Rôle |
|---------|------|----------|------|
| **Nœud initial** | 初始节点 | Cercle plein noir ⬤ | Point de départ |
| **Action** | 动作 | Rectangle arrondi | Une étape du processus |
| **Flot de contrôle** | 控制流 | Flèche → | Passage d'une action à l'autre |
| **Nœud de décision** | 决策节点 | Losange ◇ | Branchement conditionnel |
| **Nœud de fusion** | 合并节点 | Losange ◇ | Fusion de plusieurs branches |
| **Fork (分叉)** | 分叉 | Barre horizontale épaisse | Une entrée → plusieurs sorties parallèles |
| **Join (汇合)** | 汇合 | Barre horizontale épaisse | Plusieurs entrées → une sortie (synchronisation) |
| **Nœud final d'activité** | 活动终止 | Cercle + point ◎ | Fin de toute l'activité |
| **Nœud final de flot** | 流终止 | Cercle + X ⊗ | Fin d'un flux parallèle |
| **Partition (Swimlane)** | 泳道/分区 | Couloir vertical | Regroupe les actions par acteur |

> **🔑 Fork vs Join** :
> - **Fork** : 1 entrée → N sorties parallèles
> - **Join** : N entrées → 1 sortie (attend TOUTES les entrées)

---

### 4.6 活动图经典示例 / Exemple Classique : ATM

```
⬤ (Début)
  ↓
[Insérer carte]
  ↓
  ◇ Vérifier code
  ├── Code OK → [Choisir opération]
  │                ├── Retrait → [Délivrer billets]
  │                └── Dépôt → [Accepter enveloppe]
  └── Code faux (×3) → [Avaler carte]
                            ↓
                           ◎ (Fin)
```

---

## 第一部分C：类图 / Diagramme de Classe

---

### 4.7 类图核心元素 / Éléments Essentiels

**Structure d'une classe / 类结构**：

```
┌──────────────────┐
│  Nom de la Classe │  ← 类名
├──────────────────┤
│  - attribut1     │  ← 属性 (Attributs)
│  + attribut2     │
├──────────────────┤
│  + méthode1()    │  ← 方法 (Méthodes)
│  - méthode2()    │
└──────────────────┘
```

#### 可见性 / Visibilité

| Symbole | Nom | 中文 | Accessible par |
|---------|------|------|----------------|
| `+` | Public | 公有 | Toutes les classes |
| `-` | Privé | 私有 | La classe elle-même seulement |
| `#` | Protégé | 保护 | La classe + ses classes dérivées |

---

### 4.8 多重性 / Multiplicité

| Notation | Signification | 中文 |
|----------|---------------|------|
| `1` | Exactement un | 恰好一个 |
| `0..1` | Zéro ou un | 零或一个 |
| `0..*` ou `*` | Plusieurs (zéro ou plus) | 多个（零或多） |
| `1..*` | Un ou plusieurs | 一个或多个 |
| `n..m` | Entre n et m | n到m个 |

---

### 4.9 五种关系 / Les 5 Relations entre Classes

| Relation | 中文 | Notation | Signification | Exemple |
|----------|------|----------|---------------|---------|
| **Association** | 关联 | Ligne simple | Deux classes sont connectées | `Banque — Compte` |
| **Généralisation** | 泛化 | Flèche pleine → parent | « est-un » (héritage) | `CompteÉpargne → Compte` |
| **Dépendance** | 依赖 | Flèche pointillée → | Changement dans A affecte B | Utilisation temporaire |
| **Agrégation** | 聚合 | Ligne + losange vide ◇ | « a-un » (faible) ; l'enfant peut exister seul | `Équipe ◇— Docteur` |
| **Composition** | 组合 | Ligne + losange plein ◆ | « partie-de » (fort) ; l'enfant NE PEUT PAS exister seul | `Dossier ◆— Document` |

> **⚠️ 考试重点 / Agrégation vs Composition**：
>
> | Critère | Agrégation (聚合) | Composition (组合) |
> |---------|-------------------|---------------------|
> | Type de relation | « a un » / 拥有 | « partie de » / 组成部分 |
> | Force | **Faible** / 弱关联 | **Forte** / 强关联 |
> | Indépendance | L'enfant **PEUT** exister seul | L'enfant **NE PEUT PAS** exister seul |
> | Symbole | Losange **vide** ◇ | Losange **plein** ◆ |
> | Exemple | Université ◇— Étudiant (l'étudiant existe sans l'université) | Maison ◆— Pièce (la pièce n'existe pas sans la maison) |

---

### 4.10 UML 综合案例 / Étude de Cas Complète

**Système d'enseignement en ligne / 在线教学系统**：

| Exigence / 需求 | Diagramme / 图类型 |
|---|---|
| Acteurs + fonctionnalités | Cas d'utilisation |
| Flux d'une opération | Activités |
| Structure des données | Classe |

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### 题型一：识别 Include vs Extend

| Énoncé | Relation | Raison |
|--------|----------|--------|
| « Pour payer, il faut TOUJOURS vérifier le statut » | `<<include>>` | Obligatoire |
| « On peut réserver un jeu EN OPTION après consultation » | `<<extend>>` | Optionnel |
| « L'authentification est requise pour toute action » | `<<include>>` | Toujours exécuté |
| « L'utilisateur peut recevoir une notification après achat » | `<<extend>>` | Optionnel |

**🎯 判断方法** :
1. Poser la question : « Est-ce TOUJOURS exécuté ? »
2. OUI → `<<include>>` | NON → `<<extend>>`
3. `<<include>>` = flèche vers le cas INCLUS
4. `<<extend>>` = flèche vers le cas DE BASE

---

### 题型二：多重性判断 / Déterminer la Multiplicité

| Situation | Multiplicité |
|-----------|-------------|
| Un client a exactement un compte | `1` |
| Un client peut avoir 0 ou plusieurs comptes | `0..*` ou `*` |
| Un client doit avoir au moins un compte | `1..*` |
| Un employé a 0 ou 1 manager | `0..1` |
| Une commande contient 1 à 10 articles | `1..10` |

---

### 题型三：聚合 vs 组合判断

| Énoncé | Réponse |
|--------|---------|
| Une playlist contient des chansons. Si on supprime la playlist, les chansons restent. | **Agrégation** (faible) |
| Un bâtiment contient des pièces. Sans le bâtiment, les pièces n'existent pas. | **Composition** (forte) |
| Une équipe a des joueurs. Sans l'équipe, les joueurs existent toujours. | **Agrégation** (faible) |

**🎯 判断口诀**：
- « Si je supprime le contenant, le contenu survit-il ? »
- OUI → Agrégation (◇ vide) | NON → Composition (◆ plein)

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### UML 速查卡 / Carte de Référence UML

| Diagramme | 中文 | Catégorie | Usage principal |
|-----------|------|-----------|-----------------|
| Cas d'utilisation | 用例图 | Comportement | Qui fait quoi ? |
| Activités | 活动图 | Comportement | Comment ça se déroule ? |
| Classe | 类图 | Structure | Quelles sont les données ? |

### 关系速查 / Référence Relations

| Relation UML | Notation | Mots-clés |
|---|---|---|
| Include | `<<include>>` → inclus | TOUJOURS, OBLIGATOIRE |
| Extend | `<<extend>>` → base | OPTIONNEL, POINT D'EXTENSION |
| Généralisation (acteur) | Flèche pleine → parent | Héritage de rôle |
| Généralisation (classe) | Flèche pleine → parent | « est-un » |
| Agrégation | ◇— | « a-un », enfant indépendant |
| Composition | ◆— | « partie-de », enfant dépendant |

---

### 自检清单 / Points de Contrôle

- [ ] Identifier acteur principal vs secondaire dans un cas d'utilisation
- [ ] Distinguer `<<include>>` (obligatoire) vs `<<extend>>` (optionnel)
- [ ] Écrire un scénario avec flot nominal + alternatif
- [ ] Lister les éléments d'un diagramme d'activités
- [ ] Expliquer Fork vs Join
- [ ] Décrire la structure d'une classe (nom/attributs/méthodes)
- [ ] Interpréter les symboles de visibilité (`+`, `-`, `#`)
- [ ] Lire et écrire la multiplicité (`1`, `0..1`, `*`, `1..*`)
- [ ] Distinguer les 5 relations (Association, Généralisation, Dépendance, Agrégation, Composition)
- [ ] Différencier Agrégation (◇ vide, faible) vs Composition (◆ plein, forte)

---

> 📄 **Fin du Document 4** · Suite → [Document 5 : Design Patterns & Architecture](./05_DesignPatterns_Architecture.md)
