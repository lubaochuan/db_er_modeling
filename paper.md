### Conference Paper Submission  
**Authors** submit **Papers** to **Conferences**. Each author has a unique identifier, full name, email, institutional affiliation, and country. Each paper is identified by a unique paper identifier and stores its title, abstract, submission date, one or more keywords, page count, and current status (submitted, under review, accepted, or rejected). A paper can have multiple authors; the submission relationship records the order of authors on the paper. Conferences are identified by a unique identifier and also store the conference name, year, location, submission deadline, and notification date. Papers are reviewed by **Reviewers**. Each reviewer has a unique identifier, full name, email, affiliation, and one or more areas of expertise. Each review records a numeric score (1–10), written comments, the review date, and the reviewer’s recommendation (accept or reject).

<details>
<summary>Sample Solution</summary>

- Entities: **Author**, **Paper**, **Conference**, **Reviewer**, **Review** (weak on Paper + Reviewer)  
- Relationships:  
  - **Submits** (Author M : N Paper) with order attribute on relationship  
  - **Holds** (Conference 1 : N Paper)  
  - **Reviews** (Reviewer M : N Paper) → **Review**  
- Attributes:  
  - Paper: paperID (PK), title, abstract, submissionDate  
  - Review: score, comments, reviewDate  

</details>