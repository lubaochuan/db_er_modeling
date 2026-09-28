### Library Book Loans  
A library owns many **Books**. Each book is identified by its ISBN and also stores the title, edition, publisher, publication year, language, and number of pages. Every book exists in one or more physical **Copies**. A copy is distinguished by its copy number within the book and also records its condition (new/good/fair/poor), acquisition date, and current location (branch and shelf). **Patrons** borrow copies. Each patron has a unique identifier, full name, email, phone, membership start date, and membership type. Each loan is recorded with the loan date (which distinguishes one loan from another), due date, optional return date, number of renewals, and a derived fine amount.

<details>
<summary>Sample Solution</summary>

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