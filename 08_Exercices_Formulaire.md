# 软件工程复习文档 8：全课程习题精讲与公式总汇

> **GÉNIE LOGICIEL — Document de Révision 8 : Exercices Corrigés & Formulaire Complet**
> CY Cergy Paris Université — 中法双语完整复习
> ⚠️ **考前冲刺专用**

---

## 📋 第一部分：公式速查卡 / Formulaire Rapide

---

### 1. 过程模型 / Modèles de Processus

| Modèle | Mot-clé | Quand l'utiliser ? |
|--------|---------|---------------------|
| Code-and-Fix | Pas de structure | Projets simples jetables |
| Cascade | Séquentiel, phases figées | Exigences STABLES et BIEN DÉFINIES |
| Modèle en V | Tests pour chaque phase | Projets où les tests sont CRITIQUES |
| Incrémental | Livraisons progressives | Besoin de feedback RAPIDE |
| DevOps | CI/CD, Dev+Ops | Déploiement FRÉQUENT, automatisation |

---

### 2. 敏捷 / Agile

| Élément | Contenu |
|---------|---------|
| **4 Valeurs** | Individus > Processus, Logiciel > Documentation, Collaboration > Contrat, Changement > Plan |
| **12 Principes** | Satisfaction client, accueillir changements, livraisons fréquentes... |
| **User Story** | « En tant que [X], je souhaite [Y] afin de [Z] » |
| **XP 3 Piliers** | Communication, Feedbacks, Courage |
| **Scrum 3 Rôles** | Product Owner, Scrum Master, Équipe (5-9) |
| **Scrum 3 Artefacts** | Product Backlog, Sprint Backlog, Incrément |
| **Scrum 4 Événements** | Sprint Planning, Daily Scrum (15min), Sprint Review, Rétrospective |
| **Sprint** | 2-4 semaines, **PAS de changement** |

---

### 3. PERT / 项目管理计算

```
┌────────────────────────────────────────────────────────────┐
│ FTO = DTO + Durée                  DTA = FTA − Durée       │
│ Marge Totale = DTA − DTO = FTA − FTO                      │
│ Chemin Critique = Marge Totale = 0                         │
│                                                            │
│ FORWARD (→) : DTO(N) = MAX(FTO(prédécesseurs))            │
│ BACKWARD (←): FTA(N) = MIN(DTA(successeurs))              │
│                                                            │
│ V(G) = E − N + 2              V(G) = P + 1                 │
└────────────────────────────────────────────────────────────┘
```

---

### 4. 需求 / Exigences

| Classification | Critère |
|----------------|---------|
| **Objectif vs Exigence** | Vague/non testable vs Précis/testable |
| **Fonctionnelle** | Service fourni (QUOI) |
| **Non fonctionnelle** | Contrainte (COMMENT) : Produit, Organisationnelle, Externe |
| **4 Phases** | Faisabilité → Élicitation → Spécification → Validation |

---

### 5. UML 关系速查

| Relation | Notation | Mot-clé |
|----------|----------|---------|
| `<<include>>` | Flèche → inclus | **TOUJOURS**, obligatoire |
| `<<extend>>` | Flèche → base | **OPTIONNEL**, point d'extension |
| Généralisation (acteur) | Flèche pleine → parent | Héritage de rôle |
| Généralisation (classe) | Flèche pleine → parent | « est-un » |
| Agrégation | ◇— losange VIDE | « a-un », enfant indépendant |
| Composition | ◆— losange PLEIN | « partie-de », enfant dépendant |
| Association | Ligne simple | Connexion entre classes |
| Dépendance | Flèche pointillée | Usage temporaire |

---

### 6. 多重性 / Multiplicité

| Notation | Signification |
|----------|---------------|
| `1` | Exactement un |
| `0..1` | Zéro ou un |
| `*` ou `0..*` | Zéro ou plusieurs |
| `1..*` | Un ou plusieurs |
| `n..m` | Entre n et m |

---

### 7. 设计模式速查 / Design Patterns

| Pattern | Type | Quand ? |
|---------|------|---------|
| Singleton | Création | Une seule instance (logger, config) |
| Factory | Création | Créer sans exposer la logique |
| Observer | Comportement | Notifier les dépendants d'un changement |
| Adapter | Structure | Convertir une interface en une autre |
| Decorator | Structure | Ajouter des fonctionnalités sans modifier |

---

### 8. 架构模式速查 / Architecture

| Patron | Idée clé |
|--------|----------|
| MVC | Séparation Modèle/Vue/Contrôleur |
| Couches | Hiérarchie Présentation→Métier→Données |
| Client-Serveur | Serveur central + N clients |
| Référentiel | Dépôt central de données partagé |
| Pipe & Filter | Données traversent des filtres en série |

---

### 9. 测试 / Tests

| Niveau | Portée |
|--------|--------|
| Unitaire | Fonction/classe isolée |
| Intégration | Entre modules |
| Système | Application complète |
| Acceptation | Validation métier par le client |

---

## 🧠 第二部分：模拟考试自测题 / QCM d'Entraînement (20 Questions)

---

### Q1. Un logiciel se détériore parce que :
A) Il s'use avec le temps comme le matériel
B) Les utilisateurs l'utilisent mal
C) Les demandes multiples de changement introduisent des erreurs
D) Le matériel devient obsolète

> **✅ C** — Le logiciel ne s'use pas, il se détériore par les modifications successives.

---

### Q2. Quel est le SEUL attribut qui n'est PAS un attribut d'un bon logiciel ?
A) Maintenabilité
B) Efficacité
C) Esthétique
D) Fiabilité

> **✅ C** — Les 4 attributs sont : Maintenabilité, Fiabilité/Sécurité, Efficacité, Acceptabilité. L'esthétique n'en fait pas partie.

---

### Q3. Le modèle en cascade est une approche raisonnable quand :
A) Les exigences sont bien définies
B) Le client veut un feedback rapide
C) Le projet est très complexe
D) Les développeurs sont débutants

> **✅ A** — Cascade convient quand les exigences sont BIEN DÉFINIES et STABLES.

---

### Q4. Dans Scrum, qui est responsable du Product Backlog ?
A) Scrum Master
B) Product Owner
C) Équipe de développement
D) Client

> **✅ B** — Le Product Owner gère le Product Backlog.

---

### Q5. La durée d'un Daily Scrum est de :
A) 5 minutes
B) 15 minutes
C) 30 minutes
D) 1 heure

> **✅ B** — 15 minutes maximum.

---

### Q6. La durée typique d'un Sprint Scrum est de :
A) 1 semaine
B) 2-4 semaines
C) 1-2 mois
D) Variable selon le projet

> **✅ B** — 2 à 4 semaines.

---

### Q7. « Le système doit être rapide » est :
A) Une exigence fonctionnelle
B) Une exigence non fonctionnelle
C) Un objectif (pas une exigence)
D) Une spécification technique

> **✅ C** — « Rapide » est VAGUE et NON TESTABLE → c'est un objectif, pas une exigence.

---

### Q8. Dans un diagramme de cas d'utilisation, `<<include>>` signifie :
A) Optionnel
B) Toujours exécuté
C) Héritage
D) Externe au système

> **✅ B** — `<<include>>` est TOUJOURS exécuté.

---

### Q9. Dans un diagramme de classes, le symbole `#` signifie :
A) Public
B) Privé
C) Protégé
D) Package

> **✅ C** — `#` = Protégé (accessible par la classe et ses classes dérivées).

---

### Q10. La relation « Un dossier contient des documents ; si on supprime le dossier, les documents sont supprimés » est :
A) Association
B) Agrégation
C) Composition
D) Généralisation

> **✅ C** — Composition (losange PLEIN ◆) : lien FORT, l'enfant ne survit pas sans le parent.

---

### Q11. Dans PERT, DTO signifie :
A) Durée totale opérationnelle
B) Début au plus tôt
C) Date de terminaison obligatoire
D) Début de traitement opérationnel

> **✅ B** — DTO = Début au plus tôt (Earliest Start / ES).

---

### Q12. La formule de la marge totale est :
A) DTO − DTA
B) FTO − DTO
C) DTA − DTO
D) FTA + DTO

> **✅ C** — Marge Totale = DTA − DTO = FTA − FTO.

---

### Q13. Le chemin critique est défini par :
A) Le chemin le plus court du réseau
B) Le chemin où la marge totale = 0
C) Le chemin avec le plus de tâches
D) Le chemin le moins risqué

> **✅ B** — Chemin critique = marge totale = 0.

---

### Q14. Dans l'algorithme FORWARD de PERT, on utilise :
A) MIN des FTO des prédécesseurs
B) MAX des FTO des prédécesseurs
C) MIN des DTA des successeurs
D) MAX des DTA des successeurs

> **✅ B** — FORWARD : DTO(N) = MAX(FTO(prédécesseurs)).

---

### Q15. Le pattern Singleton garantit :
A) Une interface unique pour plusieurs classes
B) Une seule instance d'une classe
C) La création d'objets sans `new`
D) La notification automatique des changements

> **✅ B** — Singleton = UNE SEULE instance.

---

### Q16. V(G) = E − N + 2 est utilisé pour :
A) Calculer le coût du projet
B) Mesurer la complexité cyclomatique (tests de chemin)
C) Estimer la durée du projet
D) Calculer la marge totale

> **✅ B** — V(G) = complexité cyclomatique pour les tests de chemin.

---

### Q17. Le pattern MVC sépare :
A) Module, Variable, Constante
B) Modèle, Vue, Contrôleur
C) Main, Virtual, Cloud
D) Méthode, Valeur, Classe

> **✅ B** — MVC = Modèle (données), Vue (affichage), Contrôleur (logique).

---

### Q18. Parmi les suivants, lequel est un test NON fonctionnel ?
A) Test unitaire
B) Test d'intégration
C) Test de performance
D) Test de régression

> **✅ C** — Performance est un test non fonctionnel (ISO 25010).

---

### Q19. La première phase de la gestion de projet est :
A) Planification
B) Exécution
C) Étude de faisabilité
D) Clôture

> **✅ C** — ① Faisabilité → ② Planification → ③ Exécution → ④ Surveillance → ⑤ Clôture.

---

### Q20. Les classes d'équivalence et les valeurs limites sont des méthodes pour :
A) Estimer les coûts
B) Concevoir des cas de test
C) Choisir un modèle de processus
D) Calculer le chemin critique

> **✅ B** — Méthodes de conception de cas de test.

---

## 📋 第三部分：对比汇总表 / Tableaux Comparatifs

---

### 5种过程模型对比

| | Code-and-Fix | Cascade | V | Incrémental | DevOps |
|---|---|---|---|---|---|
| **Structure** | Aucune | Séquentielle | Tests par phase | Cascades répétées | Continue |
| **Exigences** | Changeantes | **Stables** | Stables | Évolutives | Très changeantes |
| **Tests** | Ad hoc | À la fin | **À chaque phase** | Par incrément | Automatisés |
| **Livraison** | Une fois | Une fois | Une fois | **Progressive** | **Continue** |

---

### XP vs Scrum

| Critère | XP | Scrum |
|---------|-----|-------|
| Nature | **Pratiques techniques** | **Cadre de gestion** |
| Focus | Qualité du code | Organisation du projet |
| Itération | 1-2 semaines | 2-4 semaines (Sprint) |
| Changements | Possibles pendant | **INTERDITS** pendant le Sprint |
| Pratiques clés | TDD, Pair Programming, CI | Backlog, Daily Scrum, Rétro |

---

### Include vs Extend

| | `<<include>>` | `<<extend>>` |
|---|---|---|
| Obligation | **TOUJOURS** | **OPTIONNEL** |
| Sens flèche | Cas A → Cas inclus (B) | Cas B → Cas de base (A) |
| Usage | Réutilisabilité | Comportement optionnel |
| Exemple | Payer → Vérifier statut | Consulter jeux → Réserver jeu |

---

### Agrégation vs Composition

| | Agrégation | Composition |
|---|---|---|
| Symbole | ◇ losange **VIDE** | ◆ losange **PLEIN** |
| Force | **FAIBLE** | **FORTE** |
| Relation | « a-un » / 拥有 | « partie-de » / 组成部分 |
| Survie enfant | L'enfant **PEUT** exister seul | L'enfant **NE PEUT PAS** exister seul |
| Exemple | Université ◇— Étudiant | Dossier ◆— Document |

---

### Fonctionnel vs Non Fonctionnel

| | Fonctionnel | Non Fonctionnel |
|---|---|---|
| Question | QUOI ? / 做什么？ | COMMENT ? / 如何做？ |
| Nature | Service rendu | Contrainte sur le service |
| Exemple | Calculer la paie | Temps de réponse < 2s |
| Sous-types | — | Produit, Organisationnel, Externe |

---

## 📋 第四部分：PERT 补充练习解答 / Solution Exercice Supplémentaire

> **Rappel énoncé (Document 6)** :

| Tâche | Durée | Prédécesseurs |
|-------|-------|---------------|
| P | 4 | — |
| Q | 6 | P |
| R | 3 | P |
| S | 2 | Q |
| T | 5 | Q, R |

**Solution** :

**FORWARD** :
```
DTO(P)=0,  FTO(P)=4
DTO(Q)=4,  FTO(Q)=10
DTO(R)=4,  FTO(R)=7
DTO(S)=10, FTO(S)=12
DTO(T)=MAX(10,7)=10, FTO(T)=15
```

**BACKWARD** :
```
FTA(T)=15, DTA(T)=10
FTA(S)=15, DTA(S)=13
FTA(R)=DTA(T)=10, DTA(R)=7
FTA(Q)=MIN(DTA(S),DTA(T))=MIN(13,10)=10, DTA(Q)=4
FTA(P)=MIN(DTA(Q),DTA(R))=MIN(4,7)=4, DTA(P)=0
```

**Marges** :
```
MT(P)=0 → CRITIQUE
MT(Q)=0 → CRITIQUE
MT(R)=7-4=3
MT(S)=13-10=3
MT(T)=0 → CRITIQUE
```

**Chemin critique** : P → Q → T
**Durée totale** : 15 jours

---

## 📋 第五部分：复习时间规划建议 / Planning de Révision

| Jour | Contenu | Documents |
|------|---------|-----------|
| **J1** | 导论 + 过程模型 | Doc 1 |
| **J2** | 敏捷方法 (XP + Scrum) | Doc 2 |
| **J3** | 需求工程 + 规格说明 | Doc 3 |
| **J4** | UML三图 (用例 + 活动 + 类图) | Doc 4 |
| **J5** | 设计模式 + 架构模式 | Doc 5 |
| **J6** | 项目管理 + PERT计算 ⚠️ | Doc 6 |
| **J7** | 代码/版本/测试/收尾 | Doc 7 |
| **J8** | 综合复习 + 自测题 + 公式卡 | Doc 8 |

---

## 🎯 考试核心要点 TOP 10 / Top 10 Essentiel pour l'Examen

| # | Point essentiel | Document |
|---|-----------------|----------|
| 1 | 4 attributs du bon logiciel (**M-FEA**) | Doc 1 |
| 2 | 5 modèles de processus (quand utiliser chacun ?) | Doc 1 |
| 3 | Scrum : 3 rôles, 3 artefacts, 4 événements, Sprint 2-4 sem | Doc 2 |
| 4 | Objectif (vague) vs Exigence (précise/testable) | Doc 3 |
| 5 | UML : Include (toujours) vs Extend (optionnel) | Doc 4 |
| 6 | Agrégation (◇ vide, faible) vs Composition (◆ plein, forte) | Doc 4 |
| 7 | Singleton vs classe statique (différence = interface !) | Doc 5 |
| 8 | **PERT : FORWARD=MAX, BACKWARD=MIN, Marge=DTA−DTO** | Doc 6 |
| 9 | **V(G) = E−N+2 = P+1** | Doc 7 |
| 10 | Pyramide des tests : Unitaire → Intégration → Système → Acceptation | Doc 7 |

---

> 🎉 **Félicitations ! Vous avez terminé la révision complète du cours de Génie Logiciel.**
> 恭喜！你已完成软件工程课程的全面复习。
>
> **BON COURAGE POUR VOS EXAMENS ! 考试加油！ 🍀**
>
> 📂 *Retrouvez tous les documents dans le dossier `review_output/`*

---

> *Fin du Document 8 — Dernier document de la série*
