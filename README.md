# ontologies-project
````
University:
	Classes:
		University
		Person (Abstract)
		Student
		Professor
		Course
		Room
		Subject
	Data Properties: 
		University (ID, Name, Address)
		Person (Name, Email, Address, Age)
		Student (ID, Year, GPA, Type)
		Professor (ID, Field of study, Salary)
		Course (ID, Name)
		Room (ID, Size)
		Subject (ID, Name)
	Object Properties:
		Teaches in (Professor -> Universty)
		Teaches (Professor -> Class)
		Taken In (Course -> Room)
		Content (Course -> Subject)
		Attends (Student -> Class)
		Studies In (Student -> University)
````
