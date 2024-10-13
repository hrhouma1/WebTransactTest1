# Comment exécuter un test

- Pour exécuter un test dans un projet Maven à partir du répertoire où se trouve le fichier `pom.xml`, vous pouvez suivre les étapes suivantes. 
- Supposons que vous souhaitez exécuter un test spécifique dans la classe `GradebookControllerTest.java`.

### Commande pour exécuter tous les tests :
Si vous souhaitez exécuter tous les tests du projet, utilisez la commande suivante dans le terminal à l'emplacement du fichier `pom.xml` :

```bash
mvn test
```

### Commande pour exécuter un test spécifique :
Si vous souhaitez exécuter un test spécifique, par exemple, la méthode `getStudentsHttpRequest` dans la classe `GradebookControllerTest.java`, vous pouvez utiliser cette commande Maven :

```bash
mvn -Dtest=GradebookControllerTest#getStudentsHttpRequest test
```

### Commande pour exécuter plusieurs tests spécifiques :
Si vous souhaitez exécuter plusieurs méthodes de test, vous pouvez les lister comme ceci :

```bash
mvn -Dtest=GradebookControllerTest#getStudentsHttpRequest,GradebookControllerTest#createStudentHttpRequest test
```

### Détails de la commande :
- `mvn test`: Cette commande exécute tous les tests.
- `-Dtest=NomDeClasse#NomDeTest`: Ce paramètre permet de spécifier un test spécifique. Si vous ne mettez que le nom de la classe (par exemple, `GradebookControllerTest`), cela exécutera tous les tests dans cette classe.
- `GradebookControllerTest#getStudentsHttpRequest`: Cela permet d'exécuter uniquement la méthode `getStudentsHttpRequest()` dans la classe `GradebookControllerTest`.

### Exemple d'utilisation pour `StudentAndGradeServiceTest` :
Si vous voulez exécuter un test spécifique dans la classe `StudentAndGradeServiceTest.java`, par exemple, la méthode `createStudentService`, vous pouvez taper :

```bash
mvn -Dtest=StudentAndGradeServiceTest#createStudentService test
```

Assurez-vous que le projet a bien été construit et que les dépendances sont en place avant d'exécuter les tests. Vous pouvez aussi consulter les rapports de test générés dans le dossier `target/surefire-reports` pour plus de détails sur l'exécution des tests.

