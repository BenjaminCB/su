# Assignment 1
## Assignment 1.1
| F | A | C | T | O | R |
|:-:|:-:|:-:|:-:|:-:|:-:|
|   |   |   |   |   | x |
|   |   |   |   | x |   |
|   |   |   | x |   |   |
| x |   |   |   |   |   |
|   |   |   |   | x |   |
| x |   |   |   |   |   |
|   | x |   |   |   |   |
| x |   |   |   |   |   |
|   |   |   | x |   |   |
|   |   | x |   |   |   |

## Assignment 1.2
|                           |  PD  |  AD  | Both | Neither |
| ------------------------- | :--: | :--: | :--: | :-----: |
| Administrative personnel  |      |  x   |      |         |
| Club member               |      |      |   x  |         |
| Club house                |   x  |      |      |         |
| Guest                     |      |      |   x  |         |
| Boat slip                 |   x  |      |      |         |
| Boat                      |   x  |      |      |         |
| Crane for boats           |      |      |      |    x    |
| Payment for visit         |   x  |      |      |   (x)   |
| Sensor on boat slip       |   x  |      |      |         |
| List of vacant boat slips |   x  |      |      |         |
| Payment of membership fee |   x  |      |      |   (x)   |
| Software company          |      |      |      |    x    |
| Smartphone                |      |  x   |      |         |
| Crew on boat              |      |      |      |    x    |

## Assignment 1.3
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

class MembershipFee {
    invoice date
    payment deadline
    amount
}

class BoatSlip {
    dock
    slip number
}

class BoatSlipFee {
    invoice date
    payment deadline
    amount
}

class Boat {
    name
    length
    width
}

abstract class MemberWithBoat

class Guest {
    arrival date
    departure date
}

Club "1" *-- "0..*" Member
Club "1" *-- "0..*" BoatSlip
Member "1" *-- "0..*" MembershipFee
Member <|-- Passive
Member <|-- MemberWithBoat
MemberWithBoat <|-- Active
MemberWithBoat <|-- Guest
BoatSlip "1" *-- "0..*" BoatSlipFee
MemberWithBoat "1" *-right- "0..*" Boat
Boat "1" *-- "0..*" BoatSlipFee
```

# Assignment 2
## Assignment 2.1
### Customer
```plantuml
```
### Meal

### Order

## Assignment 2.2
|                   | Customer | Meal | Order |
| ----------------- | :------: | :--: | :---: |
| customer joined   |    +     |      |       |
| customer left     |    +     |      |       |
| meal started      |    *     |  +   |       |
| meal finished     |    *     |  +   |       |
| order started     |    *     |  *   |   +   |
| add item to order |    *     |      |   *   |
| add order to meal |    *     |  *   |   +   |
| cancel order      |    *     |      |   +   |
| cancel meal       |    *     |  +   |       |

## 2.3
