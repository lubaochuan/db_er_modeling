### Online Learning Platform  
**Instructors** create **Courses** on the platform. Each instructor is identified by a unique identifier and stores full name, email, a short bio, and areas of expertise. Each course is identified by a unique course identifier and also records the course title, description, category, difficulty level (beginner, intermediate, or advanced), typical duration in weeks, price, and a derived average rating. Every course is divided into **Modules**. A module is distinguished within its course by its module number and also stores a title, description, and its order within the course. Each module contains one or more **Lessons** and **Quizzes**. A lesson is identified by its lesson number within the module and records its title, content type (video or text), duration in minutes, and an optional video URL. A quiz is identified by its quiz number within the module and stores its title, number of questions, passing score, and time limit in minutes. **Students** enroll in courses. Each student has a unique identifier, full name, email, join date, and a derived count of courses enrolled in. An enrollment record stores the enrollment date, a derived progress percentage, and an optional completion date. Students take quizzes; each **Quiz Attempt** records the attempt date, score achieved, time taken, and whether the attempt was a pass or fail (derived).

<details>
<summary>Sample Solution</summary>

- Entities: **Instructor**, **Course**, **Module** (weak on Course), **Lesson** (weak on Module), **Quiz** (weak on Module), **Student**, **Enrollment** (weak on Course + Student), **QuizAttempt** (weak on Quiz + Student)  
- Relationships:  
  - **Creates** (Instructor 1 : N Course) – total on Course  
  - **Contains** (Course 1 : N Module) – total on Module  
  - **Enrolls** (Student M : N Course) → **Enrollment**  
  - **Attempts** (Student M : N Quiz) → **QuizAttempt** with score  
- Attributes:  
  - Course: courseID (PK), title, description  
  - Module: moduleNumber (partial key), title  
  - Lesson: lessonNumber (partial key), title, duration  
  - Quiz: quizNumber (partial key), passingScore  
  - QuizAttempt: attemptDate, score  

</details>