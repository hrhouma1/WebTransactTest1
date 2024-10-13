Voici un guide pour tester les différentes pages et actions de votre application Spring Boot avec les contrôleurs définis ci-dessus.

### 1. **Accéder à la page d'accueil (index.html)**

Pour accéder à la page d'accueil qui affiche la liste des étudiants, vous pouvez utiliser l'URL suivante :

```
http://localhost:1500/
```

Cela invoquera la méthode `getStudents` du contrôleur et affichera la vue `index.html`.

### 2. **Accéder à la page des informations de l'étudiant (studentInformation.html)**

Pour afficher les informations d'un étudiant spécifique, vous pouvez utiliser une URL avec l'ID de l'étudiant. Par exemple, pour accéder à l'étudiant avec l'ID 1 :

```
http://localhost:1500/studentInformation/1
```

Cela invoquera la méthode `studentInformation` du contrôleur et affichera la vue `studentInformation.html`. Si l'étudiant n'existe pas, cela affichera la page `error.html`.

### 3. **Créer un nouvel étudiant**

La création d'un étudiant se fait via une requête POST. Voici un exemple de commande cURL pour tester la création d'un étudiant via le terminal :

```bash
curl -X POST -d "firstname=John&lastname=Doe&emailAddress=john.doe@example.com" http://localhost:1500/
```

Cela invoquera la méthode `createStudent` du contrôleur et retournera à la page d'accueil avec la liste mise à jour des étudiants.

### 4. **Supprimer un étudiant**

Pour supprimer un étudiant, vous pouvez utiliser l'URL suivante avec l'ID de l'étudiant à supprimer. Par exemple, pour supprimer l'étudiant avec l'ID 1 :

```
http://localhost:1500/delete/student/1
```

Cela invoquera la méthode `deleteStudent` du contrôleur et retournera à la vue `index.html` avec la liste mise à jour des étudiants.

### 5. **Ajouter une note à un étudiant**

Pour ajouter une note à un étudiant, utilisez une requête POST avec les informations suivantes. Voici un exemple de commande cURL pour tester l'ajout d'une note :

```bash
curl -X POST -d "grade=90&gradeType=math&studentId=1" http://localhost:1500/grades
```

Cela invoquera la méthode `createGrade` du contrôleur et retournera à la vue `studentInformation.html` de l'étudiant mis à jour.

### 6. **Supprimer une note d'un étudiant**

Pour supprimer une note d'un étudiant, utilisez l'URL suivante avec l'ID de la note et le type de note (par exemple, math) :

```
http://localhost:1500/grades/1/math
```

Cela invoquera la méthode `deleteGrade` et retournera à la vue `studentInformation.html` mise à jour.

### 7. **Tester l'application en ligne de commande avec Maven**

Voici quelques commandes Maven pour tester certaines fonctionnalités :

#### Commande Maven pour exécuter des tests spécifiques

- **Test pour créer un étudiant :**
```bash
mvn -Dtest=GradebookControllerTest#createStudentWithMock test
```

- **Test pour supprimer un étudiant :**
```bash
mvn -Dtest=GradebookControllerTest#deleteStudentWithMock test
```

- **Test pour afficher les informations d'un étudiant :**
```bash
mvn -Dtest=GradebookControllerTest#getStudentInfoWithMock test
```

### Conclusion

En utilisant ces URLs et commandes, vous pouvez interagir avec les pages de l'application et tester les différentes fonctionnalités exposées par le contrôleur. Vous pouvez tester la création, la suppression, l'affichage des étudiants et leurs notes. Assurez-vous que le serveur est bien lancé sur le port 1500 pour que toutes ces fonctionnalités soient accessibles.
