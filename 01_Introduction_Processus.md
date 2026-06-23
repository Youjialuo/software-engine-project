# 软件工程复习文档 1：导论与过程模型

> **GÉNIE LOGICIEL — Document de Révision 1 : Introduction & Modèles de Processus**
> CY Cergy Paris Université — Dr. Daniela Pamplona, Dr. Fatiha Bousbahi
> 中法双语完整复习

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

### 1.1 软件定义 / Définition du Logiciel

| 术语 | 法文 | 中文 |
|------|------|------|
| **Programme informatique** | Ensemble d'opérations exécutées automatiquement sur un support informatique | 在计算机载体上自动执行的一系列操作集合 |
| **Logiciel** | Ensemble d'instructions + éléments opérationnels (fichiers de configuration, données, procédures...) | 指令集 + 操作元素（配置文件、数据、自动程序等） |

> **🔑 关键点 / Point clé**：Un logiciel n'est PAS qu'un simple programme — c'est un ensemble complet incluant documentation, configuration, données et procédures.
> 软件不仅仅是程序——它是包含文档、配置、数据和过程的完整集合。

> **⚠️ 考试陷阱 / Piège d'examen**：« Un logiciel = un programme » → **FAUX !**
> 软件 ≠ 程序。软件 = 程序 + 文档 + 配置 + 数据 + 过程。

---

### 1.2 软件类型 / Types de Logiciels

#### A) 按应用领域 / Par domaine d'application

| Type / 类型 | Description / 描述 |
|---|---|
| Applications métier / 商业应用 | Logiciels de gestion d'entreprise (ERP, CRM, comptabilité) |
| Logiciels systèmes / 系统软件 | OS, compilateurs, drivers — gestion des ressources matérielles |
| Logiciels embarqués / 嵌入式软件 | Contrôle d'appareils spécifiques (automobile, médical, IoT) |
| Applications web & mobiles / 网页与移动应用 | Centrées réseau, intégrées BD, architecture client-serveur |
| Intelligence artificielle / 人工智能 | ML, deep learning, NLP, systèmes experts, vision |

#### B) 按许可协议 / Par contrat de licence

| Type / 类型 | Caractéristique / 特点 | Exemple |
|---|---|---|
| Propriétaire / 专有软件 | Auteur réserve droits de diffusion et modification | Windows, Photoshop |
| Libre / 自由软件 | 4 libertés : exécuter, étudier, modifier, redistribuer | Linux, GCC |
| Gratuit (Freeware) / 免费软件 | Propriétaire mais gratuit ; pas d'accès au code source | Skype |
| Partagiciel (Shareware) / 共享软件 | Diffusion autorisée, version limitée (période d'essai) | WinZip |

---

### 1.3 好的软件四大属性 / Les 4 Attributs d'un Bon Logiciel

| # | Attribut | 中文 | Définition |
|---|----------|------|------------|
| ① | **Maintenabilité** | 可维护性 | Facilité d'entretien, évolution, correction de bugs |
| ② | **Fiabilité & Sécurité** | 可靠性与安全性 | Fonctionnement sans défaillance, protection des données |
| ③ | **Efficacité** | 效率 | Utilisation optimale des ressources (CPU, mémoire, stockage) |
| ④ | **Acceptabilité** | 可接受性 | Compréhensible, utilisable, compatible avec autres systèmes |

> **🧠 记忆口诀 / Moyen mnémotechnique**：
> **« M-FEA »** → Maintenabilité, Fiabilité, Efficacité, Acceptabilité
> 中文：**「维可效受」** → 维护性、可靠性、效率、可接受性

---

### 1.4 软件危机 / La Crise du Logiciel

| 年份 | 事件 |
|------|------|
| **1950** | Apparition des langages de programmation de haut niveau / 高级编程语言出现 |
| **1960** | Nouveaux champs d'application (calcul scientifique → gestion) / 新应用领域 |
| **Fin 1960** | **CRISE DU LOGICIEL / 软件危机** — 交付延迟、预算超支、不符合需求、难以维护 |
| **1968** | Conférence OTAN à Garmisch → **Naissance du « Génie Logiciel »** / 软件工程术语诞生 |

> **🔑 关键点**：La crise a montré que le développement logiciel nécessite une approche **SYSTÉMATIQUE et DISCIPLINÉE**, pas seulement des compétences en programmation.
> 软件危机表明软件开发需要系统化、纪律化的工程方法。

---

### 1.5 软件工程定义 / Définition du Génie Logiciel

> **Définition IEEE** : « L'application d'une approche systématique, disciplinée et quantifiable au développement, à l'exploitation et à la maintenance du logiciel. »
> 「将系统化、规范化、可量化的方法应用于软件的开发、运行和维护。」

**三大支柱 / 3 Piliers**：
1. **Théories / 理论** — principes fondamentaux
2. **Méthodes / 方法** — comment faire
3. **Outils / 工具** — support automatisé

---

### 1.6 开发角色 / Rôles dans le Développement

| Rôle / 角色 | Responsabilité / 职责 |
|---|---|
| **Client / 客户** | Besoin d'un produit, paye pour le système / 需要产品，为系统付费 |
| **Manager / 管理者** | Règles et lignes directrices, survie de l'organisation / 制定规则，保障组织 |
| **Ingénieur logiciel / 软件工程师** | Écrit et teste le code / 编写和测试代码 |
| **Utilisateur final / 最终用户** | Feed-back, utilise le système / 提供反馈，实际使用 |

**软件工程师活动链 / Chaîne d'activités**：
```
Spécification → Conception → Implémentation → Intégration → Documentation
→ Vérification → Validation → Déploiement → Maintenance
规格说明 → 设计 → 实现 → 集成 → 文档 → 验证 → 确认 → 部署 → 维护
```

---

### 1.7 道德准则 8 原则 / Code d'Éthique (ACM/IEEE-CS)

| # | Principe | 中文 |
|---|----------|------|
| 1 | Le Public | 公众利益 |
| 2 | Le Client et l'Employeur | 客户与雇主 |
| 3 | Le Produit | 产品标准 |
| 4 | Le Jugement | 专业判断 |
| 5 | La Gestion | 管理 |
| 6 | La Profession | 职业 |
| 7 | Les Collègues | 同事 |
| 8 | Soi-même | 自我 |

---

### 1.8 五种过程模型对比 / Comparaison des 5 Modèles de Processus

| Modèle | Principe | Avantages | Inconvénients |
|--------|----------|-----------|---------------|
| **1. Code-and-Fix** / 无模型 | Coder puis corriger / 编码后修复 | Simple, rapide au début | Impossible à maintenir à grande échelle ; pas de documentation |
| **2. Cascade** / 瀑布模型 | Séquentiel, phases distinctes / 阶段分明顺序执行 | Simple à comprendre ; jalons clairs ; documentation riche | Rigide ; changements difficiles ; ne convient PAS aux exigences incertaines |
| **3. Modèle en V** / V模型 | Orienté tests ; chaque phase a une phase de test correspondante | Tests dès le début ; traçabilité exigences↔tests | Lourd (beaucoup de documentation) ; rigide comme cascade |
| **4. Incrémental** / 增量模型 | Cascade répétée par incréments / 多次瀑布叠加 | Livraisons rapides ; feedback précoce | Problèmes d'architecture si mal planifié |
| **5. DevOps** | Dev + Ops intégrés ; Intégration Continue | Livraison continue ; déploiement automatisé ; très rapide | Complexe à mettre en place ; changement culturel nécessaire |

---

#### 瀑布模型详解 / Cascade en détail

```
① Analyse des besoins (需求分析)
    ↓
② Spécification (规格说明)
    ↓
③ Conception (设计)
    ↓
④ Implémentation (实现)
    ↓
⑤ Tests (测试)
    ↓
⑥ Déploiement (部署)
    ↓
⑦ Maintenance (维护)
```

> Chaque phase doit être **COMPLÈTEMENT terminée** avant de passer à la suivante.
> 每个阶段必须完全完成后才能进入下一阶段。

**何时使用？/ Quand l'utiliser ?**
- ✓ Exigences BIEN DÉFINIES et STABLES / 需求明确且稳定
- ✓ Projets de taille moyenne
- ✓ Équipes expérimentées

---

#### V模型详解 / Modèle en V

```
Analyse besoins ──────────────────────── Tests acceptation
     │                                           ↑
Spécification ───────────────────── Tests système
     │                                           ↑
Conception globale ──────────── Tests intégration
     │                                           ↑
Conception détaillée ─────── Tests unitaires
     │                                           ↑
                   Codage
```

> La traçabilité est **BIDIRECTIONNELLE** — on peut remonter de n'importe quel test vers l'exigence correspondante.

---

#### DevOps 详解

```
Plan → Code → Build → Test → Release → Deploy → Operate → Monitor
 规划    编码    构建    测试    发布     部署     运维      监控
                        ↑_______________________________↓
                               Boucle continue
```

**关键实践 / Pratiques clés**：
- Intégration Continue (CI) / 持续集成
- Livraison Continue (CD) / 持续交付
- Infrastructure as Code (IaC) / 基础设施即代码
- Monitoring et Logging / 监控与日志

---

### ⚠️ 增量 vs 迭代 / Incrémental vs Itératif

| | Incrémental / 增量 | Itératif / 迭代 |
|---|---|---|
| **动作** | On **AJOUTE** des fonctionnalités | On **AMÉLIORE** ce qui existe |
| **结果** | Nouvelles features à chaque cycle | Même feature, version améliorée |

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### 题型一：选择正确的过程模型 / Choisir le bon modèle

**解题步骤 / Méthode**：

| Indice dans l'énoncé / 题干线索 | Modèle recommandé / 推荐模型 |
|---|---|
| « Exigences bien définies et stables » / 需求明确稳定 | **Cascade / 瀑布模型** |
| « Besoin de feedback rapide » / 需要快速反馈 | **Incrémental / 增量模型** |
| « Importance critique des tests » / 测试至关重要 | **Modèle en V / V模型** |
| « Déploiement fréquent, automatisation » / 频繁部署自动化 | **DevOps** |
| « Projet simple à court terme » / 简单短期项目 | **Code-and-Fix** (不推荐！) |

**例题 / Exemple**：
> « Un client a des exigences très claires et ne prévoit pas de changements majeurs. Quel modèle recommandez-vous ? »
> 「客户需求非常明确，预计不会有重大变更。推荐什么模型？」

**✅ 答案**：Modèle en Cascade / 瀑布模型
**理由**：Exigences stables et bien définies → modèle cascade simple et structuré.

---

### 题型二：判断题 / Vrai/Faux

**常见陷阱 / Pièges fréquents**：

| 陈述 | 判断 | 正确理解 |
|------|------|----------|
| « Un logiciel s'use avec le temps » / 软件随时间磨损 | ❌ FAUX | Le logiciel ne s'USE pas, il se **DÉTÉRIORE** par les modifications successives / 软件不会磨损，因多次修改而退化 |
| « L'efficacité est le seul attribut important » / 效率是唯一重要属性 | ❌ FAUX | Les 4 attributs sont TOUS importants |
| « Un programme = un logiciel » / 程序 = 软件 | ❌ FAUX | Logiciel = programmes + doc + config + données + procédures |

---

### 题型三：排序题 / Ordonner les phases

> « Ordonnez les phases de gestion de projet » / 排列项目管理阶段

**✅ 正确顺序**：
1. Étude de faisabilité / 可行性研究
2. Planification / 规划
3. Exécution / 执行
4. Surveillance et contrôle / 监控
5. Clôture / 收尾

> **🧠 口诀**：「可规执监收」/ « Fais Pla Exé Sur Clô »

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### 总结速查表 / Tableau Récapitulatif

| Concept / 概念 | À retenir / 记忆要点 |
|---|---|
| Logiciel / 软件 | ProgrammeS + doc + config + données + procédures |
| 4 Attributs / 四大属性 | **M-FEA** : Maintenabilité, Fiabilité, Efficacité, Acceptabilité |
| Crise du logiciel / 软件危机 | 1968 NATO → naissance du Génie Logiciel |
| 4 Rôles / 四种角色 | Client, Manager, Ingénieur, Utilisateur final |
| 5 Modèles / 五种模型 | Code-and-Fix → Cascade → V → Incrémental → DevOps |
| Cascade / 瀑布 | Séquentiel, exigences STABLES |
| Modèle en V | Tests pour CHAQUE phase de développement |
| Incrémental / 增量 | Livraisons progressives, feedback rapide |
| DevOps | Dev + Ops, CI/CD, livraison continue |

---

### 模型选择决策树 / Arbre de décision

```
Les exigences sont-elles STABLES ?
    ├── OUI → Les tests sont-ils CRITIQUES ?
    │           ├── OUI → Modèle en V
    │           └── NON → Cascade
    └── NON → Le déploiement doit-il être FRÉQUENT ?
                ├── OUI → DevOps
                └── NON → Incrémental ou Agile
```

---

### 自检清单 / Points de Contrôle

- [ ] Définir « logiciel » vs « programme »
- [ ] Citer les 4 attributs d'un bon logiciel (M-FEA)
- [ ] Expliquer la crise du logiciel et sa conséquence (1968)
- [ ] Lister les 4 rôles du développement
- [ ] Décrire les 5 modèles de processus avec avantages/inconvénients
- [ ] Choisir le bon modèle selon le contexte donné
- [ ] Expliquer la différence incrémental vs itératif

---

> 📄 **Fin du Document 1** · Suite → [Document 2 : Méthodes Agile / 敏捷方法](./02_Methodes_Agile.md)
