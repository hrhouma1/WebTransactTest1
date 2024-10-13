
# Résumé

- Je vous présente un résumé d'exemples de tests que vous pouvez exécuter dans notre projet Maven. 
- Cette table couvre différents cas de test dans les classes `GradebookControllerTest` et `StudentAndGradeServiceTest`, ainsi que des combinaisons de tests.
- Chaque ligne vous donne une commande Maven spécifique à exécuter.

```plaintext
+--------------------------------------+--------------------------------------------+
| Classe de test                       | Commande Maven                             |
+--------------------------------------+--------------------------------------------+
| Exécuter tous les tests              | mvn test                                   |
+--------------------------------------+--------------------------------------------+
| Exécuter tous les tests dans         | mvn -Dtest=GradebookControllerTest test    |
| GradebookControllerTest.java         |                                            |
+--------------------------------------+--------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=GradebookControllerTest#        |
| GradebookControllerTest.java         | getStudentsHttpRequest test                |
+--------------------------------------+--------------------------------------------+
| Exécuter un autre test spécifique    | mvn -Dtest=GradebookControllerTest#        |
| dans GradebookControllerTest.java    | createStudentHttpRequest test              |
+--------------------------------------+--------------------------------------------+
| Exécuter plusieurs tests dans        | mvn -Dtest=GradebookControllerTest#        |
| GradebookControllerTest.java         | getStudentsHttpRequest,                   |
|                                      | GradebookControllerTest#createStudentHttpRequest test |
+--------------------------------------+--------------------------------------------+
| Exécuter tous les tests dans         | mvn -Dtest=StudentAndGradeServiceTest test |
| StudentAndGradeServiceTest.java      |                                            |
+--------------------------------------+--------------------------------------------+
| Exécuter un test spécifique dans     | mvn -Dtest=StudentAndGradeServiceTest#     |
| StudentAndGradeServiceTest.java      | createStudentService test                  |
+--------------------------------------+--------------------------------------------+
| Exécuter un autre test spécifique    | mvn -Dtest=StudentAndGradeServiceTest#     |
| dans StudentAndGradeServiceTest.java | deleteStudentService test                  |
+--------------------------------------+--------------------------------------------+
| Exécuter plusieurs tests dans        | mvn -Dtest=StudentAndGradeServiceTest#     |
| StudentAndGradeServiceTest.java      | createStudentService,                      |
|                                      | StudentAndGradeServiceTest#deleteStudentService test |
+--------------------------------------+--------------------------------------------+
| Exécuter tous les tests dans les     | mvn -Dtest=GradebookControllerTest,        |
| classes GradebookControllerTest      | StudentAndGradeServiceTest test            |
| et StudentAndGradeServiceTest        |                                            |
+--------------------------------------+--------------------------------------------+
| Exécuter un test avec l'option debug | mvn -Dtest=GradebookControllerTest#        |
| pour voir plus de logs               | getStudentsHttpRequest -X test             |
+--------------------------------------+--------------------------------------------+
| Exécuter un test sans compilation    | mvn -Dtest=GradebookControllerTest#        |
| (uniquement les tests existants)     | getStudentsHttpRequest -DskipTests=false test |
+--------------------------------------+--------------------------------------------+
```

### Explication des commandes :
- **`mvn test`** : Exécute tous les tests dans le projet.
- **`-Dtest=NomDeClasse#NomDeMéthode`** : Exécute une méthode de test spécifique dans la classe spécifiée.
- **`-Dtest=NomDeClasse`** : Exécute tous les tests dans une classe spécifique.
- **`-X`** : Active les logs en mode "debug" pour avoir plus de détails sur l'exécution des tests.
- **`-DskipTests=false`** : Empêche Maven d'ignorer les tests si la compilation est demandée sans tests.

Vous pouvez copier ces commandes et les exécuter à partir du répertoire où se trouve votre fichier `pom.xml`.

N'hésitez pas à me demander si vous avez besoin de plus d'exemples ou d'une explication supplémentaire sur les tests unitaires !
