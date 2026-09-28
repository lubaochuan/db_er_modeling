### Fitness Center Membership  
A fitness center maintains records on its **Members**. Each member has a unique identifier, full name, email, phone, join date, membership type (monthly or annual), and membership status (active or suspended). Members may enroll in **Classes** (yoga, spinning, etc.). Each class is identified by a unique identifier and also stores the class name, description, weekly schedule (day and time), duration in minutes, maximum capacity, and current number of enrolled members (derived). Every class is taught by exactly one **Trainer**. Trainers have a unique identifier, full name, email, phone, area of specialization, and certification date. When a member enrolls in a class, the enrollment record stores the enrollment date and a derived attendance count. Members may also book **Personal Training Sessions** with trainers. Each session records the date, start and end times, any notes, and the hourly rate charged.

<details>
<summary>Sample Solution</summary>

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