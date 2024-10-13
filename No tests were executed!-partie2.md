- Si vous rencontrez l'erreur suivante ("No tests were executed!"), ceci indique que Maven ne trouve pas les tests que vous spécifiez. 
- Voici quelques étapes pour résoudre ce problème et réussir à exécuter un test spécifique avec Maven.

# Étapes pour résoudre le problème :

1. **Vérifiez la classe de test** :
   Assurez-vous que la classe `CollegeStudentTest` existe et que le nom de la méthode de test est bien `testFullName`.

2. **Nom exact de la méthode** :
   Le nom de la méthode de test que vous spécifiez doit correspondre exactement à celui dans votre code. Par exemple, si la méthode dans votre classe de test s'appelle `testFullName`, vous devez l'utiliser exactement ainsi dans la commande Maven.

3. **Structure correcte des fichiers de test** :
   Assurez-vous que vos fichiers de test sont dans le bon répertoire. Les tests doivent se trouver dans le répertoire `src/test/java`. Si le fichier `CollegeStudentTest.java` n'est pas dans le bon répertoire, Maven ne pourra pas le trouver.

4. **Exécuter le test directement sans méthode** :
   Vous pouvez essayer d'exécuter tous les tests de la classe `CollegeStudentTest` sans spécifier de méthode pour vérifier que Maven trouve bien la classe de test :
   
   ```bash
   mvn -Dtest=CollegeStudentTest test
   ```

5. **Si Maven ne trouve toujours pas les tests, forcez le chemin** :
   Utilisez l'option `-DfailIfNoTests=false` pour ignorer l'erreur si Maven ne trouve aucun test (ceci permet de comprendre s'il s'agit d'un problème de reconnaissance de test) :
   
   ```bash
   mvn -Dtest=CollegeStudentTest -DfailIfNoTests=false test
   ```

6. **Forcer l'inclusion des tests** :
   Si Maven ne trouve toujours pas les tests, essayez d'exécuter la commande suivante pour forcer l'exécution des tests :

   ```bash
   mvn clean test
   ```

7. **Assurez-vous que vous utilisez les bonnes options Maven** :
   Le format correct pour exécuter un test spécifique dans une classe est :

   ```bash
   mvn -Dtest=CollegeStudentTest#testFullName test
   ```

# Commande correcte pour exécuter un test spécifique

Pour exécuter le test `testFullName` dans `CollegeStudentTest`, la commande devrait ressembler à ceci :

```bash
mvn -Dtest=CollegeStudentTest#testFullName test
```

Si vous avez encore des difficultés, voici quelques points supplémentaires à vérifier :

- Assurez-vous que le fichier `CollegeStudentTest.java` se trouve dans le répertoire correct `src/test/java/com/luv2code/springmvc/`.
- Vérifiez que la méthode `testFullName` est bien annotée avec `@Test` et que les autres dépendances (JUnit) sont correctement configurées dans le fichier `pom.xml`.

# Exemple d'exécution d'un test échoué

Si vous voulez provoquer une erreur intentionnellement, modifiez le test `testFullName` pour qu'il s'attende à une valeur incorrecte, par exemple :

```java
@Test
public void testFullName() {
    CollegeStudent student = new CollegeStudent("John", "Doe", "john.doe@example.com");
    assertEquals("John Smith", student.getFullName());  // Ce test échouera car "John Smith" est incorrect
}
```

Exécutez ensuite la commande suivante pour voir le test échouer :

```bash
mvn -Dtest=CollegeStudentTest#testFullName test
```

Cela devrait produire un message d'échec similaire à :

```
[ERROR] testFullName  Time elapsed: 0.001 s  <<< FAILURE!
java.lang.AssertionError: expected:<John Smith> but was:<John Doe>
```

