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



-----------------------------
# TRoubleshooting
-----------------------------

```bash
mvn -Dtest=StudentDaoTest#saveStudentMock test
```

```bash
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.137 s
[INFO] Finished at: 2024-10-12T22:29:18-04:00
[INFO] ------------------------------------------------------------------------
```


L'erreur affichée indique que **"No tests were executed"**. Cela signifie que Maven n'a trouvé aucun test à exécuter avec la commande fournie.

Pour résoudre ce problème, voici quelques étapes et suggestions à suivre :

### 1. **Vérifier les noms des classes et méthodes de test**
Assurez-vous que le nom de la classe de test et de la méthode que vous avez fournie dans la commande Maven est correct. Par exemple :

```bash
mvn -Dtest=StudentDaoTest#saveStudentMock test
```

Vérifiez si la classe `StudentDaoTest` existe réellement et si elle contient bien une méthode de test nommée `saveStudentMock`.

### 2. **Corriger la commande Maven**
La commande suivante permet de tester une méthode spécifique :

```bash
mvn -Dtest=StudentDaoTest#methodName test
```

Remplacez `methodName` par le nom exact de votre méthode. Assurez-vous que la classe et la méthode de test sont correctement orthographiées et définies.

### 3. **Vérification du fichier `pom.xml`**
Assurez-vous que le fichier `pom.xml` contient les bonnes dépendances pour les tests. Notamment les dépendances pour `JUnit`, `Mockito`, et les plugins nécessaires pour exécuter les tests avec Maven. Le plugin Maven Surefire doit également être correctement configuré.

### Exemple de dépendances dans le `pom.xml` :

```xml
<dependencies>
    <!-- Spring Boot Test -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
    
    <!-- Mockito -->
    <dependency>
        <groupId>org.mockito</groupId>
        <artifactId>mockito-core</artifactId>
        <version>4.0.0</version>
        <scope>test</scope>
    </dependency>

    <!-- JUnit -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <scope>test</scope>
    </dependency>
    
</dependencies>

<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>2.22.2</version>
        </plugin>
    </plugins>
</build>
```

### 4. **Vérifier que les tests sont annotés avec `@Test`**
Assurez-vous que vos méthodes de test dans la classe `StudentDaoTest` (ou toute autre classe) sont correctement annotées avec `@Test`. Sans cette annotation, JUnit ne reconnaîtra pas la méthode comme un test.

```java
import org.junit.jupiter.api.Test;

public class StudentDaoTest {
    
    @Test
    public void saveStudentMock() {
        // Logique de test ici
    }
}
```

### 5. **Exécuter tous les tests de la classe**
Si vous souhaitez exécuter tous les tests d'une classe spécifique, vous pouvez utiliser la commande suivante :

```bash
mvn -Dtest=StudentDaoTest test
```

Cela exécutera tous les tests disponibles dans la classe `StudentDaoTest`.

### 6. **Exécuter tous les tests du projet**
Si vous souhaitez exécuter tous les tests du projet :

```bash
mvn test
```

Cela permettra à Maven d'exécuter tous les tests dans le projet.

### 7. **Utilisation de `-DfailIfNoTests=false`**
Si vous êtes sûr que la commande est correcte mais que les tests ne sont pas trouvés pour une raison quelconque, vous pouvez ajouter l'option `-DfailIfNoTests=false` pour éviter l'échec du build si aucun test n'est trouvé :

```bash
mvn -Dtest=StudentDaoTest#saveStudentMock -DfailIfNoTests=false test
```

### Conclusion :
- Vérifiez l'existence de la classe et de la méthode de test.
- Assurez-vous que les méthodes de test sont bien annotées avec `@Test`.
- Vérifiez la configuration du fichier `pom.xml`.
- Si nécessaire, utilisez `-DfailIfNoTests=false` pour éviter les échecs lorsque Maven ne trouve pas les tests.

Essayez ces étapes et assurez-vous que les noms de classes et de méthodes sont corrects.
