# 软件工程复习文档 7：代码生产、版本控制、错误处理、测试与项目收尾

> **GÉNIE LOGICIEL — Document de Révision 7 : Production du Code, Versioning, Gestion d'Erreurs, Tests & Clôture**
> CY Cergy Paris Université — Dr. Daniela Pamplona, Dr. Fatiha Bousbahi
> 中法双语完整复习

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

## 7A. 代码生产 / Production du Code

---

### 7A.1 编码规范 / Règles de Codage

> **Objectif** : Uniformisation de la base de code source du projet.
> **目标**：统一项目源代码库。

| Avantage | 中文 |
|----------|------|
| Consultation du code facilitée | 代码查阅更方便 |
| Risques de duplication éliminés | 消除重复风险 |
| Chaque membre peut intervenir sur tout le code | 每个成员都能修改任何代码 |
| Nouveaux venus opérationnels plus vite | 新人更快上手 |

**Règles communes / 通用规则**：
- Conventions de nommage / 命名约定
- Indentation cohérente / 一致的缩进
- Commentaires significatifs / 有意义的注释
- Structures de fichiers standardisées / 标准化文件结构

---

### 7A.2 代码审查 / Revue de Code (Code Review)

| Aspect | Description |
|--------|-------------|
| **Qui ?** | Pairs (autres développeurs) |
| **Quand ?** | Avant l'intégration dans la branche principale |
| **Pourquoi ?** | Détecter bugs, améliorer qualité, partager connaissances |

---

## 7B. 版本控制 / Gestion des Versions (Git)

---

### 7B.1 Git 核心概念 / Concepts Fondamentaux

| Concept | 中文 | Définition |
|---------|------|------------|
| **Repository (Repo)** | 仓库 | Espace de stockage du projet + historique |
| **Commit** | 提交 | Sauvegarde d'un instantané (snapshot) du code |
| **Branch** | 分支 | Ligne de développement indépendante |
| **Merge** | 合并 | Fusionner deux branches |
| **Rebase** | 变基 | Réécrire l'historique pour une base linéaire |
| **Clone** | 克隆 | Copier un repo distant en local |
| **Push / Pull** | 推送/拉取 | Synchroniser avec le repo distant |

---

### 7B.2 Git 常用命令 / Commandes Essentielles

```bash
git init                  # Initialiser un repo / 初始化仓库
git add <fichier>         # Ajouter au staging / 添加到暂存区
git commit -m "message"   # Créer un commit / 创建提交
git branch <nom>          # Créer une branche / 创建分支
git checkout <branche>    # Changer de branche / 切换分支
git merge <branche>       # Fusionner / 合并分支
git push origin main      # Pousser vers le remote / 推送到远程
git pull                  # Récupérer les changements / 拉取更新
git clone <url>           # Cloner un repo / 克隆仓库
```

---

### 7B.3 GitHub 工作流 / Workflow GitHub

```
main (production) ←── develop ←── feature/xxx
    主分支                开发分支          功能分支
```

| Branche | Usage |
|---------|-------|
| `main` / `master` | Code de production / 生产代码 |
| `develop` | Intégration du développement / 开发集成 |
| `feature/xxx` | Développement d'une fonctionnalité / 功能开发 |

---

## 7C. 错误处理 / Gestion des Erreurs

---

### 7C.1 错误处理策略 / Stratégies

| Stratégie | 中文 | Description |
|-----------|------|-------------|
| **Try-Catch-Finally** | 异常捕获 | Capturer les exceptions, toujours exécuter le `finally` |
| **Programmation défensive** | 防御式编程 | Vérifier les entrées AVANT de les utiliser |
| **Logging** | 日志记录 | Enregistrer les erreurs pour diagnostic |
| **Fail-fast** | 快速失败 | Détecter et signaler les erreurs immédiatement |

---

### 7C.2 异常类型 / Types d'Exceptions

| Type | Exemple |
|------|---------|
| **Exceptions vérifiées** (checked) | Fichier non trouvé, erreur réseau |
| **Exceptions non vérifiées** (unchecked/runtime) | NullPointerException, division par zéro |
| **Erreurs** (Errors) | OutOfMemoryError — généralement non récupérables |

---

## 7D. 软件测试 / Tests de Logiciels ⚠️ 重点

---

### 7D.1 测试金字塔 / Pyramide des Tests

```
        ┌─────────┐
        │ Accept. │  ← Peu nombreux, lents, bout-en-bout
        │ 验收测试 │
       ┌┴─────────┴┐
       │  Système   │  ← Tests complets du système
       │  系统测试   │
      ┌┴───────────┴┐
      │ Intégration  │  ← Tests entre modules
      │  集成测试     │
     ┌┴─────────────┴┐
     │   Unitaires    │  ← Très nombreux, rapides, isolés
     │   单元测试      │
     └───────────────┘
```

| Niveau | 中文 | Portée | Qui ? |
|--------|------|--------|-------|
| **Unitaire** | 单元测试 | Fonction/classe isolée | Développeurs |
| **Intégration** | 集成测试 | Interaction entre modules | Développeurs |
| **Système** | 系统测试 | Système complet | Équipe test |
| **Acceptation** | 验收测试 | Validation métier | Client/utilisateurs |

---

### 7D.2 功能 vs 非功能测试

#### 功能测试 / Tests Fonctionnels

| Type | 中文 | Description |
|------|------|-------------|
| **Boîte noire** (Black Box) | 黑盒测试 | Tester sans connaître le code interne |
| **Boîte blanche** (White Box) | 白盒测试 | Tester en connaissant la structure interne |
| **End to End** | 端到端测试 | Simulation d'utilisation réelle (scénarios) |
| **Monkey Testing** | 猴子测试 | Inputs aléatoires pour vérifier la robustesse |

#### 非功能测试 / Tests Non Fonctionnels (ISO 25010)

| Type | 中文 | Aspects testés |
|------|------|----------------|
| **Sécurité** | 安全性 | Confidentialité, intégrité, authenticité |
| **Performance** | 性能 | Temps de réponse, utilisation ressources, capacité |
| **Usabilité** | 可用性 | Intelligibilité, apprentissage, opérabilité, ergonomie |
| **Compatibilité** | 兼容性 | Coexistence avec autres logiciels, interopérabilité |

---

### 7D.3 路径测试 / Path Testing ⚠️ 重点

**圈复杂度 / Complexité Cyclomatique V(G)** :

> **V(G) = E − N + 2**  (E = nombre d'arêtes/edges, N = nombre de nœuds/nodes)
> **V(G) = P + 1**  (P = nombre de nœuds de prédicat/décision)

| Formule | Composants |
|---------|------------|
| `V(G) = E − N + 2` | E = arêtes (edges), N = nœuds (nodes) |
| `V(G) = P + 1` | P = nœuds de décision (prédicats) |

> **🔑 V(G)** = nombre de chemins indépendants à tester
> V(G) = 需要测试的独立路径数量

**Exemple** :
```
    ① → ② → ③ → ⑤ → ⑥ → ⑦  (Chemin 1)
              ↓
              ④ → ⑤ → ⑥ → ⑦  (Chemin 2)
    ① → ⑥ → ⑦                  (Chemin 3)
```
`V(G) = 3 = P+1` (2 décisions + 1 = 3 chemins)

---

### 7D.4 测试用例设计 / Conception de Cas de Test

| Méthode | 中文 | Description |
|---------|------|-------------|
| **Équivalence** (Classes d'équivalence) | 等价类划分 | Regrouper les entrées en classes de comportement équivalent |
| **Valeurs limites** (Boundary Value) | 边界值分析 | Tester aux frontières des classes d'équivalence |

**Exemple** : Champ acceptant 1-100
- Classes : <1 (invalide), 1-100 (valide), >100 (invalide)
- Valeurs limites : 0, 1, 100, 101

---

## 7E. 项目收尾 / Clôture du Projet

| Étape | 中文 | Description |
|-------|------|-------------|
| **Livraison finale** | 最终交付 | Code + documentation + manuels |
| **Validation client** | 客户验收 | Le client approuve le travail |
| **Leçons apprises** | 经验教训 | Documenter ce qui a bien/pas bien fonctionné |
| **Archivage** | 归档 | Conserver tous les documents du projet |

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### 题型一：圈复杂度计算 / Calculer V(G)

**Méthode** :
1. Compter le nombre d'**arêtes** (E) et de **nœuds** (N) dans le graphe
2. OU compter le nombre de **nœuds de décision** (P)
3. Appliquer `V(G) = E − N + 2` OU `V(G) = P + 1`

**Exemple** : Graphe avec 7 nœuds, 8 arêtes, 2 décisions
- `V(G) = 8 − 7 + 2 = 3`
- `V(G) = 2 + 1 = 3`
- → 3 chemins indépendants à tester

---

### 题型二：测试类型识别

| Énoncé | Type de test |
|--------|-------------|
| « Vérifier qu'une fonction calcule correctement » | **Unitaire** |
| « Tester l'interaction entre le module A et le module B » | **Intégration** |
| « Tester toutes les fonctionnalités ensemble » | **Système** |
| « Le client vérifie que ça répond à ses besoins » | **Acceptation** |
| « Vérifier le temps de réponse sous forte charge » | **Performance** (non fonctionnel) |
| « Vérifier la protection contre les injections SQL » | **Sécurité** (non fonctionnel) |

---

### 题型三：选择题 — 等价类与边界值

> « Un champ accepte les âges de 18 à 65 ans. Quelles valeurs tester ? »

**✅ Réponse** :
- Valeurs limites : 17, 18, 65, 66
- Classes d'équivalence : <18 (invalide), 18-65 (valide), >65 (invalide)

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### 公式速查 / Fiche Formules

| Domaine | Formule |
|---------|---------|
| **V(G) formule 1** | `V(G) = E − N + 2` |
| **V(G) formule 2** | `V(G) = P + 1` |
| **V(G) interprétation** | Nombre de chemins indépendants à tester |

---

### 测试分类速查 / Classification Rapide

```
Tests
├── Fonctionnels (ce que ça FAIT)
│   ├── Unitaires (isolés)
│   ├── Intégration (inter-modules)
│   ├── Système (complet)
│   └── Acceptation (métier)
└── Non Fonctionnels (COMMENT ça le fait)
    ├── Sécurité
    ├── Performance
    ├── Usabilité
    └── Compatibilité
```

---

### Git 命令速记 / Aide-mémoire Git

| Action | Commande |
|--------|----------|
| Nouveau repo | `git init` |
| Sauvegarder | `git add .` + `git commit -m "msg"` |
| Nouvelle branche | `git branch nom` |
| Changer branche | `git checkout nom` |
| Fusionner | `git merge nom` |
| Envoyer | `git push` |
| Récupérer | `git pull` |

---

### 自检清单 / Points de Contrôle

- [ ] Expliquer l'importance des règles de codage communes
- [ ] Décrire le workflow Git de base (clone → branch → commit → push → merge)
- [ ] Différencier les stratégies de gestion d'erreurs
- [ ] **Décrire la pyramide des tests (4 niveaux)**
- [ ] Distinguer tests fonctionnels vs non fonctionnels
- [ ] **Calculer V(G) avec E−N+2 et P+1**
- [ ] Appliquer les classes d'équivalence et valeurs limites
- [ ] Citer les 4 types de tests non fonctionnels ISO 25010
- [ ] Lister les étapes de clôture du projet

---

> 📄 **Fin du Document 7** · Suite → [Document 8 : Exercices & Formulaire Complet](./08_Exercices_Formulaire.md)
