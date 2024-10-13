---------------------------------
# Structure
---------------------------------


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



-------------------
# Pistes à vérifier pour s'assurer que tout fonctionne correctement dans notre projet :
-------------------

# 1. **Vérification de la structure du projet :**
   - Assurez-vous que la structure des packages (controller, models, repository, service, etc.) est correcte, comme dans vos captures d'écran, et que les fichiers de configuration comme `application-test.properties` sont correctement placés dans le dossier `resources`.

# 2. **Exécuter un test spécifique :**
   Si vous avez un problème avec la commande Maven pour exécuter un test spécifique, vous pouvez essayer de formuler la commande de cette manière :

   ```bash
   mvn test -Dtest=NomDeLaClasseDeTest#NomDeLaMéthodeDeTest
   ```

   Exemple pour exécuter un test spécifique :
   ```bash
   mvn test -Dtest=CollegeStudentTest#testFullName
   ```

   Assurez-vous que :
   - Le nom de la classe de test est bien `CollegeStudentTest`.
   - Le nom de la méthode de test que vous essayez d'exécuter est exactement `testFullName`.

# 3. **Vérification des dépendances Maven :**
   Si vous rencontrez une erreur `No tests were executed`, vérifiez que le plugin `maven-surefire-plugin` est bien configuré dans le fichier `pom.xml`. Voici un exemple de configuration pour le plugin :

   ```xml
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

# 4. **Vérifier le contenu du test :**
   Assurez-vous que le test que vous essayez d'exécuter existe bien dans le fichier source et qu'il est correctement annoté avec `@Test`.

# 5. **Vérification des fichiers `application.properties` et `application-test.properties` :**
   Vos fichiers de configuration doivent inclure les informations correctes pour la base de données H2 en mémoire (si vous l'utilisez pour les tests), ainsi que les scripts SQL pour insérer des données de test.

