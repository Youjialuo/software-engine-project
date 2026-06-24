# 软件工程复习文档 2：敏捷方法
# GÉNIE LOGICIEL — Document de Révision 2 : Méthodes Agile

> CY Cergy Paris Université — Dr. Daniela Pamplona, Dr. Fatiha Bousbahi
> **中法双语完整复习 · Révision Bilingue Complète**

---

## 📖 PARTIE 1 — CONNAISSANCES ESSENTIELLES / 第一部分：知识点精讲

---

### 2.1 Le Manifeste Agile / 敏捷宣言

> **FR** : En 2001, 17 experts en développement logiciel se sont réunis à Snowbird (Utah, USA) et ont rédigé le **Manifeste Agile**. Ce document fondateur définit 4 valeurs et 12 principes qui ont révolutionné l'industrie du logiciel. Le manifeste ne REJETTE pas les éléments de droite — il affirme simplement que ceux de gauche ont PLUS de valeur.

> **ZH** : 2001年，17位软件开发专家在美国犹他州Snowbird聚会，撰写了**敏捷宣言**。这份奠基性文件定义了4项价值观和12条原则，彻底改变了软件行业。宣言并不**排斥**右边的事项——只是声明左边的事项**更有价值**。

---

#### Les 4 Valeurs du Manifeste Agile / 敏捷宣言四大价值观

| # | Valeur (FR) | 价值观 (ZH) | Explication (FR) | 解释 (ZH) |
|---|-------------|-------------|-------------------|------------|
| ① | **Les individus et leurs interactions** plutôt que les processus et les outils | **个人与互动** 重于 流程与工具 | La communication humaine est plus importante que de suivre aveuglément une méthodologie. Les meilleurs outils ne remplacent pas une bonne collaboration. | 人与人之间的沟通比盲从方法论更重要。最好的工具也不能替代良好的协作。 |
| ② | **Des logiciels opérationnels** plutôt qu'une documentation exhaustive | **可工作的软件** 重于 详尽的文档 | Le but ultime est de livrer un logiciel qui FONCTIONNE. La documentation est utile mais ne remplace pas un produit qui marche. | 最终目标是交付能**运行**的软件。文档有用但不能替代能工作的产品。 |
| ③ | **La collaboration avec les clients** plutôt que la négociation contractuelle | **客户合作** 重于 合同谈判 | Travailler AVEC le client tout au long du projet, plutôt que de se réfugier derrière un contrat rigide. Le client fait partie de l'équipe. | 在整个项目过程中**与**客户合作，而非躲在僵化的合同后面。客户是团队的一部分。 |
| ④ | **L'adaptation au changement** plutôt que le suivi d'un plan | **响应变化** 重于 遵循计划 | Accepter que les besoins évoluent. Un plan est un guide, pas une prison. La flexibilité est une force. | 接受需求会变化的事实。计划是指导，不是监狱。灵活性是优势。 |

> **⚠️ Piège d'Examen / 考试陷阱** :
> - **FR** : Agile ne dit PAS « pas de documentation » ou « pas de planification » ! Il dit que le logiciel qui fonctionne est PLUS important que la documentation exhaustive. La documentation et la planification restent utiles.
> - **ZH** : 敏捷并**不**说「不要文档」或「不要计划」！它是说可工作的软件比详尽的文档**更重要**。文档和计划仍然有用。

---

#### Les 12 Principes Agile / 敏捷12条原则

> **FR** : Les 12 principes détaillent comment mettre en œuvre les 4 valeurs. Ils sont fréquemment cités à l'examen. Il est recommandé d'en connaître au moins 6 par cœur.

> **ZH** : 12条原则详细说明了如何落实4项价值观。考试中经常被引用。建议至少牢记6条。

| # | Principe (FR) | 原则 (ZH) | Signification (FR) | 含义 (ZH) |
|---|---------------|------------|---------------------|------------|
| 1 | Satisfaire le client par livraison rapide et continue de logiciels utiles | 通过尽早持续交付有价值的软件使客户满意 | La priorité absolue est la satisfaction du client. On livre tôt et souvent. | 最高优先级是让客户满意。尽早并持续交付。 |
| 2 | Accueillir positivement les changements de besoins, même tard dans le développement | 欢迎需求变更，即使是在开发后期 | Les changements sont des OPPORTUNITÉS d'améliorer le produit, pas des problèmes. | 变更是改进产品的**机会**，不是问题。 |
| 3 | Livrer fréquemment un logiciel opérationnel (quelques semaines à quelques mois) | 频繁交付可工作的软件（几周到几个月） | Des cycles courts avec des livraisons concrètes. | 短周期并有具体交付物。 |
| 4 | Coopération quotidienne entre clients et développeurs | 客户与开发者日常合作 | Le client doit être disponible et intégré à l'équipe. | 客户应随时可用并融入团队。 |
| 5 | Construire les projets autour d'individus motivés | 围绕有动力的个人构建项目 | Donner la confiance, les ressources et l'environnement nécessaires. | 给予信任、资源和所需环境。 |
| 6 | Privilégier la conversation en face à face | 面对面交流最有效 | La communication directe est la plus efficace pour transmettre l'information. | 直接交流是传递信息最有效的方式。 |
| 7 | Mesurer l'avancement par le logiciel opérationnel | 可工作的软件是进度的首要衡量标准 | Un logiciel qui fonctionne > un rapport d'avancement. | 能运行的软件 > 进度报告。 |
| 8 | Maintenir un rythme de développement soutenable | 保持可持续的开发节奏 | Pas de crunch permanent. L'équipe doit pouvoir maintenir son rythme indéfiniment. | 不要持续加班。团队应能长期保持节奏。 |
| 9 | Porter une attention continue à l'excellence technique et à la bonne conception | 持续关注技术卓越与良好设计 | Le code propre et bien conçu permet d'aller plus vite à long terme. | 整洁且设计良好的代码从长远来看更快。 |
| 10 | La simplicité — l'art de maximiser la quantité de travail non fait | 简单为本——最大化未完成的工作量 | Ne faire QUE ce qui est nécessaire. Éviter la sur-ingénierie. | 只做必要的事。避免过度工程化。 |
| 11 | Les meilleures architectures émergent d'équipes auto-organisées | 最佳架构源自自组织团队 | Faire confiance à l'équipe pour trouver les meilleures solutions techniques. | 信任团队找到最佳技术方案。 |
| 12 | Réfléchir régulièrement à comment devenir plus efficace | 定期反思如何提高效率 | La rétrospective est essentielle pour l'amélioration continue. | 回顾对于持续改进至关重要。 |

---

### 2.2 Les User Stories / 用户故事

> **FR** : Une User Story est une description SIMPLE d'une fonctionnalité, écrite du point de vue de l'utilisateur. Elle répond à TROIS questions : QUI ? QUOI ? POURQUOI ? C'est l'unité de base du Product Backlog en Scrum.

> **ZH** : 用户故事是从用户视角对功能的**简单**描述。它回答三个问题：**谁**？做**什么**？**为什么**？这是Scrum中Product Backlog的基本单元。

**Format Canonique / 标准格式** :

```
En tant que [profil / 角色], je souhaite [objectif / 目标] afin de [résultat / 结果]
```

| Élément (FR) | 元素 (ZH) | Question |
|---|---|---|
| **Profil / Rôle** | 角色 | QUI utilise cette fonctionnalité ? / 谁使用此功能？ |
| **Objectif** | 目标 | QUOI ? Que veut accomplir l'utilisateur ? / 用户想完成什么？ |
| **Résultat / Bénéfice** | 结果/收益 | POURQUOI ? Quelle valeur cela apporte-t-il ? / 为什么？带来什么价值？ |

**Exemples / 示例** :

> **FR** : « En tant qu'**étudiant**, je souhaite **consulter mes notes en ligne** afin de **suivre ma progression académique**. »
> **ZH** : 「作为**学生**，我想要**在线查看我的成绩**，以便**跟踪我的学业进展**。」

> **FR** : « En tant que **client bancaire**, je souhaite **effectuer un virement** afin de **transférer de l'argent à un tiers**. »
> **ZH** : 「作为**银行客户**，我想要**进行转账**，以便**将资金转移给第三方**。」

**User Story vs Exigence Traditionnelle / 用户故事 vs 传统需求** :

| Critère | User Story | Exigence Traditionnelle / 传统需求 |
|---|---|---|
| **Contenu** | QUOI + POURQUOI (quoi et pourquoi) | QUOI + COMMENT (quoi et comment) |
| **Taille** | Courte (une phrase) / 简短（一句话） | Longue (plusieurs pages) / 详细（多页） |
| **Détail technique** | Volontairement absent / 故意不涉及 | Présent / 包含技术细节 |
| **Outil de** | Conversation avec le client / 与客户对话 | Contrat entre client et fournisseur / 客户与供应商的合同 |

---

### 2.3 XP (eXtreme Programming) / 极限编程

> **FR** : XP est une méthodologie Agile créée par Kent Beck dans les années 1990. Elle pousse les pratiques de développement à l'« extrême » — d'où son nom. XP est particulièrement adaptée aux projets où les exigences changent rapidement.

> **ZH** : XP是Kent Beck在1990年代创建的敏捷方法。它将开发实践推向「极限」——由此得名。XP特别适合需求快速变化的项目。

**Les 3 Piliers d'XP / XP三大支柱** :

| Pilier (FR) / 支柱 (ZH) | Description (FR) | 描述 (ZH) |
|---|---|---|
| **Communication** / 沟通 | Communication fréquente et efficace entre TOUS les acteurs du projet : développeurs, clients, managers. La communication orale est privilégiée. | 项目所有参与者之间的频繁有效沟通：开发者、客户、管理者。口头沟通优先。 |
| **Feedbacks** / 反馈 | Obtenir des retours en TEMPS RÉEL : tests automatisés qui s'exécutent en continu, démonstrations fréquentes au client, intégration continue. | 获取**实时**反馈：持续执行的自动化测试、频繁向客户演示、持续集成。 |
| **Courage** / 勇气 | Avoir le courage de : jeter du code qui ne fonctionne pas, refactoriser sans peur, dire « non » à des demandes irréalistes, accepter les critiques constructives. | 有勇气：抛弃不工作的代码、无畏地重构、对不现实的要求说「不」、接受建设性批评。 |

**Les 12 Pratiques XP / XP十二项实践** :

| # | Pratique (FR) | 实践 (ZH) | Description (FR) / 描述 (ZH) |
|---|---------------|------------|------------------------------|
| 1 | **TDD** (Test-Driven Development) | 测试驱动开发 | **FR** : Écrire le test AVANT le code. Cycle : RED (test échoue) → GREEN (code passe) → REFACTOR. **ZH** : 先写测试再写代码。循环：红（测试失败）→ 绿（代码通过）→ 重构。 |
| 2 | **Jeu du planning** | 计划游戏 | **FR** : L'équipe et le client décident ENSEMBLE des fonctionnalités du prochain incrément. **ZH** : 团队和客户**共同**决定下一个增量的功能。 |
| 3 | **Pair Programming** | 结对编程 | **FR** : Deux développeurs sur UN poste : l'un écrit (driver), l'autre relit et réfléchit (navigator). **ZH** : 两个开发者共用一台电脑：一人写代码（驾驶员），一人审阅思考（导航员）。 |
| 4 | **Refactoring continu** | 持续重构 | **FR** : Améliorer la structure du code SANS changer son comportement externe. Maintenir le code propre en permanence. **ZH** : 改善代码结构但**不改变**其外部行为。持续保持代码整洁。 |
| 5 | **Intégration Continue** | 持续集成 | **FR** : Intégrer le code plusieurs fois par jour. Chaque intégration déclenche des tests automatisés. **ZH** : 每天多次集成代码。每次集成都触发自动化测试。 |
| 6 | **Conception simple** | 简单设计 | **FR** : Faire le PLUS SIMPLE qui fonctionne. Ne pas anticiper des besoins futurs hypothétiques (YAGNI : You Ain't Gonna Need It). **ZH** : 做**最简单**且能工作的方案。不预测假设的未来需求（YAGNI原则）。 |
| 7 | **Rythme soutenable** | 可持续节奏 | **FR** : Pas d'heures supplémentaires excessives. Une équipe fatiguée produit du mauvais code. **ZH** : 不过度加班。疲惫的团队产出低质量代码。 |
| 8 | **Propriété collective** | 集体代码所有权 | **FR** : TOUT le monde peut modifier N'IMPORTE QUELLE partie du code. Pas de « mon code » vs « ton code ». **ZH** : **所有人**都可以修改**任何**代码部分。没有「我的代码」vs「你的代码」。 |
| 9 | **Client sur site** | 现场客户 | **FR** : Un représentant du client est présent avec l'équipe TOUS LES JOURS pour répondre aux questions. **ZH** : 客户代表**每天**与团队一起工作，随时回答问题。 |
| 10 | **Métaphore** | 隐喻 | **FR** : Utiliser un vocabulaire commun et des analogies pour décrire le système (ex : « le panier d'achat » pour un e-commerce). **ZH** : 使用共同词汇和类比描述系统（例：电商的「购物车」）。 |
| 11 | **Standard de codage** | 编码标准 | **FR** : Règles communes de formatage et de nommage pour TOUT le code. Le code doit avoir l'air d'avoir été écrit par une seule personne. **ZH** : 通用格式和命名规范适用于**所有**代码。代码应看起来像一个人写的。 |
| 12 | **Petites livraisons** | 小版本发布 | **FR** : Livrer fréquemment des versions réduites mais UTILES du logiciel. Chaque livraison apporte de la valeur. **ZH** : 频繁交付小而**有用**的软件版本。每次交付都带来价值。 |

---

### 2.4 Scrum / Scrum框架

> **FR** : Scrum est la méthodologie Agile la PLUS utilisée dans l'industrie. Créée par Ken Schwaber et Jeff Sutherland dans les années 1990, elle s'inspire du rugby (la « mêlée » = scrum). Scrum est un CADRE de gestion, pas un ensemble de pratiques techniques.

> **ZH** : Scrum是业界**最**广泛使用的敏捷方法。由Ken Schwaber和Jeff Sutherland在1990年代创建，灵感来自橄榄球（Scrum = 争球）。Scrum是一个**管理框架**，不是一套技术实践。

**Les 3 Piliers de Scrum / Scrum三大支柱** :

| Pilier (FR) / 支柱 (ZH) | Explication (FR) | 解释 (ZH) |
|---|---|---|
| **Transparence** / 透明 | Tous les aspects du processus sont visibles par tous. Rien n'est caché. Le Product Backlog est public pour l'équipe. | 过程的所有方面对所有人可见。没有隐藏。Product Backlog对团队公开。 |
| **Inspection** / 检查 | Inspecter RÉGULIÈREMENT les artefacts Scrum (backlog, incrément) pour détecter les écarts. Daily Scrum, Sprint Review. | **定期**检查Scrum工件（待办列表、增量）以发现偏差。每日站会、Sprint评审会。 |
| **Adaptation** / 适应 | Si l'inspection révèle un problème, on s'ADAPTE immédiatement. Ajuster le plan, les pratiques, la priorité. | 如果检查发现问题，立即**调整**。调整计划、实践、优先级。 |

---

#### Les 3 Rôles Scrum / Scrum三大角色

> **FR** : Scrum définit TROIS rôles, et seulement trois. Chaque rôle a des responsabilités clairement définies. Il n'y a PAS de « chef d'équipe » dans Scrum.

> **ZH** : Scrum定义了**三个**角色，仅此三个。每个角色有明确定义的职责。Scrum中**没有**「团队领导」。

| Rôle (FR) / 角色 (ZH) | Responsabilités (FR) | 职责 (ZH) |
|---|---|---|
| **Product Owner (PO)** / 产品负责人 | **FR** : C'est la VOIX DU CLIENT. Il définit la vision du produit, gère et priorise le Product Backlog. Il est responsable du ROI (retour sur investissement). Il décide CE QUI est développé et dans quel ordre. C'est UNE seule personne, pas un comité. **ZH** : **客户的声音**。定义产品愿景，管理并排序Product Backlog。对ROI（投资回报）负责。决定**什么**被开发以及顺序。**一个人**，不是委员会。 |
| **Scrum Master (SM)** / Scrum主管 | **FR** : C'est un FACILITATEUR, pas un chef. Il protège l'équipe des perturbations extérieures, lève les obstacles (impediments), et s'assure que Scrum est bien compris et appliqué. Il coache l'équipe et l'organisation. **⚠️ Il N'EST PAS responsable des livrables !** **ZH** : **促进者**，不是领导。保护团队免受外部干扰，排除障碍，确保Scrum被正确理解和应用。指导团队和组织。**⚠️ 他不对交付物负责！** |
| **Équipe de Développement** / 开发团队 | **FR** : 5 à 9 personnes, multidisciplinaires, AUTO-ORGANISÉES. L'équipe décide elle-même COMMENT réaliser le travail. Elle est collectivement responsable de la QUALITÉ et des LIVRAISONS. Pas de sous-équipes, pas de titres (pas de « développeur senior », « architecte »...). **ZH** : 5-9人，跨职能，**自组织**。团队自行决定**如何**完成工作。集体对**质量**和**交付**负责。没有子团队，没有头衔（无「高级开发」「架构师」等）。 |

---

#### Les 3 Artefacts Scrum / Scrum三大工件

| Artefact (FR) / 工件 (ZH) | Définition (FR) | 定义 (ZH) | Qui le gère ? |
|---|---|---|---|
| **Product Backlog** / 产品待办列表 | Liste ORDONNÉE et ÉVOLUTIVE de TOUT ce qui est souhaité dans le produit. Contient des User Stories, bugs, tâches techniques. Jamais « complet » — il évolue avec le produit. | 产品中所有期望功能的**有序**且**演进**的列表。包含用户故事、缺陷、技术任务。永远不会「完成」——随产品演进。 | **Product Owner** |
| **Sprint Backlog** / Sprint待办列表 | Sous-ensemble du Product Backlog SÉLECTIONNÉ pour le Sprint en cours, PLUS un plan pour livrer l'incrément. L'équipe s'engage sur ce qu'elle peut faire. | 当前Sprint中**选定**的Product Backlog子集，加上交付增量的计划。团队承诺能完成的部分。 | **Équipe de Développement** |
| **Incrément** / 增量 | Le résultat du Sprint : un logiciel POTENTIELLEMENT LIVRABLE qui s'ajoute aux incréments précédents. Doit répondre à la « Definition of Done » (DoD). | Sprint的产出：**可交付的**软件，叠加到之前的增量上。必须满足「完成定义」(DoD)。 | **Équipe de Développement** |

> **⚠️ Product Backlog vs Sprint Backlog** :
> - **FR** : Product Backlog = liste COMPLÈTE de tout ce qu'on veut. Sprint Backlog = ce qu'on s'engage à faire DANS CE SPRINT.
> - **ZH** : Product Backlog = 所有想要功能的**完整**列表。Sprint Backlog = **本次Sprint**承诺完成的功能。

---

#### Les 4 Événements Scrum / Scrum四大事件

| Événement (FR) / 事件 (ZH) | Durée Max | Objectif (FR) | 目的 (ZH) |
|---|---|---|---|
| **Sprint Planning** / Sprint计划会 | 8h (pour Sprint 1 mois) | Définir CE QUI sera livré et COMMENT. Le PO présente les priorités, l'équipe estime et sélectionne. | 定义**什么**会被交付以及**如何**做。PO展示优先级，团队估算并选择。 |
| **Daily Scrum** / 每日站会 | **15 minutes** | Synchronisation quotidienne. Chaque membre répond : (1) Qu'ai-je fait hier ? (2) Que vais-je faire aujourd'hui ? (3) Quels obstacles ? | 每日同步。每人回答：(1)昨天做了什么？(2)今天要做什么？(3)有什么障碍？ |
| **Sprint Review** / Sprint评审会 | 4h (pour Sprint 1 mois) | Présenter l'incrément aux parties prenantes. Recueillir du feedback. Adapter le Product Backlog si nécessaire. | 向利益相关者展示增量。收集反馈。必要时调整Product Backlog。 |
| **Sprint Retrospective** / Sprint回顾会 | 3h (pour Sprint 1 mois) | L'équipe inspecte SON PROCESSUS : qu'est-ce qui a bien fonctionné ? Qu'est-ce qui peut être amélioré ? Plan d'action pour le prochain Sprint. | 团队检查**自己的过程**：什么做得好？什么可以改进？为下个Sprint制定行动计划。 |

**Le Sprint / 冲刺** :

> **FR** : Un Sprint est une itération de **2 à 4 semaines** pendant laquelle l'équipe crée un incrément de produit. **AUCUN changement** n'est autorisé pendant le Sprint qui pourrait modifier l'objectif du Sprint. Si un changement urgent est nécessaire, le Product Owner peut ANNULER le Sprint (situation exceptionnelle).

> **ZH** : Sprint是一个**2-4周**的迭代周期，团队在此期间创建一个产品增量。Sprint期间**不允许任何**可能改变Sprint目标的变更。如需紧急变更，Product Owner可以**取消**Sprint（特殊情况）。

---

### 2.5 XP vs Scrum / XP vs Scrum对比

| Critère | XP | Scrum |
|---------|-----|-------|
| **Nature** | Pratiques TECHNIQUES / 技术实践 | Cadre de GESTION / 管理框架 |
| **Focus principal** | Comment bien CODER (TDD, Pair Programming, Refactoring) | Comment bien ORGANISER le travail (Backlog, Sprint, Rôles) |
| **Durée d'itération** | 1-2 semaines | Sprint 2-4 semaines |
| **Changements en cours** | Possibles dans l'itération | **INTERDITS** pendant le Sprint |
| **Rôles définis** | Coach, Client sur site | Product Owner, Scrum Master, Équipe |
| **Artefacts** | User Stories, Tests | Product Backlog, Sprint Backlog, Incrément |
| **Utilisation conjointe** | On utilise souvent XP ET Scrum ensemble : Scrum pour la gestion, XP pour les pratiques techniques | |

> **🧠 À Retenir / 记忆要点** : XP = technique (TDD, pair programming...), Scrum = management (backlog, rôles, événements). Ce sont deux méthodologies COMPLÉMENTAIRES — on les combine souvent.

---

## 🧠 PARTIE 2 — MÉTHODES DE RÉSOLUTION / 第二部分：做题思路

---

### Type 1 : QCM sur les Rôles Scrum

| Question (FR) / 问题 (ZH) | ✅ Réponse |
|---|---|
| Qui gère le Product Backlog ? / 谁管理Product Backlog？ | **Product Owner** |
| Qui est responsable de la QUALITÉ des livrables ? / 谁对交付物质量负责？ | **L'Équipe de Développement** (⚠️ PAS le Scrum Master !) |
| Qui lève les obstacles ? / 谁排除障碍？ | **Scrum Master** |
| Qui définit la vision produit ? / 谁定义产品愿景？ | **Product Owner** |
| Combien de personnes dans l'équipe Scrum ? / Scrum团队多少人？ | **5 à 9 personnes** |

---

### Type 2 : Vrai/Faux Agile

| Énoncé (FR) / 陈述 (ZH) | Vrai/Faux | Correction |
|---|---|---|
| « Agile = pas de documentation » / 「敏捷 = 无文档」 | **FAUX** | La documentation a de la valeur, le logiciel qui fonctionne en a PLUS. |
| « Le Scrum Master est le chef d'équipe » / 「Scrum主管是团队领导」 | **FAUX** | C'est un FACILITATEUR, pas un chef. |
| « On peut changer le Sprint Backlog à tout moment » / 「可以随时改变Sprint Backlog」 | **FAUX** | AUCUN changement pendant le Sprint. |
| « Le Daily Scrum dure 30 minutes » / 「每日站会30分钟」 | **FAUX** | 15 minutes MAXIMUM. |
| « Le Sprint dure toujours 2 semaines » / 「Sprint总是2周」 | **FAUX** | 2 à 4 semaines selon l'équipe. |

---

### Type 3 : Écrire une User Story

**Méthode / 方法** :
1. Identifier le **profil** (QUI ?)
2. Identifier l'**objectif** (QUOI ?)
3. Identifier le **résultat** (POURQUOI ?)
4. Formuler : « En tant que [profil], je souhaite [objectif] afin de [résultat] »

> **FR** : « Un bibliothécaire doit pouvoir rechercher des livres pour aider les lecteurs. »
> **✅** : « En tant que **bibliothécaire**, je souhaite **rechercher des livres par titre ou auteur** afin d'**aider les lecteurs à trouver rapidement les ouvrages qu'ils cherchent**. »

---

## 📋 PARTIE 3 — RÉSUMÉ ET FORMULAIRE / 第三部分：方法总结

---

### Scrum en Une Page / Scrum一页纸

```
┌──────────────────────────────────────────────────────────────┐
│                         SCRUM                                │
├────────────────┬──────────────────┬──────────────────────────┤
│ 3 RÔLES        │ 3 ARTEFACTS      │ 4 ÉVÉNEMENTS             │
│ 三种角色        │ 三种工件         │  四种事件                 │
├────────────────┼──────────────────┼──────────────────────────┤
│ Product Owner  │ Product Backlog  │ Sprint Planning (max 8h) │
│ (voix client)  │ (liste complète) │ Sprint计划会             │
│                │                  │                          │
│ Scrum Master   │ Sprint Backlog   │ Daily Scrum (15 min)     │
│ (facilitateur) │ (sélection sprint)│ 每日站会                 │
│                │                  │                          │
│ Équipe (5-9)   │ Incrément        │ Sprint Review (max 4h)   │
│ (auto-organisée)│ (produit sprint) │ Sprint评审会             │
│                │                  │                          │
│                │                  │ Sprint Retro (max 3h)    │
│                │                  │ Sprint回顾会             │
├────────────────┴──────────────────┴──────────────────────────┤
│ SPRINT : 2-4 semaines — AUCUN CHANGEMENT PENDANT LE SPRINT  │
│ Sprint：2-4周 — Sprint期间不允许任何变更                     │
└──────────────────────────────────────────────────────────────┘
```

---

### Checklist d'Auto-Évaluation / 自检清单

| # | Je sais... / 我能... | ✓ |
|---|---|---|
| 1 | Citer les 4 valeurs du Manifeste Agile (FR+ZH) | ☐ |
| 2 | Énumérer au moins 6 des 12 principes Agile | ☐ |
| 3 | Écrire une User Story au format « En tant que... je souhaite... afin de... » | ☐ |
| 4 | Citer les 3 piliers XP (Communication, Feedback, Courage) | ☐ |
| 5 | Lister au moins 8 des 12 pratiques XP | ☐ |
| 6 | Décrire les 3 rôles Scrum et leurs responsabilités | ☐ |
| 7 | Expliquer Product Backlog vs Sprint Backlog | ☐ |
| 8 | Citer les 4 événements Scrum avec leurs durées max | ☐ |
| 9 | Savoir que Sprint = 2-4 semaines, Daily Scrum = 15 min | ☐ |
| 10 | Comparer XP (technique) vs Scrum (gestion) | ☐ |

---

> 📄 **Fin du Document 2** · Suite → [Document 3 : Ingénierie des Exigences](./03_Exigences_Specification.md)
