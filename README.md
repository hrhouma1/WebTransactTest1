# WebTransactTest1

# Plan de Formation Pédagogique : Tests dans une Application Spring Boot (Projet orienté sur le *Gradebook*)

# Objectif Général :
Ce cours est conçu pour initier les étudiants aux tests dans une application Spring Boot, en utilisant un projet de gestion des étudiants et des notes (*Gradebook*). Il s'adresse à des débutants qui n'ont aucune connaissance préalable en tests. Le plan inclut une approche étape par étape pour comprendre les concepts de tests unitaires, d'intégration, et de tests de contrôleurs avec des outils comme **JUnit**, **Mockito**, et **MockMvc**.

# Objectifs d'Apprentissage :
1. Comprendre l'importance des tests automatisés dans un projet Spring Boot.
2. Savoir écrire des tests unitaires pour les différentes couches de l'application (Modèle, Service, Repository, Contrôleur).
3. Utiliser des outils de tests populaires : JUnit, Mockito, et MockMvc.
4. Tester les interactions avec les bases de données via les repositories.
5. Mettre en œuvre des tests complets pour garantir le bon fonctionnement des fonctionnalités du projet.

---

# **Module 1 : Introduction aux Tests Automatisés dans Spring Boot**
**Durée : 2 heures**

#### Objectifs :
- Comprendre ce que sont les tests logiciels et pourquoi ils sont importants.
- Différencier les types de tests : tests unitaires, tests d'intégration, et tests end-to-end (E2E).
- Se familiariser avec les outils : **JUnit**, **Mockito**, et **MockMvc**.

#### Activités :
1. Introduction théorique sur les types de tests.
2. Mise en place du projet dans un IDE (IntelliJ IDEA ou Eclipse).
3. Écrire et exécuter un **test unitaire** simple avec JUnit pour tester les getters et setters de la classe `CollegeStudent`.

#### Exercice Pratique :
- Créez un test JUnit pour vérifier que la méthode `getFullName()` dans la classe `CollegeStudent` retourne correctement le nom complet d'un étudiant.

---

# **Module 2 : Tests Unitaires avec JUnit et Mockito**
**Durée : 3 heures**

#### Objectifs :
- Apprendre à écrire des tests unitaires pour les méthodes des services en utilisant **Mockito** pour simuler les dépendances.
- Tester la logique métier, comme la création d'étudiants (`createStudent`), et la gestion des notes (`createGrade`, `deleteGrade`).

#### Activités :
1. Introduction à **Mockito** pour simuler des comportements (mocks).
2. Écrire des tests pour la classe de service `StudentAndGradeService`.
3. Tester la méthode `createStudent` et vérifier que l'étudiant est bien enregistré dans le système.

#### Exercice Pratique :
- Écrivez des tests unitaires pour :
  - **`createStudent`** : vérifier que la méthode enregistre un étudiant correctement.
  - **`deleteStudent`** : vérifier que la suppression d'un étudiant fonctionne correctement.
  - **`createGrade`** : tester la création de notes (maths, sciences, histoire) pour un étudiant.

---

# **Module 3 : Tests d'Intégration pour les Couches Repository et Service**
**Durée : 4 heures**

#### Objectifs :
- Comprendre les **tests d'intégration** pour s'assurer que les différentes couches de l'application fonctionnent ensemble.
- Tester les interactions avec la base de données à travers les repositories.

#### Activités :
1. Écrire des tests d'intégration pour les DAO (Data Access Object).
2. Tester les méthodes CRUD des repositories (`HistoryGradesDao`, `MathGradesDao`, `ScienceGradesDao`, `StudentDao`).
3. Vérifier que les données sont bien enregistrées et supprimées dans la base.

#### Exercice Pratique :
- **`HistoryGradesDao`** : écrivez des tests pour vérifier que les notes d'histoire peuvent être créées, lues et supprimées.
- **`StudentDao`** : testez la recherche d'un étudiant par son adresse email.

---

# **Module 4 : Tests des Contrôleurs avec MockMvc**
**Durée : 3 heures**

#### Objectifs :
- Tester les **contrôleurs Spring MVC** pour s'assurer que les requêtes HTTP sont bien traitées.
- Utiliser **MockMvc** pour simuler des requêtes HTTP (GET, POST, DELETE) et vérifier les réponses de l'API.

#### Activités :
1. Tester le contrôleur `GradebookController` en simulant des requêtes HTTP.
2. Écrire des tests pour les endpoints du contrôleur : 
   - `/` pour récupérer la liste des étudiants.
   - `/createStudent` pour créer un nouvel étudiant.
   - `/delete/student/{id}` pour supprimer un étudiant.
   - `/grades` pour ajouter des notes.

#### Exercice Pratique :
- Utilisez **MockMvc** pour tester l'endpoint `/studentInformation/{id}` et vérifier que les informations de l'étudiant sont bien retournées.
- Simulez une requête POST pour créer un nouvel étudiant et vérifiez que la réponse contient bien l'étudiant créé.

---

# **Module 5 : Gestion des Cas Particuliers et des Exceptions**
**Durée : 2 heures**

#### Objectifs :
- Apprendre à tester les cas d'erreurs et les exceptions.
- Tester les réponses du système lorsque des erreurs sont introduites (par exemple, supprimer un étudiant qui n'existe pas).

#### Activités :
1. Ajouter des tests pour les cas où un étudiant ou une note n'existent pas.
2. Tester les messages d'erreurs et les pages de réponse lorsqu'une exception est levée.

#### Exercice Pratique :
- Écrivez un test pour la méthode `deleteStudent` avec un ID qui n'existe pas et vérifiez que la réponse est une page d'erreur.

---

# **Module 6 : Tests End-to-End et Automatisation des Tests**
**Durée : 3 heures**

#### Objectifs :
- Comprendre le test complet du système en simulant une interaction complète avec l'application.
- Automatiser les tests pour exécuter les tests automatiquement à chaque changement dans le code.

#### Activités :
1. Écrire des tests **end-to-end** pour valider un scénario complet :
   - Ajouter un étudiant.
   - Ajouter des notes pour cet étudiant.
   - Supprimer une note.
   - Vérifier que toutes les interactions fonctionnent ensemble.

2. Introduction aux **CI/CD pipelines** pour exécuter les tests automatiquement avec **Jenkins** ou **GitHub Actions**.

#### Exercice Pratique :
- Créez un pipeline CI qui exécute tous les tests à chaque changement dans le code.

---

# **Évaluation Finale : Projet de Test Complet**
**Durée : 2 heures**

#### Objectif :
Les étudiants doivent ajouter une nouvelle fonctionnalité au projet *Gradebook* (par exemple, ajouter un calcul de moyenne finale) et écrire des tests unitaires, d'intégration et de contrôleur pour cette nouvelle fonctionnalité.

#### Critères d'Évaluation :
- Qualité des tests écrits.
- Capacité à couvrir tous les scénarios de test (cas positifs et négatifs).
- Automatisation des tests via un pipeline CI.

---

# **Ressources Supplémentaires :**
- Documentation sur **JUnit**, **Mockito**, **Spring Boot Testing**.
- Liens vers des tutoriels vidéo et des articles de blog pour approfondir la compréhension des tests dans Spring Boot.
- Exemples de projets d'entraînement pour appliquer les concepts.

