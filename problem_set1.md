Here is a curated set of 12 realistic, self-contained scenarios for ER modeling practice. 

You must:

- Identify strong and weak entity types  
- Determine primary keys and partial keys
- Decide on relationships, cardinalities (1:1, 1:N, M:N), and participation constraints (total vs. partial)  
- Recognize ternary and higher-order relationships when they appear

### Scenario 1 – University Course Registration  
**Description**  
A university offers many **Courses**. Each course can be offered in multiple **Sections** during a semester. A section is taught by exactly one **Instructor** and can have many **Students** enrolled. Each student can enroll in many sections. An enrollment record stores the **grade** the student receives.

<details>
<summary>Solution</summary>

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

### Scenario 2 – Hospital Patient Management  
**Description**  
A hospital has **Patients** who are admitted by **Doctors**. Each patient can have multiple **Admissions**. During an admission a patient is assigned to exactly one **Ward** and can undergo many **Procedures**. Each procedure is performed by one doctor.

<details>
<summary>Solution</summary>

- Entities: **Patient**, **Doctor**, **Admission** (weak on Patient), **Ward**, **Procedure**  
- Relationships:  
  - **Admits** (Doctor 1 : N Admission) – total on Admission  
  - **AssignedTo** (Admission N : 1 Ward)  
  - **Undergoes** (Admission M : N Procedure)  
- Attributes:  
  - Patient: patientID (PK), name, DOB, insurance  
  - Admission: admissionDate (partial key), dischargeDate, reason  
  - Ward: wardID (PK), name, capacity  
  - Procedure: procedureCode (PK), name, cost  

</details>

### Scenario 3 – E-commerce Order System  
**Description**  
**Customers** place **Orders**. Each order contains one or more **OrderLines**, each corresponding to a single **Product**. A product can appear in many orders. Customers have multiple **Addresses** (billing, shipping, etc.).

<details>
<summary>Solution</summary>

- Entities: **Customer**, **Order** (weak on Customer), **OrderLine** (weak on Order), **Product**, **Address** (weak on Customer)  
- Relationships:  
  - **Places** (Customer 1 : N Order) – total on Order  
  - **Contains** (Order 1 : N OrderLine) – total on OrderLine  
  - **ForProduct** (OrderLine N : 1 Product)  
- Attributes:  
  - Customer: customerID (PK), name, email  
  - Order: orderID (partial key), orderDate, status  
  - OrderLine: quantity, unitPrice  
  - Product: productID (PK), name, price, stock  
  - Address: addressType (partial key), street, city, zip  
</details>

### Scenario 4 – Library Book Loans  
**Description**  
A library owns many **Books**. Each book can be loaned to **Patrons**. A loan has a due date and can be renewed. Books have multiple **Copies**; each copy is a distinct physical item.

<details>
<summary>Solution</summary>

- Entities: **Book**, **Copy** (weak on Book), **Patron**, **Loan** (weak on Copy + Patron)  
- Relationships:  
  - **HasCopy** (Book 1 : N Copy) – total on Copy  
  - **Borrows** (Patron M : N Copy) → **Loan** entity  
- Attributes:  
  - Book: ISBN (PK), title, edition  
  - Copy: copyNumber (partial key), condition  
  - Patron: patronID (PK), name, email  
  - Loan: loanDate (partial key), dueDate, renewalCount  

</details>

### Scenario 5 – Airline Flight Booking  
**Description**  
An airline operates **Flights** between **Airports**. Each flight instance has a specific date/time. A **Passenger** can book seats on multiple flights; each booking is for a specific seat on a specific flight instance.

<details>
<summary>Solution</summary>

- Entities: **Flight**, **FlightInstance** (weak on Flight), **Airport**, **Passenger**, **Booking** (weak on FlightInstance + Passenger), **Seat** (weak on FlightInstance)  
- Relationships:  
  - **Operates** (Flight 1 : N FlightInstance) – total  
  - **DepartsFrom / ArrivesAt** (FlightInstance N : 1 Airport)  
  - **Books** (Passenger M : N FlightInstance) → **Booking**  
- Attributes:  
  - Flight: flightNumber (PK), airline  
  - FlightInstance: date, departureTime (composite)  
  - Booking: seatNumber, fare  
</details>

### Scenario 6 – Social Media Platform  
**Description**  
**Users** create **Posts**. Each post can have many **Comments** and can be **Liked** by other users. A user can follow many other users. A comment can also be liked.

<details>
<summary>Solution</summary>

- Entities: **User**, **Post**, **Comment** (weak on Post), **Like** (weak on Post/Comment + User)  
- Relationships:  
  - **Creates** (User 1 : N Post) – total on Post  
  - **CommentsOn** (User 1 : N Comment) – total on Comment  
  - **Follows** (User M : N User) – recursive  
  - **Likes** (User M : N Post/Comment) → **Like** entity  
- Attributes:  
  - User: userID (PK), username, joinDate  
  - Post: postID (PK), content, timestamp  
  - Comment: commentID (partial key), text, timestamp  

</details>

### Scenario 7 – Real-Estate Agency  
**Description**  
An agency lists **Properties** (houses, apartments). Each property is owned by one or more **Owners** (joint ownership possible). A property can have multiple **Viewings** scheduled with prospective **Buyers**. A viewing is attended by one agent.

<details>
<summary>Solution</summary>

- Entities: **Property**, **Owner** (M:N via **Ownership**), **Buyer**, **Viewing** (weak on Property), **Agent**  
- Relationships:  
  - **Lists** (Agency implied, or add **Agency** entity)  
  - **Owns** (Property M : N Owner) → **Ownership** entity with ownershipPercent  
  - **Schedules** (Agent 1 : N Viewing)  
  - **Attends** (Buyer M : N Viewing)  
- Attributes:  
  - Property: propertyID (PK), address, type, price  
  - Owner: ownerID (PK), name  
  - Viewing: viewingDate, time  

</details>

### Scenario 8 – University Research Grants  
**Description**  
**Researchers** apply for **Grants** from **FundingAgencies**. A grant can support multiple researchers and multiple **Projects**. A project can be funded by multiple grants. Each grant has a start and end date and a budget.

<details>
<summary>Solution</summary>

- Entities: **Researcher**, **Grant**, **Project**, **FundingAgency**  
- Relationships:  
  - **AppliesFor** (Researcher M : N Grant)  
  - **Funds** (Grant M : N Project)  
  - **Employs** (Agency 1 : N Grant) – total on Grant  
- Attributes:  
  - Researcher: researcherID (PK), name, dept  
  - Grant: grantID (PK), title, startDate, endDate, amount  
  - Project: projectID (PK), title, budgetAllocated  

</details>

### Scenario 9 – Fitness Center Membership  
**Description**  
A fitness center has **Members** who can enroll in multiple **Classes** (yoga, spinning, etc.). Each class is taught by one **Trainer** and has a maximum capacity. Members can also book **PersonalTrainingSessions** with trainers.

<details>
<summary>Solution</summary>

- Entities: **Member**, **Class**, **Trainer**, **Enrollment** (weak on Class + Member), **PersonalSession** (weak on Member + Trainer)  
- Relationships:  
  - **Teaches** (Trainer 1 : N Class) – total on Class  
  - **EnrollsIn** (Member M : N Class) → **Enrollment**  
  - **Books** (Member M : N Trainer) → **PersonalSession**  
- Attributes:  
  - Member: memberID (PK), name, joinDate  
  - Class: classID (PK), name, schedule, capacity  
  - Trainer: trainerID (PK), name, specialization  

</details>

### Scenario 10 – Car Rental Company  
**Description**  
A car rental company owns a fleet of **Vehicles** (cars, vans). Each vehicle is assigned to exactly one **Branch** but can be rented to **Customers** for specific **RentalPeriods**. A rental can include optional **Insurance** and **AdditionalDrivers**.

<details>
<summary>Solution</summary>

- Entities: **Vehicle**, **Branch**, **Customer**, **Rental** (weak on Vehicle + Customer), **Insurance** (weak on Rental), **AdditionalDriver** (weak on Rental)  
- Relationships:  
  - **LocatedAt** (Vehicle N : 1 Branch) – total on Vehicle  
  - **Rents** (Customer M : N Vehicle) → **Rental** entity  
- Attributes:  
  - Vehicle: VIN (PK), make, model, year, status  
  - Rental: rentalID (partial key), startDate, endDate, totalCost  
  - Insurance: policyNumber, coverageType  

</details>

### Scenario 11 – Conference Paper Submission  
**Description**  
**Authors** submit **Papers** to **Conferences**. A paper can have multiple authors (order matters). Each conference has **Reviewers** who review multiple papers. A review has a score and comments. A paper can receive multiple reviews.

<details>
<summary>Solution</summary>

- Entities: **Author**, **Paper**, **Conference**, **Reviewer**, **Review** (weak on Paper + Reviewer)  
- Relationships:  
  - **Submits** (Author M : N Paper) with order attribute on relationship  
  - **Holds** (Conference 1 : N Paper)  
  - **Reviews** (Reviewer M : N Paper) → **Review**  
- Attributes:  
  - Paper: paperID (PK), title, abstract, submissionDate  
  - Review: score, comments, reviewDate  

</details>

### Scenario 12 – Online Learning Platform  
**Description**  
**Instructors** create **Courses** on a platform. Each course has **Modules**, each module has **Lessons** and **Quizzes**. **Students** enroll in courses, watch lessons, and take quizzes. A quiz attempt records the **Score**.

<details>
<summary>Solution</summary>

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
