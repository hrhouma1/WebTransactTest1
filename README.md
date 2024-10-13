# WebTransactTest1

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
                └───overRideData.sql

    └───test
        └───java
            └───com
                └───luv2code
                    └───springmvc
                        ├───GradebookControllerTest.java
                        └───StudentAndGradeServiceTest.java

└───target
    └───classes
        ├───application-test.properties
        ├───application.properties
        ├───insertData.sql
        ├───insertGrade.sql
        ├───overRideData.sql
        ├───generated-sources
        ├───generated-test-sources
        ├───maven-status
        └───surefire-reports
            ├───com.luv2code.springmvc.GradebookControllerTest.txt
            ├───com.luv2code.springmvc.StudentAndGradeServiceTest.txt
            ├───TEST-com.luv2code.springmvc.GradebookControllerTest.xml
            ├───TEST-com.luv2code.springmvc.StudentAndGradeServiceTest.xml
            └───test-classes
                └───com.luv2code.springmvc
                    └───GradebookControllerTest.class


```





- Pour utiliser Maven dans un projet Spring MVC comme celui-ci, voici une série de commandes pour configurer, tester, générer le fichier JAR, et déployer l'application.
- Cette série inclut les étapes pour tester et générer tous les artefacts possibles à l'aide de Maven.
- Ces commandes couvrent un cycle complet de développement, test, compilation, génération de fichiers JAR/WAR, et déploiement. 
- Assurez-vous que Maven est correctement configuré avec votre projet Spring et que toutes les dépendances sont installées avant d'exécuter ces commandes.
  
# 1. **Nettoyage du projet** (Clean)

Cela supprime tous les fichiers générés dans le répertoire `target`.

```bash
mvn clean
```

# 2. **Compiler le projet** (Compile)

Cette commande va compiler les fichiers source Java et générer les classes compilées dans le répertoire `target/classes`.

```bash
mvn compile
```

# 3. **Exécuter les tests unitaires** (Test)

Pour exécuter les tests unitaires avec Maven, utilisez la commande suivante :

```bash
mvn test
```

# 4. **Générer le package JAR** (Package)

Pour générer un fichier JAR (ou WAR, selon la configuration) du projet, utilisez :

```bash
mvn package
```

Cela créera un fichier JAR dans le dossier `target`.

# 5. **Exécuter le projet Spring Boot** (Spring Boot Run)

Si ce projet est configuré avec Spring Boot, vous pouvez le lancer directement avec Maven en utilisant la commande suivante :

```bash
mvn spring-boot:run
```

# 6. **Combinaison des commandes Clean, Install et Spring Boot Run**

Vous pouvez combiner plusieurs étapes avec Maven dans une seule ligne. Par exemple, pour nettoyer, installer les dépendances, compiler, tester, et exécuter l’application en une seule commande :

```bash
mvn clean install spring-boot:run
```

# 7. **Lancer les tests et générer le rapport de test** (Surefire Report)

Pour générer des rapports de tests avec Maven Surefire, utilisez :

```bash
mvn surefire-report:report
```

Le rapport sera généré dans le répertoire `target/site`.

# 8. **Générer un site pour le projet** (Site)

Vous pouvez générer un site HTML qui documente l'état du projet, y compris des rapports sur les tests et la couverture, à l'aide de la commande suivante :

```bash
mvn site
```

Le site sera généré dans `target/site/index.html`. Vous pouvez ouvrir ce fichier dans un navigateur pour voir la documentation du projet.

# 9. **Exécuter tous les tests (unitaires et d'intégration)**

Pour exécuter à la fois les tests unitaires et les tests d'intégration (si disponibles) :

```bash
mvn verify
```

# 10. **Créer un fichier JAR sans exécuter les tests** (Skip Tests)

Si vous souhaitez générer le fichier JAR sans exécuter les tests :

```bash
mvn clean package -DskipTests
```

# 11. **Générer un fichier JAR exécutable avec Spring Boot**

Si vous voulez créer un JAR exécutable avec Spring Boot (tout en incluant toutes les dépendances) :

```bash
mvn clean package spring-boot:repackage
```

Le fichier JAR exécutable sera disponible dans le répertoire `target`.

# 12. **Combinaison complète pour déploiement**

Voici une combinaison qui nettoie, compile, teste, génère le fichier JAR exécutable, et lance l'application :

```bash
mvn clean install spring-boot:repackage spring-boot:run
```

# 13. **Exécuter l'application en utilisant le fichier JAR généré**

Après avoir généré le fichier JAR exécutable avec Maven, vous pouvez le lancer directement avec Java :

```bash
java -jar target/nom-du-fichier.jar
```

# 14. **Déployer l'application sur Tomcat ou autre serveur** (WAR)

Si l'application est configurée pour générer un fichier WAR (pour un déploiement sur un serveur comme Tomcat), générez d'abord le fichier WAR :

```bash
mvn clean package
```

Ensuite, copiez le fichier WAR dans le dossier `webapps` de votre installation Tomcat.

# 15. **Documentation du code avec Javadoc**

Pour générer la documentation Javadoc du projet, vous pouvez utiliser la commande suivante :

```bash
mvn javadoc:javadoc
```

Cela générera la documentation dans le répertoire `target/site/apidocs`.

---

