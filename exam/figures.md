```plantuml
class Passenger {
    name
}

class Shipment

class Baggage {
    QR code
    state { registered | under way | arrived }
}

class Flight {
    route
    date
    departure airport
    arrival airport
}

class Airport {
    name
    location
}

abstract class AirportUse {
    date
    start time
    end time
    gate number
}

class Arrival {
    arrival time
}

class Departure {
    departure time
}

class BaggageCarousel

AirportUse <|-- Arrival
AirportUse <|-- Departure

Airport "1" *-- "1..*" BaggageCarousel
Airport "1" *-- "0..*" AirportUse

Arrival "0..*" *-- "1" BaggageCarousel

Passenger "1" *-- "0..*" Shipment
Shipment "1" *-- "1..*" Baggage

Flight "1..*" *-- "0..*" Passenger
Flight "1" *-- "0..*" Shipment

AirportUse "2" *-- "1" Flight
```

```plantuml
state join1 <<fork>>

[*] -> Active : starts using system
Active --> Passive : stops using system
Active -> join1
join1 -> Active : arrival
join1 -> Active : departure
join1 -> Active : bill sent to customer
join1 -> Active : bill sent to debt collection
join1 -> Active : bill paid

Passive --> Active : starts using system
Passive -> [*] : ???
```

```plantuml
state join <<fork>>
[*] --> Active : acquired
Active --> [*] : not used
Active -> join
join -> Active : arrival restaurant
join -> Active : departure restaurant
```

```plantuml
[*] --> Consuming : arrival restaurant
Consuming -> Consuming : register food
Consuming --> [*] : departure restaurant
```

```plantuml
state join <<fork>>
[*] --> Customer : arrival
Customer --> [*] : not visited

Customer --> AtRestaunrant : arrival restaurant
AtRestaunrant --> Customer : departure restaunrant
AtRestaunrant --> AtRestaunrant : register food

Customer -> join
join -> Customer : arrival
join -> Customer : departure

```

```plantuml
state Closed {
    [*] --> Reminder : sent bill to customer
    Reminder -> Reminder : sent bill to customer
    Reminder --> Debt : sent bill to debt collection
}

[*] -> Open : arrival
Open -> Open : departure restaurant
Open --> Closed : departure

Closed -> [*] : bill paid

```

```plantuml
state Creation {
    [*] --> ShowShopList
    ShowShopList --> Shipment : choose shop
    Shipment -> ShowProducts : add product
    ShowProducts -> Shipment : choose product
    ShowProducts -> Shipment : cancel product
    Shipment --> Shopper : shipment finished
    Shopper -> ShopperForm : new shopper
    Shopper -> ShopperList : existing shopper
    ShopperForm --> ShowDeliveryOptions : fill in customer information
    ShopperList --> ShowDeliveryOptions : choose shooper
    ShowDeliveryOptions --> BookingOverview : choose delivery position
}
[*] -> APSHomePage : open website
APSHomePage -> Creation : new booking
Creation -> [*] : cancel booking
Creation -> [*] : booking complete
```
