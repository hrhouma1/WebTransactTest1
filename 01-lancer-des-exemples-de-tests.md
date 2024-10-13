# Objectif :

- Tester les différents types de tests dans le cadre du projet que nous utilions. 
- Chaque section inclut des exemples concrets et des scénarios basés sur le projet ci-dessus.

---

# 1. **JUnit (Tests unitaires de base)**

```plaintext
+-----------------------------------------------+
|          JUnit - Tests unitaires de base      |
+-----------------------------------------------+
| Scénario de test                | Commande Maven                          |
+-----------------------------------------------+
| Tester le nom complet           | mvn -Dtest=CollegeStudentTest#testFullName test |
| Tester l'adresse e-mail         | mvn -Dtest=CollegeStudentTest#testEmailAddress test |
| Tester le calcul des notes      | mvn -Dtest=StudentGradesTest#calculateAverage test |
| Tester l'identifiant d'étudiant | mvn -Dtest=CollegeStudentTest#testId test |
+-----------------------------------------------+
```

---

# 2. **Mockito (Tests avec simulation des dépendances)**

```plaintext
+-------------------------------------------------+
|    Mockito - Simulation des dépendances         |
+-------------------------------------------------+
| Scénario de test                 | Commande Maven                                 |
+-------------------------------------------------+
| Créer un étudiant avec un mock   | mvn -Dtest=StudentAndGradeServiceTest#createStudentMock test |
| Supprimer un étudiant avec un mock | mvn -Dtest=StudentAndGradeServiceTest#deleteStudentMock test |
| Ajouter une note avec un mock    | mvn -Dtest=StudentAndGradeServiceTest#createGradeMock test |
| Supprimer une note avec un mock  | mvn -Dtest=StudentAndGradeServiceTest#deleteGradeMock test |
| Simuler une exception            | mvn -Dtest=StudentAndGradeServiceTest#createStudentThrowsException test |
+-------------------------------------------------+
```

---

# 3. **Tests d'intégration (Integration Tests)**

```plaintext
+-------------------------------------------------+
|          Tests d'intégration avec H2            |
+-------------------------------------------------+
| Scénario de test               | Commande Maven                                  |
+-------------------------------------------------+
| Cycle de vie complet d'étudiant| mvn -Dtest=IntegrationTest#fullStudentLifecycle test |
| Créer une note                 | mvn -Dtest=IntegrationTest#createGradeIntegration test |
| Supprimer un étudiant          | mvn -Dtest=IntegrationTest#deleteStudentIntegration test |
+-------------------------------------------------+
```

---

# 4. **Spring Boot Test (Tests de contrôleur et tests d'intégration)**

```plaintext
+-----------------------------------------------------+
|       Spring Boot Test avec MockMvc                 |
+-----------------------------------------------------+
| Scénario de test                    | Commande Maven                                |
+-----------------------------------------------------+
| Créer un étudiant (MockMvc)          | mvn -Dtest=GradebookControllerTest#createStudentWithMock test |
| Récupérer la liste des étudiants     | mvn -Dtest=GradebookControllerTest#getStudentsWithMock test |
| Supprimer un étudiant (MockMvc)      | mvn -Dtest=GradebookControllerTest#deleteStudentWithMock test |
| Tester l'erreur 404 étudiant inexistant | mvn -Dtest=GradebookControllerTest#studentNotFoundError test |
+-----------------------------------------------------+
```

---

# 5. **Tests de validation (Validation Tests)**

```plaintext
+-------------------------------------------------------+
|        Tests de validation (Email, Champs vides)      |
+-------------------------------------------------------+
| Scénario de test                    | Commande Maven                                  |
+-------------------------------------------------------+
| Email invalide                      | mvn -Dtest=ValidationTest#invalidEmail test     |
| Champs vides                        | mvn -Dtest=ValidationTest#emptyFields test      |
| Nom trop court                      | mvn -Dtest=ValidationTest#invalidNameLength test|
+-------------------------------------------------------+
```

---

# 6. **Tests d'exception (Exception Testing)**

```plaintext
+-------------------------------------------------------+
|           Tests d'exception avec Mockito              |
+-------------------------------------------------------+
| Scénario de test                     | Commande Maven                                 |
+-------------------------------------------------------+
| Exception lors de suppression étudiant| mvn -Dtest=StudentAndGradeServiceTest#deleteStudentThrowsException test |
| Exception pour suppression de note    | mvn -Dtest=StudentAndGradeServiceTest#deleteNonExistingGrade test |
+-------------------------------------------------------+
```

---

# 7. **Tests d'API (Controller/REST API Tests avec MockMvc)**

```plaintext
+---------------------------------------------------------+
|           Tests d'API avec MockMvc                      |
+---------------------------------------------------------+
| Scénario de test                    | Commande Maven                                   |
+---------------------------------------------------------+
| Créer un étudiant via API           | mvn -Dtest=GradebookControllerTest#createStudentAPI test |
| Supprimer un étudiant via API       | mvn -Dtest=GradebookControllerTest#deleteStudentAPI test |
| Ajouter une note via API            | mvn -Dtest=GradebookControllerTest#createGradeAPI test   |
+---------------------------------------------------------+
```

---

# 8. **Tests de repository avec Mockito**

```plaintext
+--------------------------------------------------------+
|        Tests de repository avec Mockito                |
+--------------------------------------------------------+
| Scénario de test                    | Commande Maven                                   |
+--------------------------------------------------------+
| Enregistrer un étudiant             | mvn -Dtest=StudentDaoTest#saveStudentMock test   |
| Rechercher un étudiant par email    | mvn -Dtest=StudentDaoTest#findByEmailMock test   |
| Supprimer un étudiant               | mvn -Dtest=StudentDaoTest#deleteStudentMock test |
+--------------------------------------------------------+
```

---

# Résumé des tests Maven :

- Les commandes fournies dans les tableaux ci-dessus permettent d'exécuter des tests spécifiques dans le projet. Ces tests couvrent une gamme complète de scénarios, y compris les tests unitaires de base avec JUnit, les tests avec Mockito pour simuler les dépendances, les tests d'intégration utilisant H2, et les tests d'API à l'aide de MockMvc.
- Vous pouvez copier-coller directement les commandes Maven dans votre terminal pour exécuter les tests sur leurs machines.
