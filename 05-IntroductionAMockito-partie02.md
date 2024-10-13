# Introduction

- Je vous présente une liste exhaustive des possibilités de tests unitaires que vous pouvez réaliser dans un projet Spring Boot, en particulier avec des contrôleurs, services et l'utilisation de **Mockito** pour simuler les dépendances. 
- Cela couvre plusieurs types de tests pour s'assurer que votre projet est correctement testé.

# Structure générale des tests

Les tests peuvent être classés en différentes catégories :
1. **Tests de contrôleur (Controller Tests)**
2. **Tests de services (Service Tests)**
3. **Tests de repository (Repository Tests)**
4. **Tests de validation (Validation Tests)**
5. **Tests d'intégration (Integration Tests)**

Chaque catégorie peut inclure :
- Tests de cas normaux (Happy Path)
- Tests d'échec (Error Cases)
- Tests de validation des entrées
- Tests de comportement des dépendances (via Mockito)

# 1. **Tests de contrôleur avec Mockito**

Les tests de contrôleur permettent de valider le comportement des endpoints de votre application.

#### Possibilités de tests pour `GradebookController` :

| Scénario de test                                | Commande Maven                                                                  | Explication                                                                                           |
|-------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Créer un étudiant avec des entrées valides      | `mvn -Dtest=GradebookControllerTest#createStudentWithMock test`                  | Simule une requête POST valide pour créer un étudiant avec Mockito pour simuler le service.            |
| Créer un étudiant avec des entrées invalides    | `mvn -Dtest=GradebookControllerTest#createStudentWithInvalidMock test`           | Simule une requête POST avec des données invalides (comme un email vide) pour tester les validations.  |
| Récupérer la liste des étudiants                | `mvn -Dtest=GradebookControllerTest#getStudentsWithMock test`                    | Simule une requête GET pour récupérer la liste des étudiants.                                          |
| Récupérer les informations d'un étudiant        | `mvn -Dtest=GradebookControllerTest#getStudentInfoWithMock test`                 | Simule une requête GET pour récupérer les informations d'un étudiant particulier.                      |
| Supprimer un étudiant                           | `mvn -Dtest=GradebookControllerTest#deleteStudentWithMock test`                  | Simule une requête DELETE pour supprimer un étudiant.                                                  |
| Créer une note pour un étudiant                 | `mvn -Dtest=GradebookControllerTest#createGradeWithMock test`                    | Simule une requête POST pour ajouter une note à un étudiant donné.                                     |
| Tester le cas d'une suppression d'étudiant invalide | `mvn -Dtest=GradebookControllerTest#deleteInvalidStudentWithMock test`           | Simule une suppression d'étudiant avec un ID invalide et vérifie la gestion des erreurs.               |
| Test d'erreur 404 lorsque l'étudiant n'existe pas | `mvn -Dtest=GradebookControllerTest#studentNotFoundError test`                   | Simule une requête GET sur un étudiant inexistant et vérifie le retour d'une erreur 404.               |

#### Tests pour erreurs de validation dans le contrôleur :

| Scénario de test                                | Commande Maven                                                                  | Explication                                                                                           |
|-------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Tester un POST avec des champs manquants        | `mvn -Dtest=GradebookControllerTest#createStudentMissingFields test`             | Simule une requête POST où certains champs sont manquants (comme l'email).                            |
| Tester un POST avec des données non valides     | `mvn -Dtest=GradebookControllerTest#createStudentInvalidEmail test`              | Simule une requête POST avec un email non valide et vérifie la validation.                             |

# 2. **Tests de services avec Mockito**

Les tests de service se concentrent sur la logique métier, en s'assurant que le service fonctionne comme prévu. **Mockito** est utilisé pour simuler les DAO et les autres dépendances.

#### Possibilités de tests pour `StudentAndGradeService` :

| Scénario de test                                  | Commande Maven                                                                  | Explication                                                                                           |
|---------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Créer un étudiant avec des dépendances simulées   | `mvn -Dtest=StudentAndGradeServiceTest#createStudentMock test`                   | Simule la création d’un étudiant via un mock du DAO.                                                   |
| Supprimer un étudiant                             | `mvn -Dtest=StudentAndGradeServiceTest#deleteStudentMock test`                   | Simule la suppression d’un étudiant via un mock du DAO.                                                |
| Récupérer les informations d’un étudiant          | `mvn -Dtest=StudentAndGradeServiceTest#getStudentInfoMock test`                  | Simule la récupération des infos d’un étudiant avec un mock du DAO.                                    |
| Créer une note pour un étudiant                   | `mvn -Dtest=StudentAndGradeServiceTest#createGradeMock test`                     | Simule l’ajout d'une note à un étudiant.                                                              |
| Supprimer une note                                | `mvn -Dtest=StudentAndGradeServiceTest#deleteGradeMock test`                     | Simule la suppression d'une note avec un mock du DAO.                                                  |
| Tester une note avec un étudiant inexistant       | `mvn -Dtest=StudentAndGradeServiceTest#gradeForNonExistingStudent test`          | Teste l'ajout d'une note à un étudiant qui n'existe pas.                                               |
| Tester l'exception lors de la création d'un étudiant | `mvn -Dtest=StudentAndGradeServiceTest#createStudentThrowsException test`        | Simule un comportement où la création d'un étudiant échoue et lance une exception.                     |
| Tester la gestion des exceptions (supprimer une note inexistante) | `mvn -Dtest=StudentAndGradeServiceTest#deleteNonExistingGrade test`            | Vérifie le comportement du service lors de la tentative de suppression d’une note inexistante.         |

# 3. **Tests de repository avec Mockito**

Les tests de repository vérifient le comportement des DAO (Data Access Objects). Vous pouvez utiliser Mockito pour simuler le comportement des couches supérieures.

| Scénario de test                                  | Commande Maven                                                                  | Explication                                                                                           |
|---------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Simuler l'enregistrement d'un étudiant            | `mvn -Dtest=StudentDaoTest#saveStudentMock test`                                 | Simule l'enregistrement d'un étudiant dans la base de données.                                         |
| Simuler la recherche d'un étudiant par email      | `mvn -Dtest=StudentDaoTest#findByEmailMock test`                                 | Simule la recherche d’un étudiant par son email via le DAO.                                            |
| Simuler la suppression d'un étudiant              | `mvn -Dtest=StudentDaoTest#deleteStudentMock test`                               | Simule la suppression d’un étudiant via le DAO.                                                        |

# 4. **Tests de validation**

Les tests de validation s'assurent que les données fournies par l'utilisateur respectent les règles de validation définies (comme les annotations `@NotNull`, `@Size`, etc.).

| Scénario de test                                  | Commande Maven                                                                  | Explication                                                                                           |
|---------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Tester la validation d’un email invalide          | `mvn -Dtest=ValidationTest#invalidEmail test`                                    | Simule l’envoi d’un étudiant avec un email non valide et vérifie que la validation échoue.             |
| Tester la validation de champs vides              | `mvn -Dtest=ValidationTest#emptyFields test`                                     | Simule une requête avec des champs vides et vérifie le message d’erreur de validation.                 |
| Tester la validation d’un nom trop court          | `mvn -Dtest=ValidationTest#invalidNameLength test`                               | Simule la création d’un étudiant avec un nom trop court et vérifie que la validation échoue.           |

# 5. **Tests d'intégration**

Les tests d'intégration valident que tous les composants fonctionnent ensemble, en utilisant une véritable base de données (comme H2 en mémoire pour les tests).

| Scénario de test                                  | Commande Maven                                                                  | Explication                                                                                           |
|---------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Test complet du cycle de vie de l'étudiant        | `mvn -Dtest=IntegrationTest#fullStudentLifecycle test`                           | Teste le cycle complet : créer, lire, mettre à jour, supprimer un étudiant avec une base de données.   |
| Test d'intégration pour la création d'une note    | `mvn -Dtest=IntegrationTest#createGradeIntegration test`                         | Teste l’intégration de la création d’une note dans la base de données.                                |
| Test d'intégration pour la suppression d'un étudiant | `mvn -Dtest=IntegrationTest#deleteStudentIntegration test`                       | Teste la suppression d'un étudiant dans la base de données réelle (H2 en mémoire).                     |

# 6. **Tests d’erreurs avec Mockito (exemples)**
- **Simuler une exception pour tester la gestion des erreurs dans le contrôleur :**
   ```java
   Mockito.when(service.deleteStudent(1)).thenThrow(new RuntimeException("Erreur suppression"));
   ```
   Vous pouvez exécuter ce test avec :
   ```bash
   mvn -Dtest=GradebookControllerTest#deleteStudentErrorMock test
   ```

# Conclusion

- Cette table regroupe les tests possibles avec **Mockito**, les tests d’intégration, les tests de validation et les tests d’erreurs. 
- Utilisez ces commandes pour exécuter les tests correspondants dans votre projet Spring Boot en fonction de ce que vous souhaitez valider. 
- Vous pouvez les adapter à vos besoins pour couvrir le maximum de scénarios possibles. 

