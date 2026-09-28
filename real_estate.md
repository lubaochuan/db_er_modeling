### Real-Estate Agency  
A real-estate agency lists **Properties**. Each property is identified by a unique property identifier and stores its full address, property type (house, apartment, condo, or land), square footage, number of bedrooms, number of bathrooms, list price, current status (listed, sold, or off-market), and listing date. Properties can have multiple **Owners** (joint ownership is common). Each owner has a unique identifier, full name, email, and phone; the ownership relationship also records the ownership percentage. Prospective **Buyers** view properties. Each buyer is identified by a unique identifier and stores full name, email, phone, and budget range. Viewings are scheduled for specific properties. Each viewing records the date, start and end times, and any notes. Every viewing is conducted by exactly one **Agent**. Agents are identified by a unique identifier and also store full name, email, phone, and commission rate.

<details>
<summary>Sample Solution</summary>

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
