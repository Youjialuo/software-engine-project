# 软件工程复习文档 2：敏捷方法

> **GÉNIE LOGICIEL — Document de Révision 2 : Méthodes Agile**
> CY Cergy Paris Université — Dr. Daniela Pamplona, Dr. Fatiha Bousbahi
> 中法双语完整复习

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

### 2.1 敏捷宣言 / Le Manifeste Agile

**4 项价值观 / 4 Valeurs**：

| # | Valeur | 价值观 |
|---|--------|--------|
| ① | **Les individus et leurs interactions** plutôt que les processus et les outils | **个人与互动** 重于 流程与工具 |
| ② | **Des logiciels opérationnels** plutôt qu'une documentation exhaustive | **可工作的软件** 重于 详尽的文档 |
| ③ | **La collaboration avec les clients** plutôt que la négociation contractuelle | **客户合作** 重于 合同谈判 |
| ④ | **L'adaptation au changement** plutôt que le suivi d'un plan | **响应变化** 重于 遵循计划 |

> **⚠️ 关键理解**：右边的事项也有价值，但左边的事项**更有价值**。敏捷不是完全抛弃文档和计划！

**12 条原则 / 12 Principes**：

| # | Principe (FR) | 原则 (ZH) |
|---|---------------|------------|
| 1 | Satisfaire le client par livraison rapide et continue | 通过快速持续交付让客户满意 |
| 2 | Accueillir les changements d'exigences, même tardifs | 欢迎需求变更，即使是在后期 |
| 3 | Livrer des logiciels opérationnels fréquemment | 频繁交付可工作的软件 |
| 4 | Coopération quotidienne entre clients et développeurs | 客户与开发者日常合作 |
| 5 | Construire autour d'individus motivés | 围绕有动力的个人构建项目 |
| 6 | Privilégier la conversation en face à face | 面对面交流最有效 |
| 7 | Mesurer le progrès par le logiciel opérationnel | 可工作的软件是进度的首要衡量标准 |
| 8 | Maintenir un rythme de développement soutenable | 保持可持续的开发节奏 |
| 9 | Porter attention à l'excellence technique | 持续关注技术卓越与良好设计 |
| 10 | Simplicité — maximiser le travail non fait | 简单为本——最大化未完成的工作量 |
| 11 | Les meilleures architectures émergent d'équipes auto-organisées | 最佳架构源自自组织团队 |
| 12 | Réflexion régulière sur l'efficacité | 定期反思如何提高效率 |

---

### 2.2 用户故事 / User Stories

**格式 / Format**：
```
En tant que [profil], je souhaite [objectif] afin de [résultat]
作为 [角色]，我想要 [目标]，以便 [结果]
```

**示例 / Exemple**：
```
En tant qu'étudiant, je souhaite consulter mes notes en ligne afin de suivre ma progression.
作为学生，我想要在线查看成绩，以便跟踪我的学习进度。
```

**User Story vs Exigence traditionnelle / 用户故事 vs 传统需求**：
- User Story = **QUOI + POURQUOI** / 是什么 + 为什么（不指定如何实现）
- Exigence traditionnelle = spécification détaillée du **COMMENT** / 详细的如何实现

---

### 2.3 XP (eXtreme Programming) / 极限编程

**3 大支柱 / 3 Piliers**：

| Pilier | 中文 | Description |
|--------|------|-------------|
| **Communication** | 沟通 | Fréquente et efficace entre tous les acteurs |
| **Feedbacks** | 反馈 | Adaptation en temps réel grâce aux retours |
| **Courage** | 勇气 | Revenir sur le travail, accepter les changements |

**12 项实践 / 12 Pratiques XP**：

| # | Pratique | 中文 | Description |
|---|----------|------|-------------|
| 1 | **TDD** (Test-Driven Development) | 测试驱动开发 | Écrire les tests AVANT le code |
| 2 | **Jeu du planning** (Planning Game) | 计划游戏 | Décision des incréments par l'équipe |
| 3 | **Pair programming** | 结对编程 | Deux développeurs sur un même poste |
| 4 | **Refactoring continu** | 持续重构 | Améliorer le code sans changer le comportement |
| 5 | **Intégration continue** | 持续集成 | Intégrer le code plusieurs fois par jour |
| 6 | **Conception simple** | 简单设计 | Faire le plus simple qui fonctionne |
| 7 | **Rythme soutenable** | 可持续节奏 | Pas d'heures supplémentaires excessives |
| 8 | **Propriété collective** | 集体代码所有权 | Tout le monde peut modifier tout le code |
| 9 | **Client sur site** | 现场客户 | Un client disponible avec l'équipe |
| 10 | **Métaphore** | 隐喻 | Vocabulaire commun pour le système |
| 11 | **Standard de codage** | 编码标准 | Règles communes pour tout le code |
| 12 | **Petites livraisons** | 小版本发布 | Livrer fréquemment des versions utiles |

---

### 2.4 Scrum 框架 / Le Framework Scrum

> Scrum est la méthodologie Agile **la plus utilisée** dans l'industrie.
> Scrum 是业界**最广泛使用**的敏捷方法。

**3 大支柱 / 3 Piliers Scrum**：
1. **Transparence / 透明** — Tout le monde voit tout
2. **Inspection / 检查** — Vérifier régulièrement l'avancement
3. **Adaptation / 适应** — Ajuster en fonction des inspections

---

#### Scrum 角色 / Rôles Scrum

| Rôle | 角色 | Responsabilité |
|------|------|----------------|
| **Product Owner (PO)** | 产品负责人 | Voix du client ; vision produit ; gère le Product Backlog ; responsable du ROI |
| **Scrum Master (SM)** | Scrum主管 | Protège l'équipe ; lève les obstacles ; **N'EST PAS responsable des livrables** |
| **Équipe de développement** | 开发团队 | 5-9 personnes ; multidisciplinaire ; autogérée ; responsable qualité et livraisons |

> **⚠️ 考试陷阱**：Le Scrum Master **N'EST PAS** le chef d'équipe ! Il est un facilitateur.
> Scrum主管**不是**团队领导！他是促进者。

---

#### Scrum 工件 / Artefacts Scrum

| Artefact | 中文 | Définition |
|----------|------|------------|
| **Product Backlog** | 产品待办列表 | Liste COMPLÈTE de toutes les fonctionnalités souhaitées / 所有期望功能的完整列表 |
| **Sprint Backlog** | Sprint待办列表 | Sous-ensemble SÉLECTIONNÉ pour le sprint en cours / 当前Sprint选定的功能子集 |
| **Incrément** | 增量 | Produit du sprint — logiciel potentiellement livrable / Sprint的产出——可交付的软件 |

---

#### Scrum 事件 / Événements Scrum

| Événement | 中文 | Durée | Description |
|-----------|------|-------|-------------|
| **Sprint Planning** | Sprint计划会 | Max 8h (Sprint 1 mois) | Planifier le travail du sprint |
| **Daily Scrum** | 每日站会 | **15 min** | Synchronisation quotidienne |
| **Sprint Review** | Sprint评审会 | Max 4h | Présenter l'incrément aux parties prenantes |
| **Sprint Retrospective** | Sprint回顾会 | Max 3h | Amélioration du processus d'équipe |

**Sprint / 冲刺**：
- Durée : **2-4 semaines**
- **PAS de changement** pendant le Sprint !
- À la fin : incrément POTENTIELLEMENT LIVRABLE

---

### 2.5 XP vs Scrum 对比 / XP vs Scrum

| Critère | XP | Scrum |
|---------|-----|-------|
| **Nature** | Pratiques **techniques** / 技术实践 | Cadre de **gestion** / 管理框架 |
| **Itération** | 1-2 semaines | Sprint 2-4 semaines |
| **Changements** | Possibles dans l'itération | **PAS de changement** pendant le sprint |
| **Focus** | Qualité du code (TDD, pair programming...) | Gestion du projet (backlog, rôles...) |
| **Complémentarité** | XP + Scrum = combinaison fréquente ! | |

> **🧠 记忆口诀**：XP = Technique, Scrum = Management. XP peut être utilisé DANS Scrum.

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### 题型一：选择题 — 识别 Scrum 角色

**例题**：
> « Qui est responsable du Product Backlog ? »
> A) Scrum Master  B) Product Owner  C) Équipe de développement  D) Client

**✅ 答案**：**B) Product Owner**
**思路**：PO = voix du client, gère le backlog, responsable ROI.

---

### 题型二：判断题 — 常见陷阱

| 陈述 | 判断 | 纠正 |
|------|------|------|
| « Le Scrum Master est responsable des livrables » | ❌ FAUX | C'est l'**Équipe de développement** qui est responsable des livrables |
| « On peut changer le Sprint Backlog pendant le sprint » | ❌ FAUX | **AUCUN changement** pendant le sprint |
| « Agile = pas de documentation » | ❌ FAUX | La documentation a de la valeur, mais le logiciel opérationnel en a **plus** |
| « Le Daily Scrum dure 30 minutes » | ❌ FAUX | **15 minutes** maximum |

---

### 题型三：User Story 写作题

**方法 / Méthode**：
1. Identifier le **profil** (qui ?)
2. Identifier l'**objectif** (quoi ?)
3. Identifier le **résultat** (pourquoi ?)
4. Formuler : « En tant que [profil], je souhaite [objectif] afin de [résultat] »

**例题**：「一个图书管理员需要能够搜索书籍以帮助读者找到它们。」

**✅ 答案**：
> En tant que **bibliothécaire**, je souhaite **rechercher des livres** afin d'**aider les lecteurs à les trouver**.
> 作为**图书管理员**，我想要**搜索书籍**，以便**帮助读者找到它们**。

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### 速查表 / Aide-mémoire

| Concept | Points clés |
|---------|-------------|
| **Manifeste Agile** | 4 valeurs + 12 principes |
| **User Story** | « En tant que [X], je souhaite [Y] afin de [Z] » |
| **XP** | 3 piliers (Comm/Feedback/Courage) + 12 pratiques |
| **Scrum** | 3 rôles (PO/SM/Équipe) + 3 artefacts + 4 événements |
| **Sprint** | 2-4 semaines, **PAS de changement** |
| **Daily Scrum** | **15 minutes** |
| **Product Backlog** | Liste COMPLÈTE, gérée par le PO |
| **Sprint Backlog** | Sous-ensemble SÉLECTIONNÉ pour le sprint |

---

### Scrum 一页纸总结 / Résumé Scrum en une page

```
┌─────────────────────────────────────────────────────────┐
│                      SCRUM                              │
├───────────────┬─────────────────┬───────────────────────┤
│ 3 RÔLES       │ 3 ARTEFACTS     │ 4 ÉVÉNEMENTS          │
│ 三种角色      │ 三种工件        │ 四种事件              │
├───────────────┼─────────────────┼───────────────────────┤
│ Product Owner │ Product Backlog │ Sprint Planning       │
│ 产品负责人    │ 产品待办列表    │ Sprint计划会          │
│               │                 │                       │
│ Scrum Master  │ Sprint Backlog  │ Daily Scrum (15 min)  │
│ Scrum主管     │ Sprint待办列表  │ 每日站会              │
│               │                 │                       │
│ Équipe (5-9)  │ Incrément       │ Sprint Review         │
│ 开发团队      │ 增量            │ Sprint评审会          │
│               │                 │                       │
│               │                 │ Sprint Retrospective  │
│               │                 │ Sprint回顾会          │
├───────────────┴─────────────────┴───────────────────────┤
│ SPRINT : 2-4 semaines — PAS DE CHANGEMENT               │
└─────────────────────────────────────────────────────────┘
```

---

### 自检清单 / Points de Contrôle

- [ ] Citer les 4 valeurs du Manifeste Agile
- [ ] Énumérer au moins 6 des 12 principes Agile
- [ ] Écrire une User Story au bon format
- [ ] Lister les 3 piliers XP et au moins 6 pratiques
- [ ] Décrire les 3 rôles, 3 artefacts et 4 événements Scrum
- [ ] Expliquer la différence entre Product Backlog et Sprint Backlog
- [ ] Comparer XP vs Scrum
- [ ] Savoir que le Sprint dure 2-4 semaines, Daily Scrum 15 min

---

> 📄 **Fin du Document 2** · Suite → [Document 3 : Ingénierie des Exigences](./03_Exigences_Specification.md)
