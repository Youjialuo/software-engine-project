# 软件工程复习文档 3：需求工程与规格说明

> **GÉNIE LOGICIEL — Document de Révision 3 : Ingénierie des Exigences & Spécification**
> CY Cergy Paris Université — Dr. Daniela Pamplona
> 中法双语完整复习

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

### 3.1 什么是需求？/ Qu'est-ce qu'une Exigence ?

> **Définition** : Descriptions de ce que le système **DOIT** faire — les services qu'il fournit ET les contraintes sous lesquelles il s'exécutera et sera développé.
> **定义**：系统**必须**做什么的描述——它提供的服务以及运行和开发的约束条件。

---

#### 目标 vs 需求 / Objectif vs Exigence

| Critère | Objectif / 目标 | Exigence / 需求 |
|---------|-----------------|-----------------|
| **Nature** | Intention générale / 一般性意图 | Description très précise / 非常精确的描述 |
| **Testabilité** | **NON testable** / 不可测 | **Objectivement testable** / 客观可测 |
| **Exemple** | « facile d'utilisation » / 「易于使用」 | « pas plus de 4h d'apprentissage » / 「学习时间不超过4小时」 |
| **Mesurabilité** | Vague / 模糊 | Mesurable / 可衡量 |

> **🔑 关键点** : Un objectif est VAGUE et NON TESTABLE. Une exigence est PRÉCISE et OBJECTIVEMENT TESTABLE.
> 目标是模糊且不可测的，需求是精确且客观可测的。

> **⚠️ 考试陷阱** : « Le système doit être rapide » → c'est un OBJECTIF, pas une exigence !
> 「系统要快」→ 这是目标，不是需求！（不够精确）

---

### 3.2 需求分类 / Classification des Exigences

#### A) 按层级 / Par niveau

| Niveau | 中文 | Question répondue |
|--------|------|-------------------|
| **Exigences Utilisateur** | 用户需求 | **QUOI** et **POURQUOI** / 做什么、为什么 |
| **Exigences Système** | 系统需求 | **COMMENT** / 怎么做 |

#### B) 按类型 / Par type

| Type | 中文 | Définition | Exemples |
|------|------|------------|----------|
| **Fonctionnelles** | 功能性需求 | Services que le système doit fournir / 系统必须提供的服务 | Calculer la paie, authentifier l'utilisateur |
| **Non fonctionnelles** | 非功能性需求 | Contraintes sur les services / 对服务的约束 | Temps de réponse < 2s, disponibilité 99.9% |

#### 非功能性需求子分类 / Sous-classification

| Sous-type | 中文 | Exemples |
|-----------|------|----------|
| **Produit** | 产品需求 | Performance, fiabilité, sécurité, utilisabilité |
| **Organisationnelles** | 组织需求 | Standards de codage, procédures, méthodes |
| **Externes** | 外部需求 | Lois, éthique, régulations (ex: RGPD) |

---

### 3.3 需求工程过程 / Processus d'Ingénierie des Exigences

```
① Étude de faisabilité (可行性研究)
    ↓
② Élicitation et analyse (需求获取与分析)
    ↓
③ Spécification (规格说明)
    ↓
④ Validation (验证)
```

#### 各阶段详解 / Détail de chaque phase

| Phase | 中文 | Activités |
|-------|------|-----------|
| **① Faisabilité** | 可行性研究 | Dossier commercial, étendue du système, risques identifiés |
| **② Élicitation** | 需求获取 | Découverte en consultant les **parties prenantes (Stakeholders)** |
| **③ Spécification** | 规格说明 | Production d'un document PRÉCIS (DSEL/SRS) |
| **④ Validation** | 验证 | Vérifier cohérence et complétude des exigences |

---

### 3.4 利益相关者 / Stakeholders / 利益相关者

| Stakeholder | 中文 | Intérêt |
|-------------|------|---------|
| Ingénieurs | 工程师 | Faisabilité technique |
| Chefs d'entreprise | 企业管理者 | ROI, objectifs business |
| Experts du domaine | 领域专家 | Connaissances métier |
| Utilisateurs finaux | 最终用户 | Utilisabilité au quotidien |

---

### 3.5 需求获取的困难 / Difficultés d'Élicitation

| Difficulté | 中文 |
|------------|------|
| Stakeholders ne savent **pas ce qu'ils veulent** | 利益相关者不知道自己要什么 |
| Termes propres, **connaissances implicites** | 专有术语、隐性知识 |
| Exigences **différentes et contradictoires** | 需求不同且矛盾 |
| Priorités différentes selon **points de vue** | 不同视角优先级不同 |
| **Changement constant** des exigences | 需求持续变化 |

---

### 3.6 需求发现方法 / Méthodes de Découverte

| Méthode | 中文 | Description |
|---------|------|-------------|
| **Interviews** | 访谈 | Entretiens structurés avec les stakeholders |
| **Questionnaires** | 问卷调查 | Collecte large d'informations |
| **Ethnographie** | 民族志 | Observation et immersion dans l'environnement |
| **Récits utilisateur (User Stories)** | 用户故事 | Format Agile : « En tant que X, je veux Y afin de Z » |
| **Scénarios** | 场景 | Description de situations d'utilisation |
| **Prototypes** | 原型 | Maquette pour valider les besoins |

---

### 3.7 DSEL / SRS — 软件需求规格说明文档

> **DSEL** = Document de Spécification des Exigences Logicielles
> **SRS** = Software Requirements Specification

**DSEL / SRS 的作用**：
- Document OFFICIEL de ce que le système doit faire
- Base du contrat entre client et développeur
- Référence pour les tests de validation
- 客户与开发者之间的正式合同基础

---

### 3.8 案例研究 / Étude de Cas : SG-PSP

**SG-PSP** = Système de Gestion de Patients en Soins Psychiatriques
精神病患者护理管理系统

| Aspect | Détail |
|--------|--------|
| **Objectifs** | Générer informations utiles, fournir infos à jour sur les patients |
| **Points cruciaux** | **Privacité** et **sécurité** des données patients / 患者数据的隐私与安全 |
| **Architecture** | Base centralisée, accès PC connecté/déconnecté |

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### 题型一：区分目标与需求 / Distinguer Objectif vs Exigence

**方法**：Poser la question « Est-ce TESTABLE objectivement ? »
问自己：「这个描述是否能被客观测试？」

| Énoncé | Classification | Raison |
|--------|---------------|--------|
| « Le système doit être convivial » | ❌ Objectif | « Convivial » est subjectif, non mesurable |
| « L'utilisateur doit pouvoir terminer une tâche en moins de 3 clics » | ✅ Exigence | Mesurable objectivement |
| « Le système doit être rapide » | ❌ Objectif | « Rapide » n'est pas quantifié |
| « Le temps de réponse doit être < 500ms » | ✅ Exigence | Quantifié, testable |

**🎯 转换练习 / Exercice de transformation**：
> Objectif → Exigence :
> 「系统应易于学习」→ « L'utilisateur doit pouvoir réaliser 5 opérations de base après 2h de formation »

---

### 题型二：分类需求 / Classifier les Exigences

**方法**：Fonctionnelle = ce que le système **FAIT** ; Non fonctionnelle = **COMMENT** il le fait.
功能性 = 系统做**什么**；非功能性 = **如何**做。

| Énoncé | Type |
|--------|------|
| « Le système doit calculer le salaire mensuel » | Fonctionnelle (un service) |
| « Le calcul du salaire doit prendre moins de 2 secondes » | Non fonctionnelle (performance) |
| « L'utilisateur doit s'authentifier par mot de passe » | Fonctionnelle |
| « Le mot de passe doit avoir au moins 8 caractères » | Non fonctionnelle (sécurité) |

**🎯 快速判断口诀**：
- 包含动词做某事 → Fonctionnelle / 功能性
- 包含「多久」「多安全」「多快」→ Non fonctionnelle / 非功能性

---

### 题型三：需求工程过程排序

> « Ordonnez les phases du processus d'ingénierie des exigences »

**✅ 正确顺序**：
1. Étude de faisabilité / 可行性研究
2. Élicitation et analyse / 需求获取与分析
3. Spécification / 规格说明
4. Validation / 验证

> **🧠 口诀**：« Fais Éli Spé Vali » / 「可获规验」

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### 速查表 / Aide-mémoire

| Concept | Points clés |
|---------|-------------|
| **Objectif vs Exigence** | Vague/non testable vs Précis/testable |
| **Fonctionnelle** | Service fourni par le système / 系统提供的服务 |
| **Non fonctionnelle** | Performance, fiabilité, sécurité, utilisabilité... |
| **Sous-types NF** | Produit, Organisationnelles, Externes |
| **4 phases** | Faisabilité → Élicitation → Spécification → Validation |
| **6 méthodes découverte** | Interviews, Questionnaires, Ethnographie, User Stories, Scénarios, Prototypes |
| **DSEL/SRS** | Document officiel de spécification |
| **SG-PSP** | Privacité + Sécurité des données patients |

---

### 对比表 / Tableau comparatif

| | Objectif / 目标 | Exigence / 需求 |
|---|---|---|
| Précision | Vague | Précis |
| Testable | NON | OUI |
| Exemple | « facile à utiliser » | « apprentissage < 4h » |

| | Fonctionnelle | Non fonctionnelle |
|---|---|---|
| Question | QUOI ? / 做什么？ | COMMENT ? / 如何做？ |
| Exemple | Calculer la paie | Temps de réponse < 2s |

---

### 自检清单 / Points de Contrôle

- [ ] Distinguer objectif et exigence (testable ou non ?)
- [ ] Classer une exigence en fonctionnelle vs non fonctionnelle
- [ ] Citer les 3 sous-types d'exigences non fonctionnelles
- [ ] Énumérer les 4 phases de l'ingénierie des exigences dans l'ordre
- [ ] Lister au moins 4 méthodes de découverte des exigences
- [ ] Expliquer ce qu'est un DSEL/SRS
- [ ] Décrire l'étude de cas SG-PSP et ses enjeux

---

> 📄 **Fin du Document 3** · Suite → [Document 4 : Modélisation UML](./04_UML_Modelisation.md)
