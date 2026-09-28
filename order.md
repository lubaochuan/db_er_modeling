### E-commerce Order System  
An online retailer tracks every **Customer** with a unique customer identifier, full name, email address, phone number, and registration date. Customers place **Orders**. Each order is distinguished within a customer’s history by an order identifier and also records the order date, current status (pending, shipped, or delivered), and a derived total amount. Every order consists of one or more **OrderLines**, each of which records the quantity ordered, the unit price at the time of the order, and a derived line total. Each order line is linked to exactly one **Product**. Products are identified by a unique product identifier and also store the product name, description, category, list price, current stock level, and reorder level. Customers maintain multiple **Addresses** (billing, shipping, etc.). Each address records its type, street, city, state, zip code, and country.

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
