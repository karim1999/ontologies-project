# University Project
## Project Statement

## Classes
````
University
Person (Abstract)
Student
Professor
Course
Room
Subject
````

## Data Properties
````
University (ID, Name, Address)
Person (Name, Email, Address, Age)
Student (ID, Year, GPA, Type)
Professor (ID, Field of study, Salary)
Course (ID, Name)
Room (ID, Size)
Subject (ID, Name)
````
## Object Properties
````
Teaches in (Professor -> Universty)
Teaches (Professor -> Class)
Taken In (Course -> Room)
Content (Course -> Subject)
Attends (Student -> Class)
Studies In (Student -> University)
````
## Queries
### List all Ain Shams Undergraduate Students
````
SELECT ?ID ?Name WHERE {
?Student a uri:Student .
?Student uri:Studies_In ?University .
?University uri:Name "Ain Shams" .
?Student uri:Type "Undergraduate" .
?Student uri:Name ?Name .
?Student uri:ID ?ID .
}
````
### List all Ain Shams Graduate Students that have GPA greater than 2
````
SELECT ?ID ?Name ?GPA WHERE {
?Student a uri:Student .
?Student uri:Studies_In ?University .
?University uri:Name "Ain Shams" .
?Student uri:Type "Graduate" .
?Student uri:GPA ?GPA .
?Student uri:Name ?Name .
?Student uri:ID ?ID .
FILTER (?GPA >= 2)
}
````
### List all Ain Shams professors that teaches Geometry
````
SELECT ?ID ?Name WHERE {
?Professor a uri:Professor .
?Professor uri:Teaches_in ?University .
?University uri:Name "Ain Shams" .
?Professor uri:Teaches ?Course .
?Course uri:Name "Geometry" .
?Professor uri:Name ?Name .
?Professor uri:ID ?ID .
}
````
### List all Ain Shams professors that teaches A Math Class
````
SELECT ?ID ?Name WHERE {
?Professor a uri:Professor .
?Professor uri:Teaches_in ?University .
?University uri:Name "Ain Shams" .
?Professor uri:Teaches ?Course .
?Course uri:Content ?Subject .
?Subject uri:Name "Math" .
?Professor uri:Name ?Name .
?Professor uri:ID ?ID .
}
````
### List all Ain Shams students that take classes in Rooms that can take more than 150 students
````
SELECT ?ID ?Name ?Size WHERE {
?Student a uri:Student .
?Student uri:Studies_In ?University .
?University uri:Name "Ain Shams" .
?Student uri:Attends ?Course .
?Course uri:Taken_In ?Room .
?Room uri:Size ?Size .
?Student uri:Name ?Name .
?Student uri:ID ?ID .
FILTER (?Size >= 150)
}
````
