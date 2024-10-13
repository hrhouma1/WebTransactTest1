---------------------------------------------------------
# Introduction aux tests unitaires et à Mockito
---------------------------------------------------------

Dans un projet logiciel, les tests sont cruciaux pour garantir que le code fonctionne comme prévu et que les modifications apportées n'introduisent pas de nouveaux bogues. Différents types de tests permettent de vérifier le bon fonctionnement des différentes parties du code, à des niveaux d'abstraction variés. Nous allons voir ici ce qu’est un **test unitaire** et introduire l’utilisation de **Mockito** pour les tests unitaires avec simulation de dépendances.

---

# Qu'est-ce qu'un test unitaire ?
Un **test unitaire** est un test qui vérifie le bon fonctionnement d'une **unité** de code isolée, généralement une méthode ou une classe. L'objectif est de s'assurer que cette unité produit les résultats attendus pour des entrées spécifiques et qu'elle se comporte correctement même en cas d'erreurs prévues.

# Caractéristiques principales :
- **Isolation** : Chaque test est indépendant et ne dépend pas d'autres tests.
- **Vérification de la logique métier** : Le test unitaire se concentre sur une seule fonctionnalité ou logique de la méthode testée.
- **Rapide** : Les tests unitaires sont rapides à exécuter car ils ne nécessitent pas d'interactions avec des bases de données, des services web, ou d'autres ressources externes.

# Exemple de test unitaire avec JUnit :

Dans cet exemple, nous testons une méthode qui retourne le nom complet d’un étudiant.

```java
@Test
public void testFullName() {
    CollegeStudent student = new CollegeStudent("John", "Doe", "john.doe@example.com");
    assertEquals("John Doe", student.getFullName());
}
```

Ici, nous créons un objet `CollegeStudent` avec un prénom et un nom, puis nous utilisons l'assertion `assertEquals` pour vérifier que la méthode `getFullName()` retourne bien "John Doe".

# Pourquoi les tests unitaires sont importants ?
- **Fiabilité** : Ils permettent de s'assurer que chaque composant fonctionne indépendamment.
- **Régression** : Si un changement introduit un bug, les tests unitaires peuvent rapidement le détecter.
- **Maintenance** : Des tests unitaires bien rédigés facilitent la refactorisation du code car vous pouvez rapidement vérifier que rien n'a été cassé.

---

# Qu'est-ce que Mockito ?

Mockito est un **framework de simulation** (mocking) qui permet de créer des objets simulés (ou "mocks") pour des dépendances externes dans vos tests. Lorsque vous testez une méthode d'un service qui dépend d'autres services ou d'une base de données, vous pouvez utiliser Mockito pour **simuler** ces dépendances sans avoir à réellement interagir avec elles.

# Pourquoi utiliser Mockito ?
- **Isolation** : Vous pouvez tester une unité de code indépendamment de ses dépendances.
- **Simuler des comportements complexes** : Il est possible de simuler le comportement des dépendances pour tester des cas spécifiques (comme des erreurs ou des résultats conditionnels).
- **Test rapide** : Éviter l’accès à des bases de données ou des services externes rend les tests plus rapides.

# Exemple d'utilisation de Mockito :
Dans cet exemple, nous simulons une base de données (`StudentDao`) pour tester une méthode de service qui récupère un étudiant.

```java
@Mock
private StudentDao studentDao;

@InjectMocks
private StudentAndGradeService studentService;

@BeforeEach
public void setup() {
    MockitoAnnotations.openMocks(this); // Initialise les mocks
}

@Test
public void testFindStudentById() {
    Mockito.when(studentDao.findById(1)).thenReturn(Optional.of(new CollegeStudent("John", "Doe", "john.doe@example.com")));

    CollegeStudent student = studentService.studentInformation(1);
    assertEquals("John", student.getFirstname());
}
```

# Explication de l'exemple :
1. **@Mock** : Cette annotation permet de créer un mock de l'interface `StudentDao`. Cela signifie que nous allons simuler le comportement de cette dépendance dans nos tests.
2. **@InjectMocks** : Cette annotation permet d'injecter le mock dans notre classe `StudentAndGradeService` pour tester ses méthodes.
3. **Mockito.when(...).thenReturn(...)** : Nous définissons un comportement simulé. Ici, nous disons que lorsque la méthode `findById(1)` est appelée sur le mock `studentDao`, elle doit retourner un étudiant spécifique.
4. **assertEquals(...)** : Nous vérifions que le prénom de l'étudiant retourné est bien "John".

---

# Différence entre un test unitaire et un test d'intégration

- **Test unitaire** : Il teste une seule unité de code en isolation, en général une méthode ou une classe, et utilise des mocks pour simuler les dépendances. Il ne vérifie pas comment les différentes unités du système fonctionnent ensemble.
  
- **Test d'intégration** : Il vérifie comment différentes parties d'une application fonctionnent ensemble, comme la communication entre des services, l'interaction avec une base de données, ou le fonctionnement des contrôleurs REST.

---

# Avantages et inconvénients des tests unitaires

| Avantages                                | Inconvénients                              |
|------------------------------------------|--------------------------------------------|
| Rapides à exécuter                        | Ne vérifient pas l'intégration entre composants |
| Faciles à écrire et à maintenir           | Nécessitent des mocks pour simuler les dépendances |
| Permettent d'identifier rapidement des erreurs de logique | Ne garantissent pas que l'application fonctionne correctement dans son ensemble |
  
---

# Résumé des concepts

- **Test unitaire** : Test d'une méthode ou d'une classe isolée pour vérifier la logique métier.
- **Mockito** : Framework pour simuler les dépendances dans les tests unitaires.
- **Test d'intégration** : Test du bon fonctionnement des différents composants d'une application ensemble.

En combinant les **tests unitaires** avec des mocks (grâce à **Mockito**) et les **tests d'intégration**, vous obtenez une couverture de test complète, assurant que chaque partie du code fonctionne correctement, aussi bien individuellement que collectivement.



-----------------------------------------------------------
# Autres exemples
-----------------------------------------------------------


Je vous présente des exemples de tests classés par catégories, avec les corrections et ajustements adaptés à votre projet Spring Boot basé sur les tests unitaires et d'intégration.

---

### 1. **JUnit (Tests unitaires de base)**

Les tests unitaires vérifient une méthode ou une classe individuelle sans dépendre d'autres parties du code. Ils sont simples et rapides à exécuter.

```java
@Test
public void testFullName() {
    CollegeStudent student = new CollegeStudent("John", "Doe", "john.doe@example.com");
    assertEquals("John Doe", student.getFullName());
}

@Test
public void testStudentEmail() {
    CollegeStudent student = new CollegeStudent("John", "Doe", "john.doe@example.com");
    assertEquals("john.doe@example.com", student.getEmailAddress());
}
```

#### Commande Maven :
```
mvn -Dtest=StudentAndGradeServiceTest test
```

---

### 2. **Mockito (Tests avec simulation des dépendances)**

Mockito est un framework permettant de simuler des objets externes, comme des bases de données ou d'autres services, pour tester une classe en isolation.

```java
@Mock
private StudentDao studentDao;

@InjectMocks
private StudentAndGradeService studentService;

@BeforeEach
public void setup() {
    MockitoAnnotations.openMocks(this);  // Initialiser les mocks
}

@Test
public void testFindStudentById() {
    Mockito.when(studentDao.findById(1)).thenReturn(Optional.of(new CollegeStudent("John", "Doe", "john.doe@example.com")));

    CollegeStudent student = studentService.studentInformation(1);
    assertEquals("John", student.getFirstname());
}
```

#### Commande Maven :
```
mvn -Dtest=StudentAndGradeServiceTest test
```

---

### 3. **Tests d'intégration (Integration Tests)**

Les tests d'intégration vérifient que plusieurs composants fonctionnent correctement ensemble, souvent en interaction avec des bases de données ou des services externes.

```java
@SpringBootTest
public class StudentAndGradeServiceIntegrationTest {

    @Autowired
    private StudentAndGradeService studentService;

    @Test
    public void testCreateStudentService() {
        studentService.createStudent("Jane", "Smith", "jane.smith@example.com");
        CollegeStudent student = studentService.studentInformation(1);
        assertEquals("jane.smith@example.com", student.getEmailAddress());
    }
}
```

#### Commande Maven :
```
mvn -Dtest=StudentAndGradeServiceIntegrationTest test
```

---

### 4. **Spring Boot Test (Tests de contrôleur et tests d'intégration)**

Les tests de contrôleur simulent les requêtes HTTP pour vérifier le comportement des endpoints de l'application, souvent avec l'aide de `MockMvc`.

```java
@SpringBootTest
@AutoConfigureMockMvc
public class GradebookControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void getStudentsHttpRequest() throws Exception {
        mockMvc.perform(MockMvcRequestBuilders.get("/students"))
            .andExpect(status().isOk())
            .andExpect(view().name("index"))
            .andExpect(model().attributeExists("students"));
    }
}
```

#### Commande Maven :
```
mvn -Dtest=GradebookControllerTest test
```

---

### 5. **Tests de validation (Validation Tests)**

Les tests de validation vérifient que les règles de validation appliquées aux entités fonctionnent correctement.

```java
@Test
public void testInvalidEmailValidation() {
    CollegeStudent student = new CollegeStudent("John", "Doe", "invalid-email");
    Set<ConstraintViolation<CollegeStudent>> violations = validator.validate(student);
    assertFalse(violations.isEmpty());
}

@Test
public void testValidStudent() {
    CollegeStudent student = new CollegeStudent("John", "Doe", "john.doe@example.com");
    Set<ConstraintViolation<CollegeStudent>> violations = validator.validate(student);
    assertTrue(violations.isEmpty());
}
```

#### Commande Maven :
```
mvn -Dtest=ValidationTest test
```

---

### 6. **Tests d'exception (Exception Testing)**

Les tests d'exception vérifient que les méthodes lancent bien les exceptions prévues dans des conditions spécifiques.

```java
@Test
public void testDeleteStudentThrowsException() {
    Mockito.when(studentDao.deleteById(1)).thenThrow(new RuntimeException("Erreur suppression"));

    assertThrows(RuntimeException.class, () -> {
        studentService.deleteStudent(1);
    });
}

@Test
public void testStudentNotFoundException() {
    Mockito.when(studentDao.findById(999)).thenReturn(Optional.empty());

    assertThrows(IllegalArgumentException.class, () -> {
        studentService.studentInformation(999);
    });
}
```

#### Commande Maven :
```
mvn -Dtest=StudentAndGradeServiceTest test
```

---

### 7. **Tests d'API (Controller/REST API Tests avec MockMvc)**

Ces tests vérifient les endpoints REST de votre application en simulant des requêtes HTTP GET, POST, PUT ou DELETE.

```java
@Test
public void testCreateStudentAPI() throws Exception {
    mockMvc.perform(post("/api/students")
            .contentType(MediaType.APPLICATION_JSON)
            .content("{\"firstname\":\"John\",\"lastname\":\"Doe\",\"email\":\"john.doe@example.com\"}"))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$.firstname").value("John"));
}

@Test
public void testDeleteStudentAPI() throws Exception {
    mockMvc.perform(delete("/api/students/1"))
            .andExpect(status().isOk())
            .andExpect(content().string("Student deleted"));
}
```

#### Commande Maven :
```
mvn -Dtest=GradebookControllerTest test
```

---

- Ces exemples couvrent une large gamme de tests que vous pouvez intégrer dans votre projet Spring Boot. 
- En utilisant JUnit, Mockito et les tests d'intégration, vous assurez une couverture exhaustive de vos fonctionnalités, du niveau unitaire au niveau de l'intégration complète. 
- Ces tests peuvent être utilisés directement par vos étudiants pour comprendre les concepts de tests en Spring Boot et améliorer la qualité de leur code.
