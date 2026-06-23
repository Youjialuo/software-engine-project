# 软件工程复习文档 5：设计模式与架构模式

> **GÉNIE LOGICIEL — Document de Révision 5 : Design Patterns & Architecture Logicielle**
> CY Cergy Paris Université — Dr. Fatiha Bousbahi
> 中法双语完整复习

---

## 📖 第一部分：知识点精讲 / Connaissances Essentielles

---

### 5.1 SOLID 五原则 / Les Principes SOLID

| Lettre | Principe | 中文 | Explication |
|--------|----------|------|-------------|
| **S** | **Responsabilité Unique** (Single Responsibility) | 单一职责 | Une classe ne doit avoir qu'UNE seule raison de changer |
| **O** | **Ouvert/Fermé** (Open/Closed) | 开闭原则 | Ouvert à l'extension, fermé à la modification |
| **L** | **Substitution de Liskov** | 里氏替换 | Une classe dérivée doit pouvoir remplacer sa classe de base |
| **I** | **Ségrégation des Interfaces** | 接口隔离 | Plusieurs interfaces spécifiques > une interface générale |
| **D** | **Inversion de Dépendance** | 依赖倒置 | Dépendre des abstractions, pas des implémentations |

> **🎯 目标 SOLID** : Code plus compréhensible, modulaire, flexible et maintenable.
> 让代码更易理解、更模块化、更灵活、更易维护。

---

### 5.2 设计模式 / Les Patrons de Conception (Design Patterns)

> **Objectif** : Proposer une architecture logicielle pour des logiciels **modulaires, réutilisables, extensibles et maintenables**.
> **目标**：为模块化、可重用、可扩展、可维护的软件提供架构方案。

#### 设计模式三大类 / Les 3 Catégories (GoF)

| Catégorie | 中文 | Rôle | Exemples |
|-----------|------|------|----------|
| **Création** | 创建型 | Gérer la création d'objets | Singleton, Factory, Builder, Prototype |
| **Structure** | 结构型 | Organiser les relations entre classes | Adapter, Decorator, Facade, Composite, Proxy |
| **Comportement** | 行为型 | Gérer les interactions entre objets | Observer, Strategy, Command, State, Template Method |

---

#### 重点模式详解 / Patterns Clés

##### ① Singleton / 单例模式

| Aspect | Détail |
|--------|--------|
| **Type** | Création / 创建型 |
| **But** | Garantir qu'une classe n'a qu'**UNE SEULE instance** + fournir un point d'accès global |
| **Utilisation** | Connexion BD, logger, configuration |
| **Implémentation** | Constructeur privé + méthode `getInstance()` statique |

> **⚠️ Singleton vs Classe statique** :
> | Critère | Singleton | Classe statique |
> |---------|-----------|-----------------|
> | Instance | Une instance (objet) | Pas d'instance (la classe elle-même) |
> | Interface | Peut implémenter une interface | **NE PEUT PAS** implémenter d'interface |
> | Polymorphisme | OUI | NON |
> | Testabilité | Plus facile à mocker | Difficile à mocker |

---

##### ② Factory / 工厂模式

| Aspect | Détail |
|--------|--------|
| **Type** | Création / 创建型 |
| **But** | Déléguer la création d'objets à une classe Factory, sans exposer la logique de création |
| **Avantage** | Découplage entre le code client et les classes concrètes |

---

##### ③ Observer / 观察者模式

| Aspect | Détail |
|--------|--------|
| **Type** | Comportement / 行为型 |
| **But** | Notifier automatiquement des objets dépendants quand un objet change d'état |
| **Principe** | Relation 1-N : un sujet notifie N observateurs |
| **Exemple** | Événements GUI, notifications push, flux RSS |

---

##### ④ Adapter / 适配器模式

| Aspect | Détail |
|--------|--------|
| **Type** | Structure / 结构型 |
| **But** | Convertir l'interface d'une classe en une autre interface attendue par le client |
| **Exemple** | Adaptateur de prise électrique, wrapper d'API legacy |

---

##### ⑤ Decorator / 装饰器模式

| Aspect | Détail |
|--------|--------|
| **Type** | Structure / 结构型 |
| **But** | Ajouter dynamiquement des responsabilités à un objet sans modifier sa structure |
| **Exemple** | Ajouter des filtres à un flux de données (ex: compression, chiffrement) |

---

### 5.3 架构模式 / Patrons d'Architecture

---

#### ① MVC (Modèle-Vue-Contrôleur)

```
┌──────────┐     ┌───────────┐     ┌──────────┐
│  MODÈLE   │ ←── │CONTRÔLEUR │ ──→ │   VUE    │
│  (Données)│     │ (Logique) │     │(Affichage)│
└──────────┘     └───────────┘     └──────────┘
      ↑                                  │
      └──────────────────────────────────┘
```

| Composant | Rôle |
|-----------|------|
| **Modèle** | Gère les données et la logique métier |
| **Vue** | Affiche les données à l'utilisateur |
| **Contrôleur** | Interprète les actions utilisateur, met à jour Modèle et Vue |

> **Avantage** : Séparation des préoccupations → maintenance facile

---

#### ② Architecture en Couches / 分层架构

```
┌─────────────────────┐
│   Présentation      │  ← Interface utilisateur
├─────────────────────┤
│   Logique Métier    │  ← Règles de gestion
├─────────────────────┤
│   Accès aux Données │  ← Persistance (BD)
├─────────────────────┤
│   Base de Données   │  ← Stockage
└─────────────────────┘
```

| Avantage | Inconvénient |
|----------|--------------|
| Chaque couche est indépendante | Performance (traverser toutes les couches) |
| Maintenance et test faciles | Rigidité si trop de couches |

---

#### ③ Client-Serveur / 客户端-服务器

| Caractéristique | Détail |
|-----------------|--------|
| **Principe** | Serveur central fournit des services à N clients |
| **Avantage** | Centralisation des données, scalabilité |
| **Exemple** | Site web, application bancaire |

---

#### ④ Référentiel (Centrée sur les Données) / 数据中心架构

| Caractéristique | Détail |
|-----------------|--------|
| **Principe** | Tous les composants partagent un dépôt central de données |
| **Avantage** | Cohérence des données, partage efficace |
| **Inconvénient** | Le dépôt central est un point unique de défaillance |

---

#### ⑤ Pipe & Filter (Tube & Filtre) / 管道-过滤器

| Caractéristique | Détail |
|-----------------|--------|
| **Principe** | Les données passent par une série de filtres connectés par des tubes |
| **Avantage** | Composition flexible, réutilisabilité des filtres |
| **Exemple** | Compilateurs (lexer → parser → codegen), pipelines Unix (`ls | grep | sort`) |

---

## 🧠 第二部分：做题思路 / Méthodes de Résolution

---

### 题型一：识别设计模式 / Identifier le Pattern

| Énoncé | Pattern |
|--------|---------|
| « Garantir une seule instance d'une classe » | **Singleton** |
| « Créer des objets sans exposer la logique de création » | **Factory** |
| « Notifier automatiquement des objets d'un changement d'état » | **Observer** |
| « Adapter une interface à une autre » | **Adapter** |
| « Ajouter des fonctionnalités sans modifier la classe » | **Decorator** |

**🎯 判断方法**：
- « Un seul » → Singleton
- « Créer sans exposer » → Factory
- « Notifier quand ça change » → Observer
- « Convertir l'interface » → Adapter
- « Ajouter sans modifier » → Decorator

---

### 题型二：选择架构模式 / Choisir le Patron d'Architecture

| Contexte | Architecture recommandée |
|----------|--------------------------|
| Application web interactive | **MVC** |
| Grande application d'entreprise | **Architecture en couches** |
| Service central avec utilisateurs distants | **Client-Serveur** |
| Plusieurs outils partagent des données communes | **Référentiel (centrée données)** |
| Traitement de données par étapes | **Pipe & Filter** |

---

### 题型三：判断题 / Vrai/Faux

| Énoncé | Réponse | Explication |
|--------|---------|-------------|
| « Une classe statique = un Singleton » | ❌ FAUX | Singleton peut implémenter une interface, pas la classe statique |
| « SOLID ne concerne que Java » | ❌ FAUX | SOLID est valable pour TOUS les langages OO |
| « L'architecture MVC mélange données et interface » | ❌ FAUX | MVC les SÉPARE (Modèle ≠ Vue) |
| « Le pattern Observer crée un couplage fort » | ❌ FAUX | Observer crée un couplage FAIBLE (le sujet ne connaît que l'interface) |

---

## 📋 第三部分：方法总结 / Résumé et Formulaire

---

### 设计模式速查 / Référence Design Patterns

| Pattern | Type | Mot-clé | Usage typique |
|---------|------|---------|---------------|
| Singleton | Création | Instance UNIQUE | Logger, Config, Connexion BD |
| Factory | Création | Création déléguée | Création d'objets complexes |
| Observer | Comportement | Notification automatique | GUI events, Pub/Sub |
| Adapter | Structure | Conversion d'interface | Wrapper API legacy |
| Decorator | Structure | Ajout dynamique | Filtres, middlewares |

### 架构模式速查 / Référence Architecture

| Patron | Idée clé | Exemple |
|--------|----------|---------|
| MVC | Séparation Données/Vue/Contrôle | Applications web (Django, Rails, Spring) |
| Couches | Organisation hiérarchique | Applications d'entreprise |
| Client-Serveur | Services centralisés | Web, messagerie |
| Référentiel | Dépôt central partagé | IDE, CMS |
| Pipe & Filter | Flux de données par étapes | Compilateur, Unix pipes |

---

### 自检清单 / Points de Contrôle

- [ ] Citer et expliquer les 5 principes SOLID
- [ ] Classer les design patterns en 3 catégories (Création/Structure/Comportement)
- [ ] Expliquer Singleton vs classe statique (différence clé : interface !)
- [ ] Décrire les patterns : Singleton, Factory, Observer, Adapter, Decorator
- [ ] Lister les 5 architectures : MVC, Couches, Client-Serveur, Référentiel, Pipe&Filter
- [ ] Associer un contexte à l'architecture appropriée
- [ ] Comprendre MVC = Séparation Modèle/Vue/Contrôleur

---

> 📄 **Fin du Document 5** · Suite → [Document 6 : Gestion de Projet & PERT/Gantt](./06_GestionProjet_PERT.md)
