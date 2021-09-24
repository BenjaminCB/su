# Kajs Cars

## Notes from case description
System must support work activities related to.
- rental
- booking
- maintenance

Employees are part time with varying qualifications and computer literacy.

Lease agreements are for a SINGLE car

Cars are divided in price groups (A-D, A being the cheapest)

Customers are divided into private and corporate

System is accessed on PC at the counter

System is responsible for car stock and support the handling details related to rental agreement.

Fuel not included in price

Cash is allowed but not preferred

Booking in advance is encouraged

"Good" costumers might get a better car if no car is available

Business customers pay on a monthly basis, nor do they pay a deposit.

A reservation is not a rental, it is only a rental when the customer has picked it up.

When a car comes back within opening hours they handle fees with the customer, otherwise Kajs cars handle it themselves.

If there is visible damage to the car it is sent to the repair shop right away. Otherwise they go by normal service intervals, although they have have it set such that all A's are not gone at the same time.

You can not deliver the car at another location

Cars can be moved between offices

## Work process
- check for car availability in price range and time period
- information for lease, for that drivers license is needed
- agree on time period and insurance (you can insure both car and passengers)
- note car which has been picked
- pay deposit equal to expected price
- instruct customer if they do not know the car

# FACTOR
- F: The system can show both customers and employee which cars are in stock when and information about the specific car, price mileage etc, though employee should be able to see more information i.e who has rented the car, when is should the car have a maintenance check. Customers should be able to reserve cars and employee should be able to to see reserved cars and create a lease from that. Once a time period has been selected the system should be able to estimate a price which can be paid as a deposit.
- A: The system should be available through a website where customers can also login to gain access to their extra features.
- C: The description doesn't give much information about this, although we can say that the employees have a varying amount of computer literacy, so nothing to complicated.
- T: As stated the system will be a website. Data should also be backed up on a local server so that the shop should could continue even without internet.
- O: Employee, Car, Lease, Costumer, Reservation, Period
- R: The system is a tool that gives costumers and employees and overview of the cars, and helps in the rental process. Costumers can see which cars are available in the price ranges. Employees can see all the cars and their current status and when they should be services as well as help them fill out a lease properly.

# Classes
- Customer
- Car
- Station
- Agreement
    - Lease
    - Reservation
- Price group
    - A
    - B
    - C
    - D
- Schedule
    - Free
    - Repair
    - Other station
    - Rented

# Events
- Move
- Reserve
- Rent
- Deliver
- Repair

# Event Table
|         | Car | Customer | Station | Agreement | Price Group | Schedule |
| ------- | :-: | :------: | :-----: | :-------: | :---------: | :------: |
| Move    | x   |          | x       |           |             | x        |
| Reserve |     | x        |         | x         | x           |          |
| Rent    | x   | x        |         | x         |             | x        |
| Deliver | x   | x        |         |           |             |          |
| Repair  | x   |          |         |           |             | x        |

# Class Diagram
```plantuml
class Schedule
abstract class Period
class Free
class Repair
class Rented

Schedule "1" *-- "*" Period
Period <|-- Free
Period <|-- Repair
Period <|-- Rented

abstract class Agreement
class Lease
class Reservation

Agreement <|-- Lease
Agreement <|-- Reservation

class Station
class Car
class PriceGroup
class Customer

Station "1" *-- "*" Car
Station "1" *-- "*" Agreement
Car "1" *-- "1" Schedule
Car "*" *-- "1" PriceGroup

Reservation "*" *-- "1" Costumer
Reservation "*" *-- "1" PriceGroup

Lease "1" *-- "1" Customer
Lease "1" *-- "1" Car
```

```plantuml
[*] --> Free : Move into station
Free --> [*] : Move out of station

Free -> Repairing : Repair car
Repairing -> Free : Deliver

Free -left-> Rented : Rent car
Rented -> Free : Deliver
```
