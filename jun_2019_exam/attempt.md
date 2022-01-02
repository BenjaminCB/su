# Assignment 1
## Assignment 1.1
| F | A | C | T | O | R |
|:-:|:-:|:-:|:-:|:-:|:-:|
|   | x |   |   |   |   |
|   |   |   |   | x |   |
| x |   |   |   |   |   |
|   | x |   |   |   |   |
|   |   |   |   | x |   |
|   |   |   |   | x |   |
|   | x |   |   |   |   |
| x |   |   |   |   |   |
| x |   |   |   |   |   |
| x |   |   |   |   |   |
|   |   |   |   |   | x |
|   |   | x |   |   |   |
|   |   |   | x |   |   |
|   |   | x |   |   |   |

## Assignment 1.2
```plantuml
class Club {
    name
    address
}

abstract class Member {
    name
    address
}

class Passive

class Active

class BoatSpot {
    position (x,y)
}

class Boat {
    name
    length
    width
}

abstract class Invoice {
    due date
    payment date
    amount
}

class MemberInvoice
class BoatSpotInvoice

Member <|-- Passive
Member <|-- Active

Invoice <|-- MemberInvoice
Invoice <|-- BoatSpotInvoice

Club "1..*" *-- "0..*" Member
Club "1" *-- "1..*" BoatSpot

Member "1" *-- "0..*" Boat
Member "1" *-- "0..*" Invoice
Member "1" *- "0..*" BoatSpot

BoatSpot -- BoatSpotInvoice
```

# Assignment 2
## Assignment 2.1
|                               |  PD  |  AD  | Both | Neither |
| ----------------------------- | :--: | :--: | :--: | :-----: |
| S-Food                        |      |      |      |    x    |
| Madforretning                 |  x   |      |      |         |
| Bar                           |  x   |      |      |         |
| Kunde                         |      |      |  x   |         |
| Administrativt personale      |      |  x   |      |         |
| Personale i forretning og bar |      |  x   |      |         |
| Måltid                        |  x   |      |      |         |
| Ordre                         |  x   |      |      |         |
| Madvare                       |  x   |      |      |         |
| Drikkevare                    |  x   |      |      |         |
| Kreditkort                    |  x   |      |      |         |
| IT-afdeling                   |      |      |      |   x     |
| Smartphone                    |      |  x   |      |         |
| Server                        |      |      |      |   x     |
| Bord                          |  x   |      |      |         |
| Stol                          |      |      |      |   x     |

## Assignment 2.2
### Customer
- Goal: The goal of the customer is to get a meal which will be delivered to their table.
- Characteristics: This could be anyone which have a smartphone and a credit card. Their IT skills will therefore be very varying.
- Example: Customer A is an IT student eating out with their friends. A finds it quite easy to use their phone a uses it quite a bit in their spare time.

    Customer B is retired and only received a smartphone. B is out eating with their family and needs quite a lot of help using their newly acquired phone.

### Employee
- Goal: The goal of the employee is to see the latest orders, such that they can make it and satisfy the customer.
- Characteristics: Most likely young adults looking for part time jobs, but most people could do the job, therefore it skills will vary, though they will use the system a lot allowing them to learn it.
- Example: Employee A is an IT student and was just hired, A does not have much trouble using the system. Unlike their co-worker Employee B who was hired 3 weeks ago and is just now getting the hang of it.

### Admin
- Goal: The goal of the admin is to see how much well things are going. That is to say how much profit that has been made.
- Characteristics: To acquire an administrative position we have to assume that they have showed some form of qualifications.
- Example: Admin A uses the system to today's total profit, while Admin B checks everything that Customer A bought within the last month.

## Assignment 2.3
|                                           | Customer | Employee | Admin |
| ----------------------------------------- | :------: | :------: | :---: |
| Registrere som ny kunde                   |    x     |          |       |
| Sammensætte et måltid og betale for det   |    x     |          |       |
| Udtrække ledelsesinformation om omsætning |          |          |   x   |
| Udtrække information om enkeltkunders køb |          |          |   x   |

## Assignment 2.4
```plantuml
[*] -> Meal : New meal
Meal -> AwaitingCode : prompt 3 digit code
AwaitingCode -> Invoice : enter code
Invoice -> [*] : exit
Meal --> ShopList : new order
ShopList -> Order : choose shop
Order -> Meal : confirm order
Order -> Menu : new item
Menu -> Order : pick item
```

## Assignment 2.5
| Function name    | Complexity | Function type  |
| ---------------- | :--------: | :------------: |
| NewMeal          | Medium     | Update         |
| NewOrder         | Medium     | Update         |
| GetShops         | Simple     | Read           |
| GetMenu          | Simple     | Read           |
| AddToOrder       | Simple     | Update         |
| AddToMeal        | Simple     | Update         |
| RegisterCustomer | Medium     | Update         |
| RegisterCard     | Medium     | Update         |
| Pay              | Complex    | Signal         |
| TotalPrice       | Simple     | Calculate+Read |
| GetPurchases     | Simple     | Read           |
| Profit           | Simple     | Calculate+Read |

## Assignment 2.6
For this a client server architecture would be fitting seeing as customer use their smartphone to connect to a server. The shops will want to use the system even though they might not have any internet so a distributed data will be useful for them. We will base this in the generic architecture. Though i suspect will should use multiple different client components.

```plantuml
package Client {
    package ClientInterface {
        package ClientUserInterface
        package ClientSystemInterface
    }

    package ClientFunction
    package ClientModel
    package ClientTechnicalPlatform
}

package Server {
    package ServerInterface {
        package ServerSystemInterface
        package ServerUserInterface
    }

    package ServerFunction
    package ServerModel
    package ServerTechnicalPlatform
}

ClientSystemInterface .> ServerSystemInterface
ServerSystemInterface .> ClientSystemInterface

ClientSystemInterface ..> ClientFunction
ClientSystemInterface ..> ClientTechnicalPlatform
ClientUserInterface ..> ClientFunction
ClientUserInterface ..> ClientTechnicalPlatform
ClientFunction ..> ClientModel
ClientModel ..> ClientTechnicalPlatform

ServerSystemInterface ..> ServerFunction
ServerSystemInterface ..> ServerTechnicalPlatform
ServerUserInterface ..> ServerFunction
ServerUserInterface ..> ServerTechnicalPlatform
ServerFunction ..> ServerModel
ServerModel ..> ServerTechnicalPlatform
```

# Assignment 3
## Assignment 3.1
|                                | Kunde | Faktura | Film |
| ------------------------------ | :---: | :-----: | :--: |
| indmeldt (dato)                | +     |         |      |
| udmeldt (dato)                 | +     |         |      |
| faktura modtaget (dato,beløb)  | *     | +       |      |
| faktura betalt (dato, beløb)   | *     | +       |      |
| film valgt (dato, tid)         | *     | *       | *    |
| periode startet (måned)        |       | +       |      |
| periode sluttet (måned)        |       | +       |      |
| film stoppet (dato, tid)       |       | *       | *    |
| film sluttet (dato, tid)       |       | *       | *    |
| film indkøbt                   |       |         | +    |
| film slettet                   |       |         | +    |
| film startet                   |       |         | *    |

## Assignment 3.2
```plantuml
class Kunde {
    navn
    adresse
    indmeldt
    udmeldt
}

class Faktura {
    år
    måned
    state { startet | sluttet | modtaget | betalt }
}

class Film {
    nummer
    titel
    varighed
}

class FilmItem {
    startet
    sluttet
    stoppet
    valgt
}

Kunde "1" *-- "0..*" Faktura
Faktura "0..*" *-- "0..*" FilmItem
Kunde "0..*" *-- "0..*" FilmItem
Film "1" *-- "0..*" FilmItem

```
