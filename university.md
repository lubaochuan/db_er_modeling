
### University Course Registration  
A university maintains detailed records of the **Courses** it offers. For every course the university stores a unique course identifier, the course title, the number of credit hours, the offering department, and an optional description. Each course is offered in one or more **Sections** during a semester. A section is identified by its section number within the course and also records the semester, year, seating capacity, room number, and a composite meeting time (day of the week, start time, and end time). Every section is taught by exactly one **Instructor**, and the university keeps the instructor’s unique identifier, full name (first and last), email address, phone number, department, and office location. Students enroll in sections. The university stores each **Student**’s unique identifier, full name, email, major, year in school, and a derived GPA. Each enrollment record captures the date the student enrolled and the grade the student ultimately receives.

<details>
<summary>Sample Solution</summary>

- Entity types: **Course**, **Section** (weak, depends on Course), **Instructor**, **Student**, **Enrollment** (weak, depends on Section + Student)  
- Relationships:  
  - **Offers** (Course 1 : N Section) – total participation on Section side  
  - **Teaches** (Instructor 1 : N Section) – total on Section  
  - **Enrolls** (Student M : N Section) → represented by **Enrollment** entity  
- Attributes:  
  - Course: courseID (PK), title, credits  
  - Section: sectionNumber (partial key), semester, year  
  - Instructor: instructorID (PK), name, dept  
  - Student: studentID (PK), name, major  
  - Enrollment: grade  
</details>