
# Objectif :
- Je vous présente une série d'exemples concrets tirés du projet que nous utilisons, organisés par type de test, avec une table pour chaque section. 
- Vous pouvez les copier-coller les exemples directement pour les utiliser et les tester. 
- Chaque section est détaillée avec un exemple approprié pour faciliter la compréhension.

---

### 1. **JUnit (Tests unitaires de base)**

```plaintext
+--------------------------------------------+
|          JUnit - Tests unitaires           |
+--------------------------------------------+
| Test de méthode basique avec JUnit         |
+--------------------------------------------+

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

---

### 2. **Mockito (Tests avec simulation des dépendances)**

```plaintext
+--------------------------------------------+
|        Mockito - Simulation des mocks      |
+--------------------------------------------+
| Test avec Mockito pour simuler une DAO     |
+--------------------------------------------+

@Mock
private StudentDao studentDao;

@InjectMocks
private StudentAndGradeService studentService;

@BeforeEach
public void setup() {
    MockitoAnnotations.openMocks(this);
}

@Test
public void testFindStudentById() {
    Mockito.when(studentDao.findById(1)).thenReturn(Optional.of(new CollegeStudent("John", "Doe", "john.doe@example.com")));

    CollegeStudent student = studentService.studentInformation(1);
    assertEquals("John", student.getFirstname());
}
```

---

### 3. **Tests d'intégration (Integration Tests)**

```plaintext
+--------------------------------------------+
|      Tests d'intégration avec H2 DB        |
+--------------------------------------------+
| Test de l'intégration complète avec H2     |
+--------------------------------------------+

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

---

### 4. **Spring Boot Test (Tests de contrôleur et tests d'intégration)**

```plaintext
+--------------------------------------------+
| Spring Boot Test avec MockMvc pour contrôleur|
+--------------------------------------------+
| Test d'intégration avec MockMvc            |
+--------------------------------------------+

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

---

### 5. **Tests de validation (Validation Tests)**

```plaintext
+--------------------------------------------+
|         Tests de validation des données    |
+--------------------------------------------+
| Test de validation des entités             |
+--------------------------------------------+

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

---

### 6. **Tests d'exception (Exception Testing)**

```plaintext
+--------------------------------------------+
|       Tests d'exception avec Mockito       |
+--------------------------------------------+
| Test des exceptions dans les services      |
+--------------------------------------------+

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

---

### 7. **Tests d'API (Controller/REST API Tests avec MockMvc)**

```plaintext
+--------------------------------------------+
|        Tests d'API avec MockMvc            |
+--------------------------------------------+
| Test des endpoints REST avec MockMvc       |
+--------------------------------------------+

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

---

Ces exemples couvrent les différents types de tests dans le cadre de votre projet Spring Boot. Vous pouvez les utiliser pour démontrer les concepts et permettre à vos étudiants de mieux comprendre comment tester les différents aspects d'une application Spring Boot.

Chacun de ces tests peut être copié et collé dans les fichiers de test appropriés pour une exécution immédiate. Ils sont conçus pour être simples à comprendre et adaptés au projet déjà en place.
