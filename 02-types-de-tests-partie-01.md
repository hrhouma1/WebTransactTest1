
# Introduction:

Dans le projet que vous travaillez, il existe plusieurs types de tests et de frameworks de tests utilisés pour vérifier différents aspects de l'application. Voici une vue d'ensemble des types de tests et des technologies impliquées :

### 1. **JUnit (Tests unitaires de base)**
   - **Type de test** : Tests unitaires.
   - **Framework** : JUnit (version 5 ici, aussi appelée **JUnit Jupiter**).
   - **But** : Vérifier que chaque unité individuelle de votre code (une méthode, un composant isolé) fonctionne comme prévu.
   - **Exemple** : 
     ```java
     @Test
     public void testFullName() {
         CollegeStudent student = new CollegeStudent("John", "Doe", "john.doe@example.com");
         assertEquals("John Doe", student.getFullName());
     }
     ```
   - **Caractéristiques** :
     - Exécution rapide.
     - Chaque test est isolé et ne dépend pas d'un autre.
     - Tests de logique métier simple sans interaction avec des dépendances externes.

### 2. **Mockito (Tests avec simulation des dépendances)**
   - **Type de test** : Tests unitaires avec mocks.
   - **Framework** : Mockito.
   - **But** : Simuler des dépendances externes (comme des bases de données, des services ou des objets complexes) afin de tester des composants indépendamment des autres parties de l'application.
   - **Exemple** :
     ```java
     @Mock
     private StudentDao studentDao;

     @Test
     public void testFindStudentById() {
         Mockito.when(studentDao.findById(1)).thenReturn(Optional.of(new CollegeStudent("John", "Doe", "john.doe@example.com")));

         CollegeStudent student = studentService.findStudentById(1);
         assertEquals("John", student.getFirstname());
     }
     ```
   - **Caractéristiques** :
     - Utilisé pour simuler des composants dépendants dans les tests.
     - Vous permet d'éviter les interactions avec de vrais composants (comme des bases de données ou des services tiers).
     - Tests de logique métier avec interaction simulée.

### 3. **Tests d'intégration (Integration Tests)**
   - **Type de test** : Tests d'intégration.
   - **Framework** : JUnit + Spring Boot Test.
   - **But** : Tester l'intégration des différents composants de l'application, en particulier les interactions avec des bases de données, des services externes ou d'autres systèmes.
   - **Exemple** :
     ```java
     @SpringBootTest
     public class GradebookControllerTest {

         @Autowired
         private MockMvc mockMvc;

         @Test
         public void getStudentsHttpRequest() throws Exception {
             mockMvc.perform(get("/students"))
                 .andExpect(status().isOk())
                 .andExpect(view().name("index"))
                 .andExpect(model().attributeExists("students"));
         }
     }
     ```
   - **Caractéristiques** :
     - Utilise un serveur web intégré (comme **MockMvc** pour simuler des requêtes HTTP).
     - Interagit avec une base de données réelle ou simulée (comme **H2 en mémoire**).
     - Teste le bon fonctionnement de toute la chaîne (contrôleurs, services, bases de données).
     - Exécutions plus longues que les tests unitaires simples.

### 4. **Spring Boot Test (Tests de contrôleur et tests d'intégration)**
   - **Type de test** : Tests d'intégration + tests de contrôleur.
   - **Framework** : Spring Boot Test + MockMvc.
   - **But** : Vérifier le comportement des endpoints REST ou MVC, en simulant des requêtes HTTP sur les contrôleurs. Utilise souvent **MockMvc** pour tester les contrôleurs sans lancer un vrai serveur web.
   - **Exemple** :
     ```java
     @SpringBootTest
     @AutoConfigureMockMvc
     public class GradebookControllerTest {

         @Autowired
         private MockMvc mockMvc;

         @Test
         public void testGetStudents() throws Exception {
             mockMvc.perform(get("/students"))
                 .andExpect(status().isOk())
                 .andExpect(view().name("index"))
                 .andExpect(model().attributeExists("students"));
         }
     }
     ```
   - **Caractéristiques** :
     - Teste les contrôleurs Spring MVC ou REST.
     - Utilise **MockMvc** pour simuler des requêtes HTTP (GET, POST, etc.).
     - Interagit avec les services réels ou simulés pour vérifier le bon fonctionnement global de l'application.
  
### 5. **Tests de validation (Validation Tests)**
   - **Type de test** : Tests de validation.
   - **Framework** : JUnit + Annotations de validation Spring.
   - **But** : Tester que les données d'entrée respectent bien les règles de validation définies avec des annotations comme `@NotNull`, `@Size`, `@Email`, etc.
   - **Exemple** :
     ```java
     @Test
     public void testValidationEmail() {
         CollegeStudent student = new CollegeStudent("John", "Doe", "invalid-email");
         Set<ConstraintViolation<CollegeStudent>> violations = validator.validate(student);
         assertFalse(violations.isEmpty());
     }
     ```
   - **Caractéristiques** :
     - Utilisé pour vérifier que les validations sur les données d'entrée fonctionnent correctement.
     - Basé sur les annotations de validation des entités dans Spring (`@NotNull`, `@Size`, etc.).
     - Peut être testé indépendamment des contrôleurs ou des services.

### 6. **Tests d'exception (Exception Testing)**
   - **Type de test** : Tests d'exception.
   - **Framework** : JUnit + Mockito.
   - **But** : Vérifier que certaines méthodes lancent bien des exceptions prévues dans des conditions spécifiques.
   - **Exemple** :
     ```java
     @Test
     public void testDeleteStudentThrowsException() {
         Mockito.when(studentDao.deleteById(1)).thenThrow(new RuntimeException("Erreur suppression"));

         assertThrows(RuntimeException.class, () -> {
             studentService.deleteStudent(1);
         });
     }
     ```
   - **Caractéristiques** :
     - Simule des conditions d'erreur pour s'assurer que le code lance correctement les exceptions prévues.
     - Peut être utilisé avec **Mockito** pour simuler des erreurs dans les dépendances.

### 7. **Tests d'API (Controller/REST API Tests avec MockMvc)**
   - **Type de test** : Tests d'API.
   - **Framework** : MockMvc.
   - **But** : Tester les endpoints REST de l'application en simulant des requêtes HTTP GET, POST, PUT, DELETE.
   - **Exemple** :
     ```java
     @Test
     public void testCreateStudentAPI() throws Exception {
         mockMvc.perform(post("/api/students")
                 .contentType(MediaType.APPLICATION_JSON)
                 .content("{\"firstname\":\"John\",\"lastname\":\"Doe\",\"email\":\"john.doe@example.com\"}"))
                 .andExpect(status().isOk())
                 .andExpect(jsonPath("$.firstname").value("John"));
     }
     ```
   - **Caractéristiques** :
     - Teste directement les endpoints REST.
     - Vérifie la réponse JSON ou HTML retournée par les API.
     - Utilise **MockMvc** pour simuler les appels HTTP.

---

### Récapitulatif des technologies utilisées dans le projet

1. **JUnit (Tests unitaires)** :
   - Tests simples, indépendants, centrés sur la logique métier.

2. **Mockito (Tests avec mocks)** :
   - Simule des objets/dépendances pour des tests plus isolés sans interaction avec des services ou des bases de données réels.

3. **Spring Boot Test + MockMvc (Tests d'intégration/contrôleur)** :
   - Teste l'intégration des composants avec un serveur simulé et des requêtes HTTP simulées.

4. **H2 Database (Tests d'intégration avec une base de données en mémoire)** :
   - Pour les tests d'intégration qui nécessitent une base de données.

5. **Validation Tests (Tests de validation)** :
   - Vérifie les règles de validation appliquées sur les données d'entrée des entités.

---

Vous pouvez combiner ces différents types de tests pour obtenir une couverture de test complète de votre application, allant des tests unitaires de base à des tests d'intégration plus complexes.
