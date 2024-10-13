- Je vous présente une liste complète des tests supplémentaires basés sur **Mockito**, utilisés dans les tests unitaires pour isoler et simuler les comportements dans notre projet Spring Boot. 
- Ces tests impliquent l'utilisation de `Mockito` pour simuler des dépendances et s'assurer que les méthodes des services ou des contrôleurs fonctionnent correctement sans toucher la base de données ou d'autres systèmes externes.

### Commandes pour les tests basés sur Mockito

```plaintext
+--------------------------------------+-------------------------------------------------------------+
| Classe de test                       | Commande Maven                                              |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter tous les tests avec Mockito  | mvn test                                                    |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter les tests de                 | mvn -Dtest=GradebookControllerTest#createStudentWithMock test|
| `GradebookControllerTest` avec Mock  |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test spécifique           | mvn -Dtest=GradebookControllerTest#getStudentsWithMock test  |
| qui utilise Mockito                   |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test avec mock pour       | mvn -Dtest=GradebookControllerTest#deleteStudentWithMock test|
| suppression de student                |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test avec Mockito         | mvn -Dtest=GradebookControllerTest#createGradeWithMock test  |
| pour la création d'une note           |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test avec Mockito pour    | mvn -Dtest=StudentAndGradeServiceTest#createStudentMock test |
| création d'un étudiant                |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test avec Mockito pour    | mvn -Dtest=StudentAndGradeServiceTest#deleteGradeWithMock test|
| suppression d'une note                |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test avec Mockito pour    | mvn -Dtest=StudentAndGradeServiceTest#getStudentInfoMock test|
| récupération des infos d'étudiant     |                                                             |
+--------------------------------------+-------------------------------------------------------------+
| Exécuter un test de validation avec   | mvn -Dtest=StudentAndGradeServiceTest#isStudentValidMock test|
| Mockito                               |                                                             |
+--------------------------------------+-------------------------------------------------------------+
```

### Tests supplémentaires basés sur Mockito

#### `GradebookControllerTest.java`
- **`createStudentWithMock`** : Simule la création d’un étudiant via le contrôleur avec Mockito pour isoler le service.
- **`getStudentsWithMock`** : Teste la récupération des étudiants via un mock du service.
- **`deleteStudentWithMock`** : Teste la suppression d’un étudiant avec un mock de la couche service.
- **`createGradeWithMock`** : Teste la création d'une note via un mock du service.

#### `StudentAndGradeServiceTest.java`
- **`createStudentMock`** : Simule la création d’un étudiant via un mock du DAO.
- **`deleteGradeWithMock`** : Simule la suppression d'une note via un mock du DAO.
- **`getStudentInfoMock`** : Simule la récupération des informations d'un étudiant.
- **`isStudentValidMock`** : Teste la validation d’un étudiant via un mock du service ou du DAO.

### Exemples d'exécution de commandes :

1. **Pour exécuter le test `createStudentWithMock` dans `GradebookControllerTest` :**
   ```bash
   mvn -Dtest=GradebookControllerTest#createStudentWithMock test
   ```

2. **Pour exécuter le test `getStudentsWithMock` dans `GradebookControllerTest` :**
   ```bash
   mvn -Dtest=GradebookControllerTest#getStudentsWithMock test
   ```

3. **Pour exécuter le test `createStudentMock` dans `StudentAndGradeServiceTest` :**
   ```bash
   mvn -Dtest=StudentAndGradeServiceTest#createStudentMock test
   ```

4. **Pour exécuter tous les tests dans `StudentAndGradeServiceTest` qui utilisent Mockito :**
   ```bash
   mvn -Dtest=StudentAndGradeServiceTest test
   ```

5. **Pour exécuter tous les tests de `GradebookControllerTest` avec des mocks :**
   ```bash
   mvn -Dtest=GradebookControllerTest test
   ```

### Tests d’erreurs et de réussite avec Mockito
Pour provoquer un échec dans un test Mockito, vous pouvez simuler des comportements tels que :

- **Lever une exception pour simuler un échec de méthode :**
   ```java
   Mockito.when(service.deleteStudent(1)).thenThrow(new RuntimeException("Erreur suppression"));
   ```

- **Simuler une mauvaise entrée :**
   ```java
   Mockito.when(service.createStudent("Invalid", "", "")).thenReturn(null);
   ```

N'hésitez pas à adapter ces tests selon vos besoins en ajoutant des assertions supplémentaires ou des mocks plus complexes. 
