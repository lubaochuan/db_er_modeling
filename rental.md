### Car Rental Company  
A car rental company owns a fleet of **Vehicles**. Each vehicle is identified by its unique VIN and also stores make, model, year, color, current mileage, operational status (available, rented, or in maintenance), and daily rental rate. Every vehicle is permanently assigned to one **Branch**. Each branch has a unique identifier, name, full address, phone number, and manager name. **Customers** rent vehicles. Each customer has a unique identifier, full name, email, phone, driver’s license number, and the last four digits of their credit card. Each rental is recorded with a rental identifier (unique within the vehicle’s history), start and end dates, pickup and return branches, and a derived total cost. A rental may include optional **Insurance**; each insurance record stores the policy number, coverage type, and daily premium. A rental may also list **Additional Drivers**; each additional driver record stores the driver’s full name, driver’s license number, and relationship to the primary renter.

<details>
<summary>Sample Solution</summary>

- Entities: **Vehicle**, **Branch**, **Customer**, **Rental** (weak on Vehicle + Customer), **Insurance** (weak on Rental), **AdditionalDriver** (weak on Rental)  
- Relationships:  
  - **LocatedAt** (Vehicle N : 1 Branch) – total on Vehicle  
  - **Rents** (Customer M : N Vehicle) → **Rental** entity  
- Attributes:  
  - Vehicle: VIN (PK), make, model, year, status  
  - Rental: rentalID (partial key), startDate, endDate, totalCost  
  - Insurance: policyNumber, coverageType  

</details>