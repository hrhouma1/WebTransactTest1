# WebTransactTest1

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
