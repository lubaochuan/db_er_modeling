### Hospital Patient Management  
A hospital keeps complete profiles on every **Patient**, recording a unique patient identifier, full name, date of birth, gender, complete address, phone number, insurance provider, and policy number. Patients are admitted by **Doctors**. For each doctor the hospital stores a unique identifier, name, medical specialty, phone, email, and office location. Every admission is recorded with the admission date (which distinguishes one admission from another for the same patient), discharge date, reason for admission, assigned room number, and a derived total cost. During an admission a patient is assigned to exactly one **Ward**. Each ward has a unique identifier, name, floor, capacity, and a derived current occupancy. While admitted, a patient may undergo many **Procedures**; each procedure is identified by a unique procedure code and also stores its name, description, standard cost, and typical duration in minutes. Every procedure is performed by one doctor.

<details>
<summary>Sample Solution</summary>

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