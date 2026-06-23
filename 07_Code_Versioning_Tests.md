# 软件工程复习文档 7：代码生产、版本控制、错误处理、测试与项目收尾
# GÉNIE LOGICIEL — Document de Révision 7 : Code, Versioning, Tests & Clôture

> CY Cergy Paris Université — Dr. Daniela Pamplona, Dr. Fatiha Bousbahi
> **中法双语完整复习 · Révision Bilingue Complète**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

## 7A. PRODUCTION DU CODE / 代码生产

---

### 7A.1 Règles de Codage / 编码规范

> **FR** : L'objectif des règles de codage est l'UNIFORMISATION de la base de code. Quand tout le code suit les mêmes conventions, n'importe quel développeur peut comprendre et modifier n'importe quelle partie du projet.

> **ZH** : 编码规范的目标是代码库的**统一化**。当所有代码遵循相同的约定时，任何开发者都可以理解和修改项目的任何部分。

| Avantage (FR) | 优点 (ZH) |
|---|---|
| La consultation du code est FACILITÉE | 代码查阅更加方便 |
| Les risques de DUPLICATION sont éliminés | 消除重复代码的风险 |
| Chaque membre peut intervenir sur TOUT le code | 每个成员都能修改**任何**代码 |
| Les nouveaux venus sont opérationnels plus VITE | 新人更快上手 |

---

### 7A.2 Revue de Code (Code Review) / 代码审查

> **FR** : La revue de code consiste à faire relire le code par un autre développeur AVANT de l'intégrer. Objectifs : détecter les bugs tôt, améliorer la qualité, partager les connaissances dans l'équipe.

> **ZH** : 代码审查是在集成之前让另一位开发者审阅代码。目标：早期发现缺陷、提高质量、在团队中分享知识。

---

## 7B. GESTION DES VERSIONS (GIT) / 版本控制

---

### 7B.1 Concepts Fondamentaux / 核心概念

| Concept (FR) / 概念 (ZH) | Définition (FR) | 定义 (ZH) |
|---|---|---|
| **Repository** / 仓库 | Espace de stockage du projet + tout son historique | 项目 + 全部历史的存储空间 |
| **Commit** / 提交 | Sauvegarde d'un instantané (snapshot) du code à un instant T | 代码在某个时刻的快照保存 |
| **Branch** / 分支 | Ligne de développement INDÉPENDANTE | **独立的**开发线 |
| **Merge** / 合并 | Fusionner les changements d'une branche dans une autre | 将一分支的变更合并到另一分支 |
| **Push / Pull** / 推送/拉取 | Synchroniser le repo local avec le repo distant | 同步本地仓库和远程仓库 |

---

### 7B.2 Commandes Git Essentielles / Git常用命令

```bash
git init                    # Initialiser un nouveau repo / 初始化新仓库
git add <fichier>           # Ajouter au staging (zone d'index) / 添加到暂存区
git commit -m "message"     # Créer un commit avec un message / 创建提交
git branch <nom>            # Créer une nouvelle branche / 创建新分支
git checkout <branche>      # Changer de branche active / 切换分支
git merge <branche>         # Fusionner la branche dans la branche courante
git push origin main        # Envoyer vers le dépôt distant / 推送到远程
git pull                    # Récupérer les changements distants / 拉取远程更新
git clone <url>             # Cloner un dépôt distant / 克隆远程仓库
```

---

### 7B.3 Workflow Git Standard / 标准Git工作流

```
main ────────────────────────────── (production / 生产环境)
  │
  └── develop ──────────────────── (intégration / 开发集成)
        │
        ├── feature/login ──────── (fonctionnalité / 功能分支)
        ├── feature/paiement ────
        └── fix/bug-123 ───────── (correction / 修复分支)
```

---

## 7C. GESTION DES ERREURS / 错误处理

---

### 7C.1 Stratégies / 错误处理策略

| Stratégie (FR) / 策略 (ZH) | Description (FR) | 描述 (ZH) |
|---|---|---|
| **Try-Catch-Finally** / 异常捕获 | Capturer les exceptions pour éviter le crash. Le bloc `finally` s'exécute TOUJOURS (libération des ressources). | 捕获异常防止崩溃。`finally`块**始终**执行（释放资源）。 |
| **Programmation défensive** / 防御式编程 | Vérifier TOUTES les entrées AVANT de les utiliser. Ne jamais faire confiance aux données externes. | 在使用**之前**验证**所有**输入。永远不信任外部数据。 |
| **Logging** / 日志记录 | Enregistrer les erreurs avec leur contexte (timestamp, utilisateur, action) pour faciliter le diagnostic. | 记录错误及其上下文（时间戳、用户、操作）以便诊断。 |
| **Fail-fast** / 快速失败 | Détecter et signaler les erreurs IMMÉDIATEMENT, plutôt que de les laisser se propager. | **立即**检测并报告错误，而不是让它们传播。 |

---

## 7D. TESTS DE LOGICIELS / 软件测试 ⚠️ 重点

---

### 7D.1 La Pyramide des Tests / 测试金字塔

> **FR** : La pyramide des tests illustre la proportion IDÉALE des différents types de tests. Plus on descend, plus les tests sont NOMBREUX, RAPIDES et ISOLÉS.

> **ZH** : 测试金字塔展示了不同类型测试的**理想**比例。越往下，测试越**多**、越**快**、越**独立**。

```
        ┌──────────┐
        │ Accept.  │  ← Peu nombreux, lents, testent le système complet
        │ 验收测试  │
       ┌┴──────────┴┐
       │  Système    │  ← Tests fonctionnels complets
       │  系统测试    │
      ┌┴────────────┴┐
      │ Intégration   │  ← Tests des interactions entre modules
      │  集成测试      │
     ┌┴──────────────┴┐
     │   Unitaires     │  ← Très nombreux, rapides (< 1ms), isolés
     │   单元测试       │
     └────────────────┘
```

| Niveau | FR | ZH | Portée |
|--------|-----|-----|--------|
| **Unitaire** | Test d'une fonction ou classe isolée | 测试独立的函数或类 | Fonction/classe seule |
| **Intégration** | Test de l'interaction entre plusieurs modules | 测试多模块之间的交互 | Modules |
| **Système** | Test du système complet assemblé | 测试完整组装的系统 | Application entière |
| **Acceptation** | Validation par le client/utilisateur final | 客户/最终用户验收 | Besoins métier |

---

### 7D.2 Tests Fonctionnels vs Non Fonctionnels

#### Tests Fonctionnels / 功能测试

| Type (FR) / 类型 (ZH) | Description |
|---|---|
| **Boîte noire** (Black Box) / 黑盒 | Tester sans connaître le code interne — on teste les entrées/sorties |
| **Boîte blanche** (White Box) / 白盒 | Tester en connaissant la structure interne du code |
| **End to End** (E2E) / 端到端 | Simulation d'un scénario d'utilisation réel complet |

#### Tests Non Fonctionnels (ISO 25010) / 非功能测试

| Type (FR) / 类型 (ZH) | Aspects Testés (FR) | 测试方面 (ZH) |
|---|---|---|
| **Sécurité** / 安全性 | Confidentialité, intégrité, authenticité, non-répudiation | 保密性、完整性、真实性、不可否认性 |
| **Performance** / 性能 | Temps de réponse, utilisation ressources, capacité maximale | 响应时间、资源使用、最大容量 |
| **Usabilité** / 可用性 | Intelligibilité, apprentissage, opérabilité, ergonomie | 可理解性、易学性、可操作性、人体工学 |
| **Compatibilité** / 兼容性 | Coexistence avec autres logiciels, interopérabilité | 与其他软件共存、互操作性 |

---

### 7D.3 Path Testing — Complexité Cyclomatique / 路径测试 ⚠️

> **FR** : La complexité cyclomatique V(G) mesure le nombre de CHEMINS INDÉPENDANTS dans un programme. Elle est utilisée pour déterminer le nombre MINIMAL de cas de test nécessaires pour couvrir tous les chemins.

> **ZH** : 圈复杂度V(G)衡量程序中**独立路径**的数量。用于确定覆盖所有路径所需的**最小**测试用例数。

**Deux Formules Équivalentes / 两个等价公式** :

| Formule | Composants |
|---------|------------|
| **V(G) = E − N + 2** | E = nombre d'arêtes (edges), N = nombre de nœuds (nodes) |
| **V(G) = P + 1** | P = nombre de nœuds de décision (prédicats) |

**Exemple** : Pour un graphe avec 7 nœuds, 8 arêtes et 2 décisions :
- V(G) = 8 − 7 + 2 = **3**
- V(G) = 2 + 1 = **3**
- → **3 chemins indépendants** à tester

---

### 7D.4 Conception de Cas de Test / 测试用例设计

| Méthode (FR) / 方法 (ZH) | Principe (FR) | 原理 (ZH) |
|---|---|---|
| **Classes d'équivalence** / 等价类划分 | Regrouper les entrées qui ont un comportement SIMILAIRE. Tester UNE valeur par classe. | 将行为**相似**的输入分组。每组测试**一个**值。 |
| **Valeurs limites** / 边界值分析 | Tester aux FRONTIÈRES des classes d'équivalence (là où les bugs se cachent). | 测试等价类的**边界**（bug藏身之处）。 |

**Exemple** : Champ acceptant les valeurs de 1 à 100
- Classes : <1 (invalide), 1-100 (valide), >100 (invalide)
- Valeurs limites à tester : **0, 1, 100, 101**

---

## 7E. CLÔTURE DU PROJET / 项目收尾

| Étape (FR) / 步骤 (ZH) | Description |
|---|---|
| **Livraison finale** / 最终交付 | Code source, documentation, manuels utilisateur |
| **Validation client** / 客户验收 | Le client approuve formellement le livrable |
| **Leçons apprises** / 经验教训 | Documenter ce qui a fonctionné et ce qui peut être amélioré |
| **Archivage** / 归档 | Conserver tous les documents et le code pour référence future |

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Type 1 : Calculer V(G)

**Méthode** : (1) Compter E et N dans le graphe, (2) OU compter P (décisions), (3) Appliquer la formule.

**Exemple** : Graphe avec 6 nœuds, 7 arêtes, 2 décisions
→ V(G) = 7 − 6 + 2 = **3**  ou  V(G) = 2 + 1 = **3**

---

### Type 2 : Identifier le Type de Test

| Énoncé | Type |
|--------|------|
| « Vérifier qu'une fonction calcule correctement » | **Unitaire** |
| « Tester l'interaction entre module A et module B » | **Intégration** |
| « Le client vérifie que ça répond à ses besoins » | **Acceptation** |
| « Vérifier le temps de réponse sous 1000 utilisateurs » | **Performance** (non fonctionnel) |

---

### Type 3 : Classes d'Équivalence et Valeurs Limites

> « Un champ accepte les âges de 18 à 65 ans. Quelles valeurs tester ? »

**✅** : Limites = **17, 18, 65, 66**. Classes = <18 (invalide), 18-65 (valide), >65 (invalide).

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

### Formules Clés

| Domaine | Formule |
|---------|---------|
| **V(G)** | V(G) = E − N + 2 = P + 1 |

### Pyramide des Tests

```
Tests
├── Fonctionnels (ce que ça FAIT)
│   ├── Unitaires → Intégration → Système → Acceptation
└── Non Fonctionnels (COMMENT ça le fait)
    ├── Sécurité, Performance, Usabilité, Compatibilité
```

### Checklist

| # | Je sais... | ✓ |
|---|---|---|
| 1 | Expliquer l'importance des règles de codage | ☐ |
| 2 | Décrire le workflow Git (clone → branch → commit → push → merge) | ☐ |
| 3 | Différencier les stratégies de gestion d'erreurs | ☐ |
| 4 | Décrire la pyramide des tests (4 niveaux) | ☐ |
| 5 | Distinguer tests fonctionnels vs non fonctionnels | ☐ |
| 6 | **Calculer V(G) avec E−N+2 et P+1** | ☐ |
| 7 | Appliquer classes d'équivalence et valeurs limites | ☐ |
| 8 | Lister les étapes de clôture du projet | ☐ |

---

> 📄 **Fin du Document 7** · Suite → [Document 8 : Exercices & Formulaire Complet](./08_Exercices_Formulaire.md)
