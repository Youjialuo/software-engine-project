# 软件工程复习文档 3：需求工程与规格说明
# GÉNIE LOGICIEL — Document de Révision 3 : Ingénierie des Exigences & Spécification

> CY Cergy Paris Université — Dr. Daniela Pamplona
> **中法双语完整复习 · Révision Bilingue Complète**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

### 3.1 Qu'est-ce qu'une Exigence ? / 什么是需求？

> **FR** : Une exigence (requirement) est une description PRÉCISE de ce que le système DOIT faire — les services qu'il fournit ET les contraintes sous lesquelles il s'exécute. Une exigence doit être OBJECTIVEMENT TESTABLE : on doit pouvoir vérifier sans ambiguïté si elle est satisfaite ou non.

> **ZH** : 需求是对系统**必须**做什么的**精确**描述——它提供的服务以及运行约束条件。需求必须**客观可测试**：必须能够无歧义地验证它是否被满足。

---

#### Objectif vs Exigence / 目标 vs 需求

> **FR** : C'est LA distinction la plus importante de ce chapitre. Un OBJECTIF est une intention générale, vague et NON TESTABLE. Une EXIGENCE est une description précise, mesurable et OBJECTIVEMENT TESTABLE. La transformation d'un objectif en exigence est une étape clé de l'ingénierie des exigences.

> **ZH** : 这是本章**最重要**的区分。目标是模糊且**不可测**的一般性意图。需求是精确、可衡量且**客观可测**的描述。将目标转化为需求是需求工程的关键步骤。

| Critère | Objectif (FR) / 目标 (ZH) | Exigence (FR) / 需求 (ZH) |
|---------|---------------------------|---------------------------|
| **Nature** | Intention générale, vague / 一般性意图，模糊 | Description très précise / 非常精确的描述 |
| **Testabilité** | **NON testable** / 不可测试 | **Objectivement testable** / 客观可测试 |
| **Mesurabilité** | Qualitative / 定性的 | Quantitative / 定量的 |
| **Exemple (FR)** | « Le système doit être facile à utiliser » | « L'utilisateur doit pouvoir effectuer 5 opérations après 2 heures de formation » |
| **Exemple (ZH)** | 「系统应易于使用」 | 「用户经过2小时培训后应能完成5项操作」 |
| **Validation** | Opinion subjective / 主观判断 | Test objectif (réussi/échoué) / 客观测试（通过/失败） |

> **⚠️ Piège d'Examen / 考试陷阱** :
> - **FR** : « Le système doit être rapide » → c'est un OBJECTIF, pas une exigence ! « Rapide » n'est pas quantifié.
> - **ZH** : 「系统要快」→ 这是**目标**，不是需求！「快」没有量化。

---

### 3.2 Classification des Exigences / 需求分类

#### A) Par Niveau / 按层级分类

| Niveau (FR) / 层级 (ZH) | Question | Public Cible |
|---|---|---|
| **Exigences Utilisateur** / 用户需求 | **QUOI** et **POURQUOI** / 做什么、为什么 | Clients, utilisateurs finaux |
| **Exigences Système** / 系统需求 | **COMMENT** le système doit fonctionner / 系统如何运作 | Développeurs, architectes |

#### B) Par Type / 按类型分类

| Type (FR) / 类型 (ZH) | Définition (FR) | 定义 (ZH) | Exemples |
|---|---|---|---|
| **Fonctionnelles** / 功能性需求 | Services que le système DOIT fournir. Décrivent le COMPORTEMENT du système : comment il réagit aux entrées. | 系统**必须**提供的服务。描述系统的**行为**：如何响应输入。 | Calculer la paie, authentifier un utilisateur, envoyer un email |
| **Non Fonctionnelles** / 非功能性需求 | Contraintes sur les services ou fonctions. Décrivent des PROPRIÉTÉS du système (pas des comportements). | 对服务或功能的**约束**。描述系统的**属性**（非行为）。 | Temps de réponse < 2s, disponibilité 99.9%, mot de passe ≥ 8 caractères |

#### Sous-Classification des Exigences Non Fonctionnelles / 非功能性需求子分类

| Sous-Type (FR) / 子类型 (ZH) | Description (FR) | 描述 (ZH) | Exemples |
|---|---|---|---|
| **Produit** / 产品需求 | Propriétés que le logiciel DOIT posséder | 软件必须具备的属性 | Performance, fiabilité, sécurité, utilisabilité |
| **Organisationnelles** / 组织需求 | Contraintes imposées par l'organisation qui développe | 开发组织施加的约束 | Standards de codage, langage imposé, méthode de développement |
| **Externes** / 外部需求 | Contraintes imposées par l'environnement externe | 外部环境施加的约束 | Lois (RGPD), régulations sectorielles, normes éthiques |

> **🎯 Méthode Rapide / 快速判断法** :
> - **FR** : Fonctionnelle = un VERBE d'action que le système fait. Non fonctionnelle = un ADJECTIF ou une MESURE.
> - **ZH** : 功能性 = 系统执行的**动作动词**。非功能性 = **形容词**或**度量**。

---

### 3.3 Le Processus d'Ingénierie des Exigences / 需求工程过程

> **FR** : L'ingénierie des exigences suit un processus en 4 phases. Ce processus n'est PAS linéaire — il y a des itérations et des retours en arrière entre les phases.

> **ZH** : 需求工程遵循4阶段过程。该过程**不是**线性的——阶段之间有迭代和回溯。

| # | Phase (FR) / 阶段 (ZH) | Activités (FR) | 活动 (ZH) | Livrable |
|---|---|---|---|---|
| ① | **Étude de faisabilité** / 可行性研究 | Évaluer si le projet est techniquement possible et économiquement viable. Identifier les risques majeurs. | 评估项目在技术上是否可行、经济上是否合理。识别主要风险。 | Rapport de faisabilité |
| ② | **Élicitation et analyse** / 需求获取与分析 | Découvrir les besoins en consultant les parties prenantes (stakeholders). Techniques : interviews, questionnaires, observation, prototypes. | 通过咨询利益相关者来发现需求。技术：访谈、问卷、观察、原型。 | Liste des besoins bruts |
| ③ | **Spécification** / 规格说明 | Transformer les besoins bruts en un document PRÉCIS et STRUCTURÉ (le DSEL/SRS). | 将原始需求转化为**精确**且**结构化**的文档（DSEL/SRS）。 | Document DSEL / SRS |
| ④ | **Validation** / 验证 | Vérifier la cohérence (pas de contradictions), la complétude (rien n'a été oublié) et la testabilité des exigences. | 验证需求的一致性（无矛盾）、完整性（无遗漏）和可测试性。 | Exigences validées |

> **🧠 Mnémotechnique / 记忆口诀** : « **Fais Éli Spé Vali** » / 「**可获规验**」

---

### 3.4 Les Parties Prenantes (Stakeholders) / 利益相关者

> **FR** : Les stakeholders sont TOUTES les personnes ou organisations qui ont un intérêt dans le projet. Les identifier et les consulter est essentiel car chacun a un point de vue différent sur ce que le système doit faire.

> **ZH** : 利益相关者是所有对项目有利害关系的人或组织。识别并咨询他们至关重要，因为每个人对系统应该做什么有不同的视角。

| Stakeholder (FR) / 利益相关者 (ZH) | Intérêt Principal (FR) | 主要关注点 (ZH) |
|---|---|---|
| **Ingénieurs** / 工程师 | Faisabilité technique, complexité de réalisation | 技术可行性、实现复杂度 |
| **Chefs d'entreprise** / 企业管理者 | ROI, objectifs business, respect du budget | 投资回报、业务目标、预算 |
| **Experts du domaine** / 领域专家 | Règles métier, conformité, bonnes pratiques | 业务规则、合规性、最佳实践 |
| **Utilisateurs finaux** / 最终用户 | Utilisabilité, productivité au quotidien | 可用性、日常工作效率 |

---

### 3.5 Difficultés de l'Élicitation / 需求获取的困难

| Difficulté (FR) | 困难 (ZH) | Impact |
|---|---|---|
| Les stakeholders ne savent **pas ce qu'ils veulent** | 利益相关者**不知道自己要什么** | Exigences floues, changements tardifs |
| **Connaissances implicites** (termes métier) | **隐性知识**（行业术语） | Mauvaise compréhension par les développeurs |
| Exigences **contradictoires** entre stakeholders | 利益相关者之间的**矛盾**需求 | Conflits à résoudre, compromis nécessaires |
| **Changement constant** des exigences | 需求**持续变化** | Dérive du projet (scope creep) |

---

### 3.6 Méthodes de Découverte des Exigences / 需求发现方法

| Méthode (FR) / 方法 (ZH) | Description (FR) | 描述 (ZH) | Quand ? |
|---|---|---|---|
| **Interviews** / 访谈 | Entretiens structurés ou semi-structurés | 结构化或半结构化访谈 | Comprendre les besoins individuels en profondeur |
| **Questionnaires** / 问卷调查 | Collecte d'informations à grande échelle | 大规模信息收集 | Beaucoup d'utilisateurs, questions fermées |
| **Ethnographie** / 民族志 | Observation et immersion dans l'environnement de travail | 在用户工作环境中观察和沉浸 | Comprendre le contexte réel d'utilisation |
| **User Stories** / 用户故事 | Format Agile : « En tant que X, je veux Y afin de Z » | 敏捷格式：作为X，我想要Y以便Z | Projets Agile, besoin de simplicité |
| **Scénarios** / 场景 | Description narrative d'une situation d'utilisation | 使用场景的叙述性描述 | Illustrer des cas concrets |
| **Prototypes** / 原型 | Maquette interactive pour valider les besoins | 交互式模型以验证需求 | Valider des idées avant de coder |

---

### 3.7 Le DSEL / SRS / 软件需求规格说明文档

> **FR** : Le DSEL (Document de Spécification des Exigences Logicielles), ou SRS (Software Requirements Specification) en anglais, est le document OFFICIEL qui décrit ce que le système doit faire. C'est la base du contrat entre le client et le développeur.

> **ZH** : DSEL（软件需求规格说明文档）或SRS，是描述系统必须做什么的**正式**文档。它是客户和开发者之间合同的基础。

| Rôle du DSEL/SRS | FR | ZH |
|---|---|---|
| Base contractuelle | Document de référence en cas de litige | 争议时的参考文档 |
| Guide pour la conception | Les concepteurs s'appuient sur le DSEL | 设计者依据DSEL进行设计 |
| Base pour les tests | Les tests de validation vérifient le DSEL | 验证测试检查DSEL是否被满足 |

---

### 3.8 Étude de Cas : SG-PSP / 案例研究

> **FR** : SG-PSP (Système de Gestion de Patients en Soins Psychiatriques) est un système de gestion de dossiers patients pour un hôpital psychiatrique. Ce cas illustre l'importance des exigences non fonctionnelles, en particulier la SÉCURITÉ et la CONFIDENTIALITÉ.

> **ZH** : SG-PSP（精神病患者护理管理系统）是为精神病院设计的患者档案管理系统。此案例说明了非功能性需求的重要性，特别是**安全性**和**保密性**。

| Aspect | Détail (FR) | 细节 (ZH) |
|--------|-------------|-----------|
| **Objectif** | Générer des informations utiles, fournir des données à jour sur les patients | 生成有用信息，提供最新的患者数据 |
| **Contrainte critique** | **Privacité et sécurité** : les données médicales sont hautement sensibles | **隐私与安全**：医疗数据高度敏感 |
| **Architecture** | Base de données centralisée, accès depuis des PC connectés ou déconnectés | 集中式数据库，支持联网或离线PC访问 |
| **Leçon** | Les exigences non fonctionnelles (sécurité) sont parfois PLUS importantes que les fonctionnelles | 非功能性需求（安全）有时比功能性需求**更重要** |

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Type 1 : Distinguer Objectif vs Exigence

**Méthode / 方法** : Poser la question « Peut-on tester cela OBJECTIVEMENT ? »

| Énoncé | Classification | Raison |
|--------|---------------|--------|
| « Le système doit être convivial » / 系统应友好 | **Objectif** | « Convivial » est subjectif |
| « L'utilisateur doit pouvoir terminer en moins de 3 clics » / 用户应在3次点击内完成 | **Exigence** | Testable et quantifié |
| « Le système doit être sécurisé » / 系统应安全 | **Objectif** | Pas de mesure précise |
| « Le mot de passe doit contenir au moins 8 caractères » / 密码至少8个字符 | **Exigence** | Mesurable et testable |

---

### Type 2 : Classifier Fonctionnelle vs Non Fonctionnelle

| Énoncé (FR) / 陈述 (ZH) | Type |
|---|---|
| « Le système doit calculer le salaire mensuel des employés » / 系统必须计算员工月薪 | **Fonctionnelle** (un service rendu) |
| « Le calcul du salaire doit prendre moins de 2 secondes » / 工资计算必须在2秒内完成 | **Non Fonctionnelle** (performance) |
| « L'utilisateur doit s'authentifier par login et mot de passe » / 用户必须通过账号密码认证 | **Fonctionnelle** |
| « La disponibilité du système doit être de 99,9% » / 系统可用性必须达到99.9% | **Non Fonctionnelle** (fiabilité) |

---

### Type 3 : Ordonner les Phases

> « Ordonnez les phases de l'ingénierie des exigences » / 排列需求工程各阶段

**✅ Ordre** : ① Faisabilité → ② Élicitation → ③ Spécification → ④ Validation

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

### Tableau Récapitulatif / 速查表

| Concept (FR/ ZH) | Points Clés |
|---|---|
| **Objectif vs Exigence** | Vague/non testable vs Précis/testable |
| **Fonctionnelle** | Service fourni (VERBE d'action) |
| **Non Fonctionnelle** | Contrainte (MESURE/ADJECTIF) — Produit, Organisationnelle, Externe |
| **4 Phases** | Faisabilité → Élicitation → Spécification → Validation |
| **6 Méthodes** | Interviews, Questionnaires, Ethnographie, User Stories, Scénarios, Prototypes |
| **DSEL/SRS** | Document officiel, base contractuelle |
| **SG-PSP** | Privacité + Sécurité = exigences non fonctionnelles critiques |

### Checklist d'Auto-Évaluation

| # | Je sais... / 我能... | ✓ |
|---|---|---|
| 1 | Distinguer objectif (vague) et exigence (précise, testable) | ☐ |
| 2 | Classer exigence fonctionnelle vs non fonctionnelle | ☐ |
| 3 | Citer les 3 sous-types d'exigences non fonctionnelles | ☐ |
| 4 | Énumérer les 4 phases dans l'ordre | ☐ |
| 5 | Lister au moins 4 méthodes de découverte | ☐ |
| 6 | Expliquer le rôle du DSEL/SRS | ☐ |
| 7 | Décrire le cas SG-PSP et ses enjeux de sécurité | ☐ |

---

> 📄 **Fin du Document 3** · Suite → [Document 4 : Modélisation UML](./04_UML_Modelisation.md)
