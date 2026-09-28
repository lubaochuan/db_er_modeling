### University Research Grants  
**Researchers** apply for **Grants** funded by **Funding Agencies**. Each researcher is identified by a unique identifier and also stores full name, email, department, and academic title. Each grant is identified by a unique grant identifier and records its title, the funding agency, start and end dates, total funding amount, and current status (active or closed). Grants support one or more **Projects**. Each project is identified by a unique identifier and stores its title, description, start and end dates, and the portion of the grant budget allocated to it. Funding agencies are identified by a unique agency identifier and also store the agency name, contact email, and website.

<details>
<summary>Sample Solution</summary>

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