### Airline Flight Booking  
An airline operates **Flights** identified by a unique flight number. It also records the airline name, typical aircraft type, and scheduled duration in minutes. Each flight has many **Flight Instances** on specific dates. A flight instance records the date, scheduled departure and arrival times, and current status (on-time, delayed, or cancelled). Flights depart from and arrive at **Airports**, each identified by its airport code and also storing the airport name, city, country, and time zone. **Passengers** book seats on flight instances. Each passenger is identified by a unique identifier and also stores full name, passport number, nationality, date of birth, and email. Each booking records the seat number, fare class (economy/business/first), fare amount, booking date, and booking status. Every flight instance has a set of **Seats**, each distinguished by its seat number and also recording seat type (window/aisle/middle) and whether it is currently available.

<details>
<summary>Sample Solution</summary>

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