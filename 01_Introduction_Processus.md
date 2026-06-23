# 软件工程复习文档 1：导论与过程模型
# GÉNIE LOGICIEL — Document de Révision 1 : Introduction & Modèles de Processus

> CY Cergy Paris Université — Dr. Daniela Pamplona, Dr. Fatiha Bousbahi
> **中法双语完整复习 · Révision Bilingue Complète**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

### 1.1 Qu'est-ce qu'un Logiciel ? / 什么是软件？

> **FR** : Un **programme informatique** est un ensemble d'opérations exécutées automatiquement sur un support informatique (ordinateur, calculatrice, téléphone...). Un **logiciel** (software) est plus large : c'est un ensemble d'instructions ET d'éléments opérationnels — fichiers de configuration, données, procédures automatiques, documentation. Typiquement, un logiciel est composé de plusieurs programmes qui travaillent ensemble.

> **ZH** : **计算机程序**是在计算机载体（电脑、计算器、手机等）上自动执行的一系列操作集合。**软件**的范围更广：它是程序指令集**加上**操作元素——配置文件、数据、自动程序、文档。通常一个软件由多个协同工作的程序组成。

> **🔑 Point Clé / 关键点** :
> - **FR** : Un logiciel N'EST PAS qu'un simple programme. Logiciel = Programmes + Documentation + Configuration + Données + Procédures.
> - **ZH** : 软件不仅仅是程序。软件 = 程序 + 文档 + 配置 + 数据 + 过程。

> **⚠️ Piège d'Examen / 考试陷阱** :
> - **FR** : « Un logiciel = un programme » → **FAUX !** Cette confusion est l'erreur la plus fréquente à l'examen.
> - **ZH** : 「软件 = 程序」→ **错误！** 这是考试中最常见的混淆。

---

### 1.2 Types de Logiciels / 软件类型

#### A) Par Domaine d'Application / 按应用领域

> **FR** : On classe les logiciels selon leur domaine d'utilisation. Chaque type répond à des besoins spécifiques et utilise des technologies adaptées.

> **ZH** : 软件按应用领域分类，每种类型对应特定需求并使用相应的技术。

| Type (FR) / 类型 (ZH) | Description (FR) | 描述 (ZH) |
|---|---|---|
| **Applications métier** / 商业应用 | Logiciels de gestion d'entreprise : ERP, CRM, comptabilité, paie. Ils automatisent les processus métier. | 企业管理软件：ERP、CRM、财务、工资系统。自动化业务流程。 |
| **Logiciels systèmes** / 系统软件 | Systèmes d'exploitation, compilateurs, drivers. Ils gèrent les ressources matérielles et servent de plateforme aux autres logiciels. | 操作系统、编译器、驱动程序。管理硬件资源，为其他软件提供平台。 |
| **Logiciels embarqués** / 嵌入式软件 | Contrôle d'appareils spécifiques : automobile, dispositifs médicaux, objets connectés (IoT). Contraintes temps réel et ressources limitées. | 控制特定设备：汽车电子、医疗设备、物联网。有实时性和资源受限的约束。 |
| **Applications web & mobiles** / 网页与移动应用 | Applications centrées réseau avec base de données intégrée. Architecture client-serveur, accessibles via navigateur ou app store. | 以网络为中心、集成数据库的应用。客户端-服务器架构，通过浏览器或应用商店访问。 |
| **Intelligence Artificielle** / 人工智能 | Machine Learning, Deep Learning, NLP, systèmes experts, vision par ordinateur. Apprennent à partir des données. | 机器学习、深度学习、自然语言处理、专家系统、计算机视觉。从数据中学习。 |

#### B) Par Contrat de Licence / 按许可协议

> **FR** : La licence détermine ce que l'utilisateur a le DROIT de faire avec le logiciel. C'est un contrat juridique, pas technique.

> **ZH** : 许可协议决定了用户对软件的**权利**范围。这是法律合同，而非技术问题。

| Type (FR) / 类型 (ZH) | Définition (FR) | 定义 (ZH) | Exemple |
|---|---|---|---|
| **Propriétaire** / 专有软件 | L'auteur se réserve TOUS les droits de diffusion, modification et utilisation. Le code source n'est PAS accessible. | 作者保留所有分发、修改和使用权。源代码**不公开**。 | Windows, Photoshop, MS Office |
| **Libre** / 自由软件 | 4 libertés fondamentales : (1) exécuter le programme, (2) étudier le code source, (3) redistribuer des copies, (4) modifier et publier les améliorations. | 四大自由：(1)运行程序，(2)研究源代码，(3)再分发副本，(4)修改并发布改进版本。 | Linux, GCC, Firefox, LibreOffice |
| **Gratuit (Freeware)** / 免费软件 | Propriétaire mais GRATUIT. Le code source reste fermé. L'utilisateur n'a pas le droit de modifier le logiciel. | 专有但**免费**。源代码不公开，用户无权修改软件。 | Skype, Adobe Reader, Google Chrome |
| **Partagiciel (Shareware)** / 共享软件 | Diffusion autorisée avec des limitations (période d'essai, fonctionnalités réduites). L'utilisateur paie pour débloquer la version complète. | 允许分发但有限制（试用期、功能缩减）。用户付费解锁完整版。 | WinZip, WinRAR (période d'essai) |

---

### 1.3 Les 4 Attributs d'un Bon Logiciel / 好的软件四大属性

> **FR** : Ces quatre attributs sont FONDAMENTAUX. Tout bon logiciel professionnel doit les satisfaire. Ils sont issus du livre de référence de Ian Sommerville.

> **ZH** : 这四大属性是**基础中的基础**。任何专业的优质软件都必须满足它们。源自 Ian Sommerville 的经典教材。

| # | Attribut (FR) / 属性 (ZH) | Explication (FR) | 解释 (ZH) |
|---|---------------------------|-------------------|------------|
| ① | **Maintenabilité** / 可维护性 | Facilité avec laquelle le logiciel peut être corrigé, adapté et amélioré après sa mise en service. Le coût de maintenance représente souvent plus de 60% du coût total du cycle de vie. | 软件投入使用后，被修正、适配和改进的难易程度。维护成本通常占软件生命周期总成本的60%以上。 |
| ② | **Fiabilité & Sécurité** / 可靠性与安全性 | Le logiciel doit fonctionner sans défaillance et protéger les données contre les accès non autorisés. Un logiciel bancaire qui perd des transactions est inacceptable. | 软件必须无故障运行，并保护数据免受未授权访问。银行软件丢失交易数据是不可接受的。 |
| ③ | **Efficacité** / 效率 | Utilisation optimale des ressources système : CPU, mémoire vive, espace disque, bande passante réseau. Un logiciel ne doit pas gaspiller les ressources. | 优化使用系统资源：CPU、内存、磁盘空间、网络带宽。软件不应浪费资源。 |
| ④ | **Acceptabilité** / 可接受性 | Le logiciel doit être compréhensible, utilisable et compatible avec les autres systèmes que l'utilisateur emploie. L'interface doit être intuitive. | 软件必须可理解、可使用，并与用户使用的其他系统兼容。界面必须直观。 |

> **🧠 Moyen Mnémotechnique / 记忆口诀** :
> - **FR** : Retenez **« M-FEA »** → **M**aintenabilité, **F**iabilité, **E**fficacité, **A**cceptabilité.
> - **ZH** : 记住 **「维可效受」** → 可**维**护性、**可**靠性、**效**率、接**受**性。

---

### 1.4 La Crise du Logiciel / 软件危机

> **FR** : La crise du logiciel est un moment clé de l'histoire de l'informatique. Dans les années 1960, les projets logiciels devenaient de plus en plus complexes, et les méthodes artisanales de programmation ne suffisaient plus. Les conséquences étaient désastreuses.

> **ZH** : 软件危机是计算机历史上的关键时刻。20世纪60年代，软件项目变得越来越复杂，手工作坊式的编程方法已经不够用了，后果是灾难性的。

**Chronologie / 时间线** :

| Année / 年份 | Événement (FR) | 事件 (ZH) |
|---|---|---|
| **1950** | Apparition des premiers langages de programmation de haut niveau (Fortran, COBOL). La programmation devient accessible à plus de monde. | 第一批高级编程语言出现（Fortran, COBOL）。编程变得更加普及。 |
| **1960** | Nouveaux champs d'application : on passe du calcul scientifique à la gestion d'entreprise. Les logiciels deviennent plus complexes. | 新应用领域：从科学计算扩展到企业管理。软件变得更加复杂。 |
| **Fin 1960** | **CRISE DU LOGICIEL** : les projets dépassent systématiquement les délais et les budgets. Les logiciels livrés ne répondent pas aux besoins, sont bourrés de bugs, et impossibles à maintenir. | **软件危机**：项目普遍超期超预算。交付的软件不符合需求、充满缺陷、无法维护。 |
| **1968** | Conférence de l'OTAN à Garmisch (Allemagne). Naissance officielle du terme **« Génie Logiciel »** (Software Engineering). On reconnaît que le développement logiciel doit devenir une discipline d'ingénierie. | 北约在德国Garmisch召开工作会议。**「软件工程」**术语正式诞生。人们认识到软件开发必须成为一门工程学科。 |

> **🔑 Point Clé / 关键点** :
> - **FR** : La crise a démontré que programmer n'est PAS suffisant. Il faut une approche **systématique, disciplinée et quantifiable** — c'est cela, le génie logiciel.
> - **ZH** : 软件危机证明了光会编程是不够的。需要**系统化、规范化、可量化**的方法——这就是软件工程的意义。

---

### 1.5 Définition du Génie Logiciel / 软件工程定义

> **FR** : Selon l'IEEE (Institute of Electrical and Electronics Engineers), le génie logiciel est « l'application d'une approche systématique, disciplinée et quantifiable au développement, à l'exploitation et à la maintenance du logiciel ». Cette définition met l'accent sur trois aspects : **systématique** (on suit une méthode), **disciplinée** (on respecte des règles), et **quantifiable** (on mesure les résultats).

> **ZH** : 根据IEEE（电气电子工程师学会）的定义，软件工程是「将系统化、规范化、可量化的方法应用于软件的开发、运行和维护」。这一定义强调三个方面：**系统化**（遵循方法）、**规范化**（遵守规则）、**可量化**（衡量结果）。

**Les 3 Piliers du Génie Logiciel / 软件工程三大支柱** :

| Pilier (FR) / 支柱 (ZH) | Explication (FR) | 解释 (ZH) |
|---|---|---|
| **Théories** / 理论 | Les principes fondamentaux issus de l'informatique, des mathématiques et de la gestion. Par exemple : la théorie de la complexité algorithmique, les structures de données. | 来自计算机科学、数学和管理学的基本原理。例如：算法复杂度理论、数据结构。 |
| **Méthodes** / 方法 | Les procédures à suivre pour chaque activité : comment analyser les besoins, comment concevoir l'architecture, comment tester le logiciel. Exemple : la méthode Agile Scrum. | 每项活动应遵循的步骤：如何分析需求、如何设计架构、如何测试软件。例：敏捷Scrum方法。 |
| **Outils** / 工具 | Les logiciels qui automatisent les méthodes : IDE (Eclipse, VS Code), gestionnaires de versions (Git), outils de test (JUnit, Selenium), outils de modélisation (StarUML, draw.io). | 自动化方法的软件工具：IDE（Eclipse, VS Code）、版本管理工具（Git）、测试工具（JUnit, Selenium）、建模工具（StarUML, draw.io）。 |

---

### 1.6 Les Rôles dans le Développement Logiciel / 软件开发角色

> **FR** : Un projet logiciel implique plusieurs acteurs, chacun avec des responsabilités distinctes. Il est crucial de comprendre qui fait quoi — c'est une question fréquente à l'examen.

> **ZH** : 软件项目涉及多个参与者，各有不同的职责。理解谁做什么至关重要——这是考试中的常见问题。

| Rôle (FR) / 角色 (ZH) | Responsabilités (FR) | 职责 (ZH) |
|---|---|---|
| **Client** / 客户 | Celui qui a besoin du produit et qui le finance. Il définit les objectifs généraux et valide le produit final. Le client peut être interne (un autre service de l'entreprise) ou externe. | 需要产品并为其付费的人。定义总体目标并验收最终产品。客户可以是内部的（公司其他部门）或外部的。 |
| **Manager** / 管理者 | Définit les règles, les lignes directrices et les contraintes (budget, délais). Sa priorité est la survie économique de l'organisation. Il n'écrit généralement pas de code. | 制定规则、指导方针和约束条件（预算、时间）。首要任务是组织的经济生存。通常不写代码。 |
| **Ingénieur Logiciel** / 软件工程师 | Écrit et teste le code, conçoit l'architecture, documente le système. C'est le producteur technique du logiciel. Doit maîtriser à la fois la théorie et la pratique. | 编写和测试代码，设计架构，编写文档。软件的技术生产者。必须同时掌握理论和实践。 |
| **Utilisateur Final** / 最终用户 | Utilise effectivement le logiciel au quotidien. Fournit le feedback le plus précieux sur l'utilisabilité. Peut être différent du client (ex : le client est la direction, l'utilisateur est l'employé). | 日常实际使用软件的人。提供关于可用性最宝贵的反馈。可能与客户不同（例：客户是管理层，用户是员工）。 |

**Les Activités de l'Ingénieur Logiciel / 软件工程师活动链** :

> **FR** : L'ingénieur logiciel suit un cycle d'activités qui couvre tout le cycle de vie du logiciel. Chaque activité produit un livrable spécifique.

> **ZH** : 软件工程师遵循覆盖软件全生命周期的活动链。每项活动产出特定的交付物。

```
Spécification → Conception → Implémentation → Intégration → Documentation
(规格说明)      (设计)        (实现)           (集成)        (文档)
     ↓
Vérification → Validation → Déploiement → Maintenance
(验证)          (确认)        (部署)         (维护)
```

| Activité (FR) | 中文 | Livrable produit |
|---|---|---|
| **Spécification** | 规格说明 | Document d'exigences (DSEL/SRS) |
| **Conception** | 设计 | Diagrammes UML, architecture |
| **Implémentation** | 实现 | Code source |
| **Intégration** | 集成 | Système assemblé |
| **Documentation** | 文档 | Manuel utilisateur, doc technique |
| **Vérification** | 验证 | Rapports de tests |
| **Validation** | 确认 | PV de recette client |
| **Déploiement** | 部署 | Logiciel en production |
| **Maintenance** | 维护 | Correctifs, mises à jour |

---

### 1.7 Code d'Éthique / 道德准则

> **FR** : L'ACM et l'IEEE-CS ont établi un code d'éthique en 8 principes pour les ingénieurs logiciels. Ces principes guident la conduite professionnelle. Ils peuvent faire l'objet d'une question à l'examen.

> **ZH** : ACM和IEEE-CS为软件工程师制定了8条道德准则。这些准则指导职业行为，可能成为考试题目。

| # | Principe (FR) | 原则 (ZH) | Signification (FR) | 含义 (ZH) |
|---|---------------|------------|---------------------|------------|
| 1 | **Le Public** | 公众利益 | Agir dans l'intérêt du public. Accepter la responsabilité de son travail. | 以公众利益为出发点行事，对自身工作负责。 |
| 2 | **Le Client et l'Employeur** | 客户与雇主 | Agir au mieux de leurs intérêts, dans le respect du public. Être honnête sur ses compétences. | 在尊重公众利益的前提下，最大化客户和雇主的利益。诚实说明自己的能力。 |
| 3 | **Le Produit** | 产品标准 | Assurer la plus haute qualité possible. Respecter les standards professionnels. | 确保产品达到最高质量标准。遵守专业标准。 |
| 4 | **Le Jugement** | 专业判断 | Maintenir l'intégrité et l'indépendance dans son jugement professionnel. Ne pas se laisser influencer indûment. | 保持专业判断的诚信和独立性。不受不当影响。 |
| 5 | **La Gestion** | 管理 | Les managers doivent promouvoir une approche éthique. Ne pas imposer des délais irréalistes qui compromettent la qualité. | 管理者应推行道德方法。不强加损害质量的不现实期限。 |
| 6 | **La Profession** | 职业 | Avancer l'intégrité et la réputation de la profession. Participer aux communautés professionnelles. | 提升职业的诚信和声誉。参与专业社区。 |
| 7 | **Les Collègues** | 同事 | Être juste, solidaire et respectueux envers ses collègues. Partager ses connaissances. | 对同事公平、团结、尊重。分享知识。 |
| 8 | **Soi-même** | 自我 | Participer à l'apprentissage continu tout au long de sa carrière. Se tenir à jour des évolutions technologiques. | 终身学习，持续进修。跟进技术发展。 |

---

### 1.8 Les Modèles de Processus / 过程模型

> **FR** : Un modèle de processus (ou cycle de vie) décrit COMMENT organiser les activités de développement logiciel. Il existe 5 modèles principaux, chacun avec ses forces et faiblesses. Savoir choisir le bon modèle selon le contexte est une compétence clé évaluée à l'examen.

> **ZH** : 过程模型（或生命周期模型）描述了**如何**组织软件开发活动。主要有5种模型，各有优缺点。能根据场景选择正确的模型是考试重点评估的能力。

---

#### Tableau Comparatif des 5 Modèles / 五种模型对比表

| Modèle (FR/ ZH) | Principe (FR) / 原理 (ZH) | Avantages (FR) / 优点 (ZH) | Inconvénients (FR) / 缺点 (ZH) |
|---|---|---|---|
| **1. Code-and-Fix** / 无模型 | **FR** : On code directement, puis on corrige les bugs au fur et à mesure. Aucune planification, aucune spécification. **ZH** : 直接编码，边写边修bug。无计划，无规格说明。 | **FR** : Simple, rapide au début, pas de formalisme. **ZH** : 简单，初期快速，无形式化要求。 | **FR** : Impossible à maintenir à grande échelle. Aucune documentation. Catastrophique pour les projets sérieux. **ZH** : 大规模不可维护。无文档。对严肃项目是灾难。 |
| **2. Cascade** (Waterfall) / 瀑布模型 | **FR** : Phases séquentielles distinctes. Chaque phase doit être TERMINÉE avant de passer à la suivante. Pas de retour en arrière. **ZH** : 阶段分明、顺序执行。每个阶段必须**完全完成**后才能进入下一阶段。不可回溯。 | **FR** : Simple à comprendre. Jalons clairs. Documentation riche. Adapté aux projets avec exigences STABLES. **ZH** : 易于理解。里程碑清晰。文档丰富。适合需求**稳定**的项目。 | **FR** : Très rigide. Le client voit le produit très tard. Ne convient PAS aux projets où les exigences sont incertaines ou changeantes. **ZH** : 非常僵化。客户很晚才能看到产品。**不适合**需求不确定或变化的项目。 |
| **3. Modèle en V** / V模型 | **FR** : Variante du modèle cascade, orientée TESTS. Chaque phase de développement (branche gauche) a une phase de test correspondante (branche droite). **ZH** : 瀑布模型的变体，以**测试**为导向。每个开发阶段（左分支）对应一个测试阶段（右分支）。 | **FR** : Tests planifiés dès le début. Traçabilité exigences ↔ tests. Qualité renforcée. **ZH** : 从开始就规划测试。需求-测试可追溯。质量有保障。 | **FR** : Lourd en documentation. Rigide. Peu adapté aux changements tardifs. **ZH** : 文档负担重。僵化。不适合后期变更。 |
| **4. Incrémental** / 增量模型 | **FR** : On développe le système par incréments successifs. Chaque incrément est une mini-cascade qui ajoute des fonctionnalités. **ZH** : 通过连续增量开发系统。每个增量是一个迷你瀑布，添加新功能。 | **FR** : Livraisons rapides (chaque incrément). Feedback précoce du client. Risques réduits. **ZH** : 快速交付（每个增量）。客户早期反馈。风险降低。 | **FR** : Problèmes d'architecture possibles si mal planifié dès le début. Difficulté à intégrer les incréments. **ZH** : 如果一开始架构规划不好，后续可能出问题。增量集成有难度。 |
| **5. DevOps** | **FR** : Fusionne Développement (Dev) et Opérations (Ops). Intégration et livraison continues (CI/CD). Déploiement automatisé. **ZH** : 融合开发(Dev)和运维(Ops)。持续集成/持续交付(CI/CD)。自动化部署。 | **FR** : Livraison très rapide. Feedback en temps réel. Automatisation complète. Adapté au Cloud. **ZH** : 交付极快。实时反馈。完全自动化。适合云环境。 | **FR** : Complexe à mettre en place. Nécessite un changement culturel important. Investissement initial élevé. **ZH** : 搭建复杂。需要重大文化变革。初始投入高。 |

---

#### Détail du Modèle en Cascade / 瀑布模型详解

> **FR** : Le modèle en cascade (Waterfall) a été proposé par Winston Royce en 1970. C'est le premier modèle formel de processus logiciel. Les phases s'enchaînent de façon strictement séquentielle. Chaque phase produit un document qui doit être validé avant de passer à la suivante.

> **ZH** : 瀑布模型由Winston Royce于1970年提出，是第一个正式的软件过程模型。各阶段严格顺序执行。每阶段产出一个需确认后才能进入下一阶段的文档。

```
① Analyse des besoins / 需求分析
        ↓ (Document de spécification validé)
② Spécification / 规格说明
        ↓ (Spécification fonctionnelle détaillée)
③ Conception / 设计
        ↓ (Architecture et design validés)
④ Implémentation / 实现
        ↓ (Code source)
⑤ Tests / 测试
        ↓ (Rapport de tests)
⑥ Déploiement / 部署
        ↓ (Logiciel en production)
⑦ Maintenance / 维护
```

> **FR** : **Quand utiliser le modèle Cascade ?** Quand les exigences sont **BIEN DÉFINIES et STABLES**. Exemples typiques : systèmes critiques (aéronautique, médical) où les exigences sont validées par des autorités de certification et ne peuvent pas changer en cours de route.

> **ZH** : **何时使用瀑布模型？** 当需求**明确且稳定**时。典型场景：关键系统（航空、医疗），其需求由认证机构确认，开发过程中不可更改。

---

#### Détail du Modèle en V / V模型详解

> **FR** : Le modèle en V met l'accent sur la VÉRIFICATION et la VALIDATION. La branche gauche (descendante) correspond à la décomposition du problème. La branche droite (montante) correspond à la recomposition par les tests.

> **ZH** : V模型强调**验证和确认**。左分支（下降）对应问题分解，右分支（上升）对应通过测试进行重组验证。

```
Branche gauche (Décomposition)          Branche droite (Tests)
────────────────────────────────────────────────────────────────
Analyse des besoins ──────────────────── Tests d'acceptation
        │                                         ↑
Spécification ──────────────────────── Tests système
        │                                         ↑
Conception architecturale ──────── Tests d'intégration
        │                                         ↑
Conception détaillée ────────────── Tests unitaires
        │                                         ↑
                   Codage (Implementation)
```

> **FR** : La **traçabilité est BIDIRECTIONNELLE** : on peut remonter de n'importe quel test vers l'exigence qui l'a motivé, et vice-versa. C'est l'avantage principal du modèle en V.

> **ZH** : **可追溯性是双向的**：可以从任何测试回溯到驱动该测试的需求，反之亦然。这是V模型的主要优势。

---

#### DevOps en Détail / DevOps详解

> **FR** : DevOps n'est pas seulement un modèle de processus, c'est une **culture** qui brise le mur entre les développeurs (qui créent le logiciel) et les opérateurs (qui le font tourner en production).

> **ZH** : DevOps不仅是过程模型，更是一种**文化**，打破开发者（创建软件）和运维人员（在生产环境中运行软件）之间的壁垒。

```
Boucle DevOps infinie / DevOps无限循环 :
  PLAN → CODE → BUILD → TEST → RELEASE → DEPLOY → OPERATE → MONITOR
  规划    编码    构建    测试    发布      部署     运维      监控
    ↑_______________________________________________________________↓
                           (Feedback continu)
```

| Pratique DevOps (FR) / 实践 (ZH) | Description (FR) | 描述 (ZH) |
|---|---|---|
| **Intégration Continue (CI)** / 持续集成 | Chaque modification de code est intégrée et testée automatiquement plusieurs fois par jour. | 每次代码修改在一天内被自动集成和测试多次。 |
| **Livraison Continue (CD)** / 持续交付 | Le logiciel est toujours en état d'être déployé en production. Le déploiement est automatisé. | 软件始终处于可部署到生产环境的状态。部署是自动化的。 |
| **Infrastructure as Code (IaC)** / 基础设施即代码 | Les serveurs et l'infrastructure sont gérés par du code (Terraform, Ansible) plutôt que manuellement. | 服务器和基础设施通过代码（Terraform, Ansible）管理，而非手动操作。 |

---

#### ⚠️ Incrémental vs Itératif / 增量 vs 迭代

> **FR** : Ces deux termes sont souvent confondus mais désignent des approches différentes. L'incrémental AJOUTE des fonctionnalités. L'itératif AMÉLIORE des fonctionnalités existantes.

> **ZH** : 这两个术语经常被混淆，但代表不同的方法。增量是**添加**新功能，迭代是**改进**现有功能。

| | Incrémental (FR) / 增量 (ZH) | Itératif (FR) / 迭代 (ZH) |
|---|---|---|
| **Action** | On AJOUTE de nouvelles fonctionnalités à chaque cycle. / 每个周期添加新功能。 | On AMÉLIORE ce qui existe déjà (raffinement progressif). / 改进已有功能（渐进式细化）。 |
| **Résultat** | Plus de fonctionnalités à chaque incrément. / 每个增量有更多功能。 | Meilleure qualité des mêmes fonctionnalités. / 相同功能的质量提升。 |
| **Analogie** | Construire une maison pièce par pièce. / 逐间建造房屋。 | Rénover une pièce pour la rendre plus belle. / 翻新房间使其更美观。 |

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Type 1 : Choisir le Bon Modèle de Processus / 题型一：选择正确过程模型

**Méthode / 解题方法** :

> **FR** : Lisez attentivement l'énoncé et identifiez les MOTS-CLÉS qui indiquent le modèle approprié. Chaque modèle a ses « signaux » caractéristiques.

> **ZH** : 仔细阅读题干，找出指示合适模型的**关键词**。每种模型都有其特征「信号」。

| Mot-Clé dans l'Énoncé (FR) | 题干关键词 (ZH) | Modèle Recommandé / 推荐模型 |
|---|---|---|
| « exigences bien définies et stables » | 「需求明确且稳定」 | **Cascade** / 瀑布模型 |
| « exigences incertaines », « besoin de feedback rapide » | 「需求不确定」「需要快速反馈」 | **Incrémental** / 增量模型 |
| « tests critiques », « système critique » | 「测试至关重要」「关键系统」 | **Modèle en V** / V模型 |
| « déploiement fréquent », « automatisation », « cloud » | 「频繁部署」「自动化」「云」 | **DevOps** |
| « projet simple et court », « prototype jetable » | 「简单短期项目」「一次性原型」 | **Code-and-Fix** |

**Exercice Type / 典型例题** :

> **FR** : « Une entreprise développe un logiciel de contrôle pour un dispositif médical. Les exigences ont été validées par les autorités de santé et ne peuvent pas changer en cours de développement. Quel modèle de processus recommandez-vous ? Justifiez. »

> **ZH** : 「一家公司开发医疗设备控制软件。需求已经通过卫生部门认证，开发过程中不可更改。推荐什么过程模型？请说明理由。」

**✅ Réponse / 答案** :
- **Modèle en V** (ou Cascade) / V模型（或瀑布模型）
- **Justification (FR)** : Les exigences sont STABLES et VALIDÉES par une autorité externe. Le modèle en V est particulièrement adapté car il garantit la traçabilité et la vérification systématique à chaque niveau — essentiel pour un dispositif médical.
- **理由 (ZH)** : 需求**稳定**且经过外部权威机构**认证**。V模型特别适合，因为它保证每个级别的可追溯性和系统验证——这对医疗设备至关重要。

---

### Type 2 : Vrai/Faux sur les Concepts de Base / 题型二：基础概念判断题

> **FR** : Les questions Vrai/Faux testent votre compréhension des nuances. Voici les pièges les plus fréquents.

> **ZH** : 判断题测试你对细微差别的理解。以下是最常见的陷阱。

| Énoncé (FR) / 陈述 (ZH) | Vrai/Faux | Explication (FR) / 解释 (ZH) |
|---|---|---|
| « Un logiciel s'use avec le temps comme le matériel » / 「软件像硬件一样随时间磨损」 | **FAUX** / 错 | **FR** : Le logiciel ne s'USE pas physiquement. Il se DÉTÉRIORE par les modifications successives qui introduisent des erreurs. C'est une différence fondamentale avec le matériel. **ZH** : 软件不会物理磨损。它是因多次修改引入错误而**退化**。这是与硬件的根本区别。 |
| « Un programme = un logiciel » / 「程序 = 软件」 | **FAUX** / 错 | **FR** : Un logiciel = programmeS + documentation + configuration + données + procédures. Le programme n'est qu'un composant du logiciel. **ZH** : 软件 = 多个程序 + 文档 + 配置 + 数据 + 过程。程序只是软件的组成部分。 |
| « L'efficacité est le seul attribut important » / 「效率是唯一重要的属性」 | **FAUX** / 错 | **FR** : Les 4 attributs (Maintenabilité, Fiabilité, Efficacité, Acceptabilité) sont TOUS importants. Négliger l'un d'eux conduit à un mauvais logiciel. **ZH** : 四大属性（可维护性、可靠性、效率、可接受性）**全部**重要。忽视任何一个都会导致劣质软件。 |
| « Le modèle en cascade permet de revenir facilement en arrière » / 「瀑布模型可以轻松回溯」 | **FAUX** / 错 | **FR** : C'est précisément le contraire. Le modèle cascade est RIGIDE : une fois une phase terminée, on ne revient PAS en arrière. C'est son principal inconvénient. **ZH** : 恰恰相反。瀑布模型是**僵化**的：一个阶段完成后，不能回溯。这是它的主要缺点。 |

---

### Type 3 : Ordonner les Phases / 题型三：排序题

> **FR** : L'examen peut vous demander d'ordonner les phases de gestion de projet. L'ordre est crucial — une erreur d'ordre = 0 point.

> **ZH** : 考试可能要求排列项目管理阶段。顺序至关重要——顺序错了就是0分。

**✅ Ordre Correct / 正确顺序** :

| # | Phase (FR) | 阶段 (ZH) | Activité Principale |
|---|---|---|---|
| ① | Étude de faisabilité | 可行性研究 | Vérifier si le projet est réalisable techniquement et économiquement. |
| ② | Planification | 规划 | Rédiger le plan de projet (SMART, risques, ressources, calendrier). |
| ③ | Exécution | 执行 | Réaliser les livrables. Déléguer les tâches à l'équipe. |
| ④ | Surveillance et contrôle | 监控 | Suivre les indicateurs : temps, coûts, qualité, risques. Ajuster si nécessaire. |
| ⑤ | Clôture | 收尾 | Livrer le produit final. Documenter les leçons apprises. Archiver. |

> **🧠 Moyen Mnémotechnique / 记忆口诀** :
> - **FR** : « **F**ais **P**la **E**xé **S**ur **C**lô » → Faisabilité, Planification, Exécution, Surveillance, Clôture.
> - **ZH** : **「可规执监收」** → 可行性、规划、执行、监控、收尾。

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

---

### Tableau Récapitulatif / 总结速查表

| Concept (FR) / 概念 (ZH) | À Retenir (FR) | 记忆要点 (ZH) |
|---|---|---|
| **Logiciel vs Programme** | Logiciel = Programmes + Documentation + Configuration + Données | 软件 ≠ 程序。软件 = 多程序 + 文档 + 配置 + 数据 |
| **4 Attributs** | **M-FEA** : Maintenabilité, Fiabilité, Efficacité, Acceptabilité | 维可效受：可维护性、可靠性、效率、可接受性 |
| **Crise du Logiciel** | 1968 Conférence OTAN → Naissance du Génie Logiciel | 1968北约会议 → 软件工程诞生 |
| **4 Rôles** | Client, Manager, Ingénieur Logiciel, Utilisateur Final | 客户、管理者、软件工程师、最终用户 |
| **5 Modèles** | Code-and-Fix → Cascade → V → Incrémental → DevOps | 无模型 → 瀑布 → V模型 → 增量 → DevOps |
| **Cascade** | Séquentiel, exigences STABLES, documentation riche | 顺序执行，需求稳定，文档丰富 |
| **Modèle en V** | Tests pour chaque phase, traçabilité bidirectionnelle | 每阶段对应测试，双向可追溯 |
| **Incrémental** | Livraisons progressives, feedback précoce | 渐进交付，早期反馈 |
| **DevOps** | Dev + Ops intégrés, CI/CD, automatisation | 开发运维一体，CI/CD，自动化 |
| **Incrémental vs Itératif** | Incrémental = AJOUTER, Itératif = AMÉLIORER | 增量 = 添加功能，迭代 = 改进功能 |

---

### Arbre de Décision pour Choisir un Modèle / 模型选择决策树

```
Question 1 : Les exigences sont-elles STABLES et bien définies ?
  ├── OUI → Question 2 : Les tests sont-ils CRITIQUES (sécurité, certification) ?
  │           ├── OUI → Modèle en V / V模型
  │           └── NON → Modèle en Cascade / 瀑布模型
  │
  └── NON → Question 3 : Le logiciel doit-il être déployé FRÉQUEMMENT (plusieurs fois par jour) ?
                ├── OUI → DevOps
                └── NON → Incrémental (ou Agile)
```

---

### Checklist d'Auto-Évaluation / 自检清单

| # | Je sais... (FR) | 我能... (ZH) | ✓ |
|---|---|---|---|
| 1 | Définir la différence entre « logiciel » et « programme » | 区分「软件」和「程序」的定义 | ☐ |
| 2 | Citer et expliquer les 4 attributs d'un bon logiciel (M-FEA) | 列举并解释软件的四大属性 | ☐ |
| 3 | Raconter l'histoire de la crise du logiciel (1968 → Génie Logiciel) | 讲述软件危机的历史 | ☐ |
| 4 | Lister les 4 rôles et leurs responsabilités | 列出四种角色及其职责 | ☐ |
| 5 | Décrire les 5 modèles de processus avec avantages/inconvénients | 描述五种过程模型及其优缺点 | ☐ |
| 6 | Choisir le bon modèle selon le contexte d'un projet | 根据项目场景选择正确的模型 | ☐ |
| 7 | Expliquer la différence entre incrémental et itératif | 解释增量和迭代的区别 | ☐ |
| 8 | Citer les 8 principes du code d'éthique | 列举八大道德准则 | ☐ |
| 9 | Expliquer ce qu'est DevOps (CI/CD, IaC) | 解释DevOps的核心概念 | ☐ |
| 10 | Ordonner les 5 phases de gestion de projet | 排列项目管理五阶段 | ☐ |

---

> 📄 **Fin du Document 1** · Suite → [Document 2 : Méthodes Agile / 敏捷方法](./02_Methodes_Agile.md)
> *Dernière mise à jour : 23/06/2026*
