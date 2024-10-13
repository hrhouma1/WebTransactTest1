--------------------------------
# Tests dans les classes GradebookControllerTest et StudentAndGradeServiceTest
--------------------------------



```html


TESTS-SOLUTION-FINAL
│
└───src
    │
    └───main
        │
        └───java
        │   └───com
        │       └───luv2code
        │           └───springmvc
        │               ├───controller
        │               │   └───GradebookController.java
        │               │
        │               └───models
        │                   ├───CollegeStudent.java
        │                   ├───Grade.java
        │                   ├───Gradebook.java
        │                   ├───GradebookCollegeStudent.java
        │                   ├───HistoryGrade.java
        │                   ├───MathGrade.java
        │                   ├───ScienceGrade.java
        │                   ├───Student.java
        │                   └───StudentGrades.java
        │
        └───repository
        │   ├───HistoryGradesDao.java
        │   ├───MathGradesDao.java
        │   ├───ScienceGradesDao.java
        │   └───StudentDao.java
        │
        └───service
        │   ├───StudentAndGradeService.java
        │   └───MvcTestingExampleApplication.java
        │
        └───resources
            ├───static
            │   └───cssandjs
            │       ├───main.js
            │       └───main.css
            │
            └───templates
                ├───error.html
                ├───index.html
                ├───studentInformation.html
            ├───application-test.properties
            ├───application.properties
            ├───insertData.sql
            ├───insertGrade.sql
            ├───overRideData.sql

    └───test
        └───java
            └───com
                └───luv2code
                    └───springmvc
                        ├───GradebookControllerTest.java
                        └───StudentAndGradeServiceTest.java

└───target
    └───classes
        ├───com
        │   └───luv2code
        │       └───springmvc
        │           ├───controller
        │           ├───models
        │           ├───repository
        │           ├───service
        │           └───MvcTestingExampleApplication.class
        ├───static
        │   ├───cssandjs
        │   │   ├───main.js
        │   │   └───main.css
        └───templates
            ├───error.html
            ├───index.html
            ├───studentInformation.html
        ├───application-test.properties
        ├───application.properties
        ├───insertData.sql
        ├───insertGrade.sql
        ├───overRideData.sql
        ├───generated-sources
        ├───generated-test-sources
        ├───maven-status
        ├───surefire-reports
            ├───com.luv2code.springmvc.GradebookControllerTest.txt
            ├───com.luv2code.springmvc.StudentAndGradeServiceTest.txt
            ├───TEST-com.luv2code.springmvc.GradebookControllerTest.xml
            ├───TEST-com.luv2code.springmvc.StudentAndGradeServiceTest.xml
        └───test-classes
            └───com
                └───luv2code
                    └───springmvc
                        └───GradebookControllerTest.class


```

### Table complète des tests à exécuter 

```plaintext
+--------------------------------------+-------------------------------------------------+
| Classe de test                       | Commande Maven                                  |
+--------------------------------------+-------------------------------------------------+
| Exécuter tous les tests              | mvn test                                        |
+--------------------------------------+-------------------------------------------------+
| Exécuter tous les tests dans         | mvn -Dtest=GradebookControllerTest test         |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#getStudentsHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createStudentHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#deleteStudentHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#studentInformationHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#studentInformationHttpStudentDoesNotExistRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createMathGradeHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createScienceGradeHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createHistoryGradeHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createHistoryGradeHttpStudentDoesNotExistEmptyResponse test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createHistoryGradeHttpGradeTypeDoesNotExistEmptyResponse test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createHistoryGradeHttpGradeIsHigherThan100EmptyResponse test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#createHistoryGradeHttpGradeIsNegativeEmptyResponse test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#deleteMathGradeHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#deleteScienceGradeHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#deleteHistoryGradeHttpRequest test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#deleteGradeHttpRequestStudentIdDoesNotExistEmptyResponse test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#deleteGradeHttpRequestGradeTypeDoesNotExistEmptyResponse test |
| GradebookControllerTest.java         |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter tous les tests dans         | mvn -Dtest=StudentAndGradeServiceTest test       |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#isStudentNullCheck test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#createStudentService test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#deleteStudentService test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#studentInformationService test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#isGradeNullCheck test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#deleteGradeService test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#createGradeService test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#getGradebookService test |
| StudentAndGradeServiceTest.java      |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter tous les tests dans les     | mvn -Dtest=GradebookControllerTest,             |
| classes GradebookControllerTest      | StudentAndGradeServiceTest test                 |
| et StudentAndGradeServiceTest        |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test avec l'option debug | mvn -Dtest=GradebookControllerTest#getStudentsHttpRequest -X test |
| pour voir plus de logs               |                                                 |
+--------------------------------------+-------------------------------------------------+
| Exécuter un test sans compilation    | mvn -Dtest=GradebookControllerTest#getStudentsHttpRequest -DskipTests=false test |
| (uniquement les tests existants)     |                                                 |
+--------------------------------------+-------------------------------------------------+
```

### Commandes clés supplémentaires :
- **`mvn -Dtest=GradebookControllerTest#NomDeMéthode`** : Permet de tester des méthodes spécifiques comme `createMathGradeHttpRequest` ou `deleteScienceGradeHttpRequest`.
- **`mvn -Dtest=StudentAndGradeServiceTest#NomDeMéthode`** : Pour tester des services spécifiques tels que `createStudentService` ou `deleteGradeService`.

# Conclusion
- Cela couvre tous les tests dans les classes **GradebookControllerTest** et **StudentAndGradeServiceTest**. 
- Vous pouvez exécuter chaque test individuel, ou plusieurs tests à la fois en les séparant par des virgules, pour affiner votre processus de tests. 

