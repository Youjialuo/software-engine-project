# 软件工程复习文档 6：项目管理与PERT/甘特图
# GÉNIE LOGICIEL — Document de Révision 6 : Gestion de Projet, PERT & Gantt

> CY Cergy Paris Université — Dr. Daniela Pamplona
> **中法双语完整复习 · Révision Bilingue Complète · ⚠️ 计算题重点**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

### 6.1 Pourquoi la Gestion de Projet ? / 为什么需要项目管理？

> **FR** : « Une bonne gestion ne peut pas garantir le succès, mais une mauvaise gestion conduit généralement à l'échec. » Le chef de projet doit veiller à respecter les contraintes (budget, délais, périmètre) tout en livrant un logiciel de haute qualité.

> **ZH** : 「好的管理不能保证成功，但差的管理通常导致失败。」项目经理必须在交付高质量软件的同时，遵守约束条件（预算、时间、范围）。

---

### 6.2 Les 5 Phases de la Gestion de Projet / 项目管理五阶段

| # | Phase (FR) | 阶段 (ZH) | Activités Principales |
|---|------------|-----------|----------------------|
| ① | **Étude de faisabilité** | 可行性研究 | Vérifier si le projet est techniquement et économiquement réalisable. |
| ② | **Planification** | 规划 | Rédiger le plan de projet : objectifs SMART, risques, ressources, calendrier. |
| ③ | **Exécution** | 执行 | Réaliser les livrables. Déléguer les tâches. Coordonner l'équipe. |
| ④ | **Surveillance et contrôle** | 监控 | Suivre les indicateurs (temps, coûts, qualité). Ajuster si nécessaire. |
| ⑤ | **Clôture** | 收尾 | Travail terminé et approuvé. Documenter les leçons apprises. Archiver. |

> **🧠 Mnémotechnique** : « **F**ais **P**la **E**xé **S**ur **C**lô » / 「**可规执监收**」

---

### 6.3 SMART / SMART目标

| L | Signification (FR) | 中文 |
|---|---------------------|------|
| **S** | Spécifique | 具体的 |
| **M** | Mesurable | 可衡量的 |
| **A** | Atteignable (Achievable) | 可实现的 |
| **R** | Pertinent (Relevant) | 相关的 |
| **T** | Temporellement défini (Time-bound) | 有时限的 |

---

### 6.4 Les 8 Types de Risques / 八种风险类型

| # | Risque (FR) | 风险 (ZH) |
|---|-------------|-----------|
| 1 | Commerciaux | 商业风险 |
| 2 | Financiers | 财务风险 |
| 3 | Techniques | 技术风险 |
| 4 | Développement | 开发风险 |
| 5 | Calendrier | 进度风险 |
| 6 | Bogues et erreurs | 缺陷与错误 |
| 7 | Exigences mal comprises | 需求理解错误 |
| 8 | Changement fréquent des exigences | 需求频繁变更 |

**Matrice des risques / 风险矩阵** = **Probabilité × Impact** / 概率 × 影响

---

### 6.5 Outils de Gestion / 管理工具

| Outil (FR) | 工具 (ZH) | Usage |
|------------|-----------|-------|
| **PBS** (Product Breakdown Structure) | 产品分解结构 | Décomposer le PRODUIT en sous-ensembles |
| **WBS** (Work Breakdown Structure) | 任务分解结构 | Décomposer le TRAVAIL en tâches |
| **OBS** (Organizational Breakdown Structure) | 组织分解结构 | Structurer l'ÉQUIPE |

---

### 6.6 ⚠️ PERT — Calculs Essentiels / PERT核心计算

> **FR** : PERT (Program Evaluation and Review Techniques) est une méthode de planification de projet développée par la marine américaine dans les années 1950 pour le projet Polaris. Le calcul PERT est INCONTOURNABLE à l'examen.

> **ZH** : PERT（计划评审技术）是美国海军在1950年代为北极星项目开发的规划方法。PERT计算是考试中**必考**内容。

---

#### Définitions Fondamentales / 基本定义

| Abréviation | Nom Complet (FR) | 中文 | Formule |
|-------------|-------------------|------|---------|
| **DTO / ES** | Début au plus tôt (Earliest Start) | 最早开始时间 | DTO(N) = MAX(FTO(prédécesseurs)) |
| **FTO / EF** | Fin au plus tôt (Earliest Finish) | 最早完成时间 | **FTO = DTO + Durée** |
| **DTA / LS** | Début au plus tard (Latest Start) | 最晚开始时间 | DTA = FTA − Durée |
| **FTA / LF** | Fin au plus tard (Latest Finish) | 最晚完成时间 | FTA(N) = MIN(DTA(successeurs)) |
| **MT** | Marge Totale (Total Float) | 总浮动 | **MT = DTA − DTO = FTA − FTO** |
| **ML** | Marge Libre (Free Float) | 自由浮动 | Délai sans impacter les tâches suivantes |

---

#### Algorithme PERT / PERT算法

**FORWARD (向前传播)** — calcul des temps « au plus tôt » :
```
DTO(départ) = 0
Pour chaque tâche N (dans l'ordre topologique) :
    DTO(N) = MAX(FTO de tous les prédécesseurs de N)
    FTO(N) = DTO(N) + Durée(N)
```

**BACKWARD (向后传播)** — calcul des temps « au plus tard » :
```
FTA(dernière tâche) = MAX(FTO de toutes les tâches)
Pour chaque tâche N (dans l'ordre topologique INVERSE) :
    FTA(N) = MIN(DTA de tous les successeurs de N)
    DTA(N) = FTA(N) − Durée(N)
```

> **🔑 Règle d'Or** : FORWARD utilise **MAX**. BACKWARD utilise **MIN**.

---

#### Chemin Critique / 关键路径

> **FR** : Le chemin critique est le chemin le PLUS LONG du réseau PERT. Toutes les tâches sur ce chemin ont une **marge totale = 0**. Tout retard sur une tâche critique retarde TOUT le projet.

> **ZH** : 关键路径是PERT网络中最**长**的路径。该路径上所有任务**总浮动 = 0**。任何关键任务延迟都会延迟**整个**项目。

---

#### Les 4 Types de Dépendances / 四种依赖关系

| Type | Code | Signification (FR) | 含义 (ZH) | Fréquence |
|------|------|---------------------|-----------|-----------|
| Fin à Début | **FD / FS** | B commence après la fin de A | B在A完成后开始 | **La plus courante** |
| Fin à Fin | **FF** | B finit après la fin de A | B在A完成后完成 | |
| Début à Début | **DD / SS** | B commence après le début de A | B在A开始后开始 | |
| Début à Fin | **DF / SF** | B finit après le début de A | B在A开始后完成 | Rare |

---

### 6.7 Diagramme de Gantt / 甘特图

| Critère | PERT | Gantt |
|---------|------|-------|
| **Représentation** | Graphe de dépendances (réseau) | Barres horizontales sur un calendrier |
| **Temps** | Relatif (durées, marges) | Absolu (dates calendaires) |
| **Usage Principal** | Calculer le chemin critique et les marges | Visualiser le planning dans le temps |

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Calcul PERT Complet — Exemple Pas à Pas

**Énoncé** :

| Tâche | Durée (j) | Prédécesseurs |
|-------|-----------|---------------|
| A | 3 | — |
| B | 4 | A |
| C | 2 | A |
| D | 5 | B |
| E | 3 | B, C |
| F | 2 | D, E |

**Étape 1 — FORWARD** :
```
DTO(A)=0,                 FTO(A)=0+3=3
DTO(B)=FTO(A)=3,          FTO(B)=3+4=7
DTO(C)=FTO(A)=3,          FTO(C)=3+2=5
DTO(D)=FTO(B)=7,          FTO(D)=7+5=12
DTO(E)=MAX(7,5)=7,        FTO(E)=7+3=10
DTO(F)=MAX(12,10)=12,     FTO(F)=12+2=14
```

**Étape 2 — BACKWARD** :
```
FTA(F)=14,                DTA(F)=14-2=12
FTA(E)=DTA(F)=12,         DTA(E)=12-3=9
FTA(D)=DTA(F)=12,         DTA(D)=12-5=7
FTA(C)=DTA(E)=9,          DTA(C)=9-2=7
FTA(B)=MIN(7,9)=7,        DTA(B)=7-4=3
FTA(A)=MIN(3,7)=3,        DTA(A)=3-3=0
```

**Étape 3 — Marges** :
```
MT(A)=0-0=0 ← CRITIQUE    MT(D)=7-7=0 ← CRITIQUE
MT(B)=3-3=0 ← CRITIQUE    MT(E)=9-7=2
MT(C)=7-3=4               MT(F)=12-12=0 ← CRITIQUE
```

**✅ Résultat** : Chemin critique = **A → B → D → F** | Durée = **14 jours**

---

### Pièges Fréquents / 常见陷阱

| Piège (FR) | 陷阱 (ZH) | Correction |
|------------|-----------|------------|
| Confondre DTO (tôt) et DTA (tard) | 混淆最早和最晚 | DTO = tôt (早), DTA = tard (晚) |
| Utiliser MIN au lieu de MAX en FORWARD | Forward用了MIN而非MAX | Forward = **MAX**, Backward = **MIN** |
| Prendre le chemin le plus COURT | 取了最短路径 | Chemin critique = le plus **LONG** |
| Oublier MAX avec plusieurs prédécesseurs | 多前驱忘取MAX | Si 2+ prédécesseurs → DTO = MAX des FTO |

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

### Fiche Formules PERT / PERT公式卡

```
┌──────────────────────────────────────────────────────────────┐
│                   FORMULES PERT                              │
├──────────────────────────────────────────────────────────────┤
│ FTO = DTO + Durée                                            │
│ DTA = FTA − Durée                                            │
│ Marge Totale = DTA − DTO = FTA − FTO                        │
│ Chemin Critique = Marge Totale = 0                           │
├──────────────────────────────────────────────────────────────┤
│ FORWARD (→) : DTO(N) = MAX(FTO(prédécesseurs))              │
│ BACKWARD (←): FTA(N) = MIN(DTA(successeurs))                │
├──────────────────────────────────────────────────────────────┤
│ Durée totale = MAX(FTO)                                      │
└──────────────────────────────────────────────────────────────┘
```

### Checklist

| # | Je sais... | ✓ |
|---|---|---|
| 1 | Lister les 5 phases de gestion de projet dans l'ordre | ☐ |
| 2 | Expliquer SMART | ☐ |
| 3 | Citer les 8 types de risques | ☐ |
| 4 | **Calculer DTO, FTO, DTA, FTA sur un PERT** | ☐ |
| 5 | **Appliquer FORWARD (MAX) et BACKWARD (MIN)** | ☐ |
| 6 | **Calculer la marge totale et identifier le chemin critique** | ☐ |
| 7 | Différencier PERT (graphe) vs Gantt (calendrier) | ☐ |

---

> 📄 **Fin du Document 6** · Suite → [Document 7 : Code, Tests & Clôture](./07_Code_Versioning_Tests.md)
