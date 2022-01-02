# Assignment 1
## Assignment 1.1
- F: The system can register a new customer  with credit card information, compose a meal with a number of orders for food shops and bars,  select food or drink items in each order of a meal, make payment of a meal, and register the table  where a customer wants his/her orders delivered.
- A: A system provided as an app, which is used by customers who want to order food and drinks at  the street food market operated by S-Food. The customers come to S-Food on their own  initiative, and their only relation to S-Food is that they download and use the app to order and  pay for food and drinks.
- C: The app will be developed by S-Food’s own IT department in cooperation with  S-Food’s sales department, the food shops and bars, and a few customers that will be selected to  represent the whole customer segment. It may be necessary to resolve conflicting requirements  between these different groups. The app will be used by users with very different levels of IT  skills.
- T: The app is running on each customer’s  smartphone. It communicates through a wireless network with a server that registers what the individual customer has ordered and paid. On the smartphone, there is always a copy of all meals  from the current day, so they are available if the wireless network should fail. The app includes a  QR code reader.
- O: Customer, Order, Meal, Table, Foddshop, bar
- R: The system is primarily an administrative tool that is responsible for  registering all customers and their orders, and facilitating secure payment of these with the  customers’ credit cards. Secondarily, it is a communication medium that customers use to  request delivery of orders from the food shops and bars.

## Assignment 1.2
```plantuml
class Table
class Customer
class Meal
abstract class Item
class FoodItem
class DrinkItem
class Order

Customer "1" *-- "0..*" Meal
Meal "1" *-- "1..*" Order
Meal "0..*" *-- "1" Table
Order "0..*" -- "1" Table
Order "1" *-- "1..*" Item
Item <|-- FoodItem
Item <|-- DrinkItem
```

# Assignment 2
## Assignment 2.1
### AP

**Definition:** The organization that administrates, monitors, or controls a problem.

**Example:** In the context that would be the customer which can use the system to join the club and then order wine until they eventually leave the club.

### PD
**Definition:** That part of a context that is administrated, monitored, or controlled by a system.

**Example:** In this context all classes from the class diagram are problem domain objects. We keep track of all them. As an example we keep track of when a customer orders a bottle, if said bottle has been delivered. And we keep track if which wine is in stock.

## Assignment 2.2
|                                  | Customer | Employee |
| :------------------------------- | :------: | :------: |
| Join as a new member             |    x     |          |
| Leave as a member                |    x     |          |
| Include wine in the assortment   |          |    x     |
| Exclude wine from the assortment |          |    x     |
| Register bottle(s) received      |          |    x     |
| Order bottle(s) of wine          |    x     |          |
| Cancel bottle order(s)           |    x     |          |
| Register delivery of bottle(s)   |          |    x     |

## Assignment 2.3
| Function name     | Complexity | Function Type |
| ----------------- | :--------: | :-----------: |
| Create Member     | Medium     | Update        |
| Retire Member     | Medium     | Update        |
| Include Wine      | Simple     | Update        |
| Exclude Wine      | Simple     | Update        |
| Register Bottle   | Medium     | Update        |
| Cancel Order      | Simple     | Update        |
| Register Delivery | Simple     | Update        |

## Assignment 2.4
Have not done this completely right just going to check actual solution.

# Assignment 3
## Assignment 3.1
| Patterns        | Classes connected                 |
| :------:        | --------------------------------- |
| Role Pattern    | Consumption, Watched, Listened to |
| Hierarchy       | Customer, Invoice, Consumption    |
| Hierarchy       | Album, Song, Listened to          |
| Item-descriptor | Movie, Watched                    |
| Item-descriptor | Song, Listened to                 |

## Assignment 3.2
|                   | Customer | Invoice | Watched | Listened to | Movie | Song | Album |
| ----------------- | :------: | :-----: | :-----: | :---------: | :---: | :--: | :---: |
| movie selected    |    *     |         |         |             |   *   |      |       |
| song selected     |    *     |         |         |             |       |  *   |       |
| movie ended       |          |         |    +    |             |       |      |       |
| song ended        |          |         |         |      +      |       |      |       |
| movie started     |          |         |    +    |             |       |      |       |
| song started      |          |         |         |      +      |       |      |       |
| movie cancelled   |    *     |         |    +    |             |       |      |       |
| song cancelled    |    *     |         |         |      +      |       |      |       |
| movie acquired    |          |         |         |             |   +   |      |       |
| song acquired     |          |         |         |             |       |  +   |       |
| album acquired    |          |         |         |             |       |      |   +   |
| movie deleted     |          |         |         |             |   +   |      |       |
| song deleted      |          |         |         |             |       |  +   |       |
| album deleted     |          |         |         |             |       |      |   +   |
| invoice generated |    *     |    +    |         |             |       |      |       |
| customer joined   |    +     |         |         |             |       |      |       |
| customer left     |    +     |         |         |             |       |      |       |
| invoice paid      |    *     |    +    |         |             |       |      |       |
| invoice time      |    *     |    +    |         |             |       |      |       |

## Assignment 3.3
### Customer
```plantuml
state join1 <<fork>>

[*] -> Included : customer joined
Included -up-> Excluded : Invoice time
Excluded -down-> Included : Invoice paid
Included --> [*] : customer left
Included -> join1
join1 -> Included : cunsumption selected
join1 -> Included : consumption cancelled
join1 -> Included : invoice generated
join1 -> Included : Invoice paid
```

### Invoice
```plantuml
[*] -> Generated : invoice generated
Generated -up-> Unpaid : invoice timeout
Generated -> [*] : invoice paid
Unpaid -> [*] : invoice paid
```
### Consumption
this is simple enough i will skip

# Assignment 4
## Assignment 4.1
Client server with distributed functionality everybody needs to access some public information and in this day and age most people have access to internet on their phones no matter where they are.

will just look at solution far architecture design.
