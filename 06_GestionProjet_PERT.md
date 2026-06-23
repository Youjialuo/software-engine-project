# 软件工程复习文档 6：项目管理与PERT/甘特图

> **GÉNIE LOGICIEL — Document de Révision 6 : Gestion de Projet, PERT & Gantt**
> CY Cergy Paris Université — Dr. Daniela Pamplona
> 中法双语完整复习 · ⚠️ **计算题重点章节**

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

### 6.1 为什么需要项目管理？/ Pourquoi la Gestion de Projet ?

> « Une bonne gestion ne peut pas garantir le succès, mais une mauvaise gestion conduit généralement à l'échec. »
> 「好的管理不能保证成功，但差的管理通常导致失败。」

**项目经理角色 / Rôle du chef de projet** :
Veiller à respecter les contraintes (预算/时间/范围) tout en livrant un logiciel de haute qualité.

---

### 6.2 项目管理5阶段 / Les 5 Phases

| # | Phase | 中文 | Activités clés |
|---|-------|------|----------------|
| ① | **Étude de faisabilité** | 可行性研究 | Vérifier si le projet est réalisable |
| ② | **Planification** | 规划 | Écriture d'un plan de projet |
| ③ | **Exécution** | 执行 | Réalisation des livrables, délégation des tâches |
| ④ | **Surveillance et contrôle** | 监控 | Temps, coûts, portée, qualité, risques |
| ⑤ | **Clôture** | 收尾 | Travail terminé, approuvé, transmis. Leçons apprises |

> **🧠 口诀**: « Fais Pla Exé Sur Clô » / 「可规执监收」

---

### 6.3 SMART 目标

| Lettre | Signification | 中文 |
|--------|---------------|------|
| **S** | Spécifique | 具体的 |
| **M** | Mesurable | 可衡量的 |
| **A** | Atteignable (Achievable) | 可实现的 |
| **R** | Pertinent (Relevant) | 相关的 |
| **T** | Temporellement défini (Time-bound) | 有时限的 |

---

### 6.4 项目计划6章结构 / Structure du Plan de Projet

| Chapitre | 中文 | Contenu |
|----------|------|---------|
| ① Introduction | 引言 | Objectifs SMART + résumé exécutif |
| ② Organisation | 组织 | Équipe, personnes, rôles |
| ③ Analyse des risques | 风险分析 | Types de risques, matrice des risques |
| ④ Ressources | 资源 | Matérielles, logicielles, humaines |
| ⑤ Activités, livrables, calendrier | 活动/交付物/日程 | Planning détaillé |
| ⑥ Évaluation | 评估 | Indicateurs de réussite |

---

### 6.5 8种风险类型 / Les 8 Types de Risques

| # | Risque | 中文 |
|---|--------|------|
| 1 | Commerciaux | 商业风险 |
| 2 | Financiers | 财务风险 |
| 3 | Techniques | 技术风险 |
| 4 | Développement | 开发风险 |
| 5 | Calendrier | 进度风险 |
| 6 | Bogues et erreurs | 缺陷与错误 |
| 7 | Exigences mal comprises | 需求理解错误 |
| 8 | Changement fréquent des exigences | 需求频繁变更 |

**Matrice des risques / 风险矩阵** = Probabilité × Impact / 概率 × 影响

---

### 6.6 项目管理工具 / Outils de Gestion

| Outil | Sigle | 中文 | Usage |
|-------|------|------|-------|
| **Organigramme de produit** | PBS | 产品分解结构 | Décomposer le produit |
| **Organigramme des tâches** | WBS | 任务分解结构 | Décomposer le travail |
| **Organigramme de l'organisation** | OBS | 组织分解结构 | Structurer l'équipe |

---

### 6.7 ⚠️ PERT 图核心计算 / Calculs PERT

---

#### 6.7.1 定义速查 / Définitions

| Abréviation | Nom complet | 中文 | Formule |
|-------------|-------------|------|---------|
| **DTO (ES)** | Début au plus tôt / Earliest Start | 最早开始时间 | DTO(N) = MAX(FTO(prédécesseurs)) |
| **FTO (EF)** | Fin au plus tôt / Earliest Finish | 最早完成时间 | **FTO = DTO + Durée** |
| **DTA (LS)** | Début au plus tard / Latest Start | 最晚开始时间 | DTA = FTA − Durée |
| **FTA (LF)** | Fin au plus tard / Latest Finish | 最晚完成时间 | FTA(N) = MIN(DTA(successeurs)) |
| **MT** | Marge totale / Total Float | 总浮动 | **MT = DTA − DTO = FTA − FTO** |
| **ML** | Marge libre / Free Float | 自由浮动 | Délai sans impacter les tâches suivantes |

> **🔑 关键公式** : FTO = DTO + D ; MT = DTA − DTO ; Chemin critique = MT = 0

---

#### 6.7.2 PERT 算法 / Algorithme PERT

**FORWARD (向前传播) / Propagation avant** :
```
DTO(départ) = 0
DTO(N) = MAX(FTO(prédécesseurs))
FTO(N) = DTO(N) + Durée(N)
```

**BACKWARD (向后传播) / Propagation arrière** :
```
FTA(fin) = MAX(FTO)  ← la plus grande FTO
FTA(N) = MIN(DTA(successeurs))
DTA(N) = FTA(N) − Durée(N)
```

---

#### 6.7.3 4种依赖关系 / Les 4 Dépendances

| Type | Code | Signification | La plus courante ? |
|------|------|---------------|---------------------|
| Fin à Début | **FD / FS** | B commence après la fin de A | ✅ **OUI** (la plus courante) |
| Fin à Fin | **FF** | B finit après la fin de A | |
| Début à Début | **DD / SS** | B commence après le début de A | |
| Début à Fin | **DF / SF** | B finit après le début de A | Rare |

---

#### 6.7.4 关键路径 / Chemin Critique

> **Définition** : Chemin le plus long du réseau PERT où la **marge totale = 0**.
> 关键路径是PERT网络中最长的路径，其总浮动 = 0。

> **⚠️ Tout retard sur le chemin critique retarde TOUT le projet !**

---

### 6.8 甘特图 / Diagramme de Gantt

| Caractéristique | PERT | Gantt |
|-----------------|------|-------|
| **Représentation** | Graphe de dépendances (nœuds + flèches) | Calendrier absolu (barres horizontales) |
| **Temps** | Relatif (durées, marges) | Absolu (dates calendaires) |
| **Usage** | Calculer les marges et le chemin critique | Visualiser le planning dans le temps |

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### ⚠️ PERT 计算题完整解题步骤

> **Exemple complet / 完整例题** :

Soit le projet suivant :

| Tâche | Durée (j) | Prédécesseurs |
|-------|-----------|---------------|
| A | 3 | — |
| B | 4 | A |
| C | 2 | A |
| D | 5 | B |
| E | 3 | B, C |
| F | 2 | D, E |

**Étape 1 : FORWARD (DTO, FTO)**
```
DTO(A)=0, FTO(A)=0+3=3
DTO(B)=FTO(A)=3, FTO(B)=3+4=7
DTO(C)=FTO(A)=3, FTO(C)=3+2=5
DTO(D)=FTO(B)=7, FTO(D)=7+5=12
DTO(E)=MAX(FTO(B),FTO(C))=MAX(7,5)=7, FTO(E)=7+3=10
DTO(F)=MAX(FTO(D),FTO(E))=MAX(12,10)=12, FTO(F)=12+2=14
```

**Étape 2 : BACKWARD (FTA, DTA)**
```
FTA(F)=MAX(FTO)=14, DTA(F)=14-2=12
FTA(E)=DTA(F)=12, DTA(E)=12-3=9
FTA(D)=DTA(F)=12, DTA(D)=12-5=7
FTA(C)=DTA(E)=9, DTA(C)=9-2=7
FTA(B)=MIN(DTA(D),DTA(E))=MIN(7,9)=7, DTA(B)=7-4=3
FTA(A)=MIN(DTA(B),DTA(C))=MIN(3,7)=3, DTA(A)=3-3=0
```

**Étape 3 : Marge totale**
```
MT(A)=0-0=0  ← CHEMIN CRITIQUE
MT(B)=3-3=0  ← CHEMIN CRITIQUE
MT(C)=7-3=4
MT(D)=7-7=0  ← CHEMIN CRITIQUE
MT(E)=9-7=2
MT(F)=12-12=0 ← CHEMIN CRITIQUE
```

**Étape 4 : Chemin critique** = A → B → D → F (MT=0 partout)
**Durée totale du projet** = 14 jours

---

### 题型速查 / Guide Rapide par Type

| Type de question | Méthode |
|------------------|---------|
| Calculer DTO/FTO | **FORWARD** : DTO=MAX(FTO(préd)), FTO=DTO+D |
| Calculer DTA/FTA | **BACKWARD** : FTA=MIN(DTA(succ)), DTA=FTA−D |
| Trouver le chemin critique | Marge totale = 0 |
| Durée du projet | MAX(FTO) = FTO de la dernière tâche |
| Impact d'un retard | Si tâche critique → impact total; sinon → comparer avec marge |

---

### 常见陷阱 / Pièges Fréquents

| Piège | Correction |
|-------|------------|
| Confondre DTO et DTA | DTO = tôt (早), DTA = tard (晚) — ne pas inverser ! |
| MAX vs MIN | Forward = MAX, Backward = MIN |
| Oublier le MAX avec plusieurs prédécesseurs | Si une tâche a 2+ prédécesseurs, DTO = MAX des FTO |
| Chemin le plus COURT vs le plus LONG | Chemin critique = le plus LONG (pas le plus court !) |

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### PERT 公式卡 / Fiche Formules PERT

```
┌─────────────────────────────────────────────────────────┐
│                    FORMULES PERT                        │
├─────────────────────────────────────────────────────────┤
│ FTO = DTO + Durée                                      │
│ DTA = FTA − Durée                                      │
│ Marge Totale (MT) = DTA − DTO = FTA − FTO              │
│ Chemin Critique = MT = 0                               │
├─────────────────────────────────────────────────────────┤
│ FORWARD  (→): DTO(N) = MAX(FTO(prédécesseurs))         │
│ BACKWARD (←): FTA(N) = MIN(DTA(successeurs))           │
├─────────────────────────────────────────────────────────┤
│ Durée totale du projet = MAX(FTO) de toutes les tâches  │
└─────────────────────────────────────────────────────────┘
```

---

### 项目关键数字速记 / Chiffres Clés

| Concept | Valeur |
|---------|--------|
| Phases de gestion de projet | **5** |
| Chapitres du plan projet | **6** |
| Types de risques | **8** |
| Types de dépendances PERT | **4** (FD, FF, DD, DF) |
| Outils d'organigramme | **3** (PBS, WBS, OBS) |

---

### 自检清单 / Points de Contrôle

- [ ] Lister les 5 phases de gestion de projet dans l'ordre
- [ ] Expliquer SMART
- [ ] Citer les 8 types de risques
- [ ] Définir PBS, WBS, OBS
- [ ] **Calculer DTO, FTO, DTA, FTA sur un PERT**
- [ ] **Appliquer FORWARD (MAX) et BACKWARD (MIN)**
- [ ] **Calculer la marge totale**
- [ ] **Identifier le chemin critique (MT=0)**
- [ ] Différencier PERT (graphe) vs Gantt (calendrier)
- [ ] Nommer les 4 types de dépendances

---

> 📄 **Fin du Document 6** · Suite → [Document 7 : Code, Versioning, Tests & Clôture](./07_Code_Versioning_Tests.md)

---

### 📎 Annexe : Exercice PERT supplémentaire

**Énoncé** :

| Tâche | Durée | Prédécesseurs |
|-------|-------|---------------|
| P | 4 | — |
| Q | 6 | P |
| R | 3 | P |
| S | 2 | Q |
| T | 5 | Q, R |

**À faire** :
1. Calculer DTO, FTO, DTA, FTA
2. Calculer la marge totale pour chaque tâche
3. Identifier le chemin critique
4. Donner la durée totale du projet

*(Solution disponible dans le Document 8 — Formulaire complet)*
