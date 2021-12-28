# Info
**Student name:** Benjamin Clausen Bennetezn**

**Student Number:** 20204761?

**Study Programme and Semester:** Comp Sci 3rd semester

# Assignment 1. App Supporting Social Exercising
## Assignment 1.1 System Definition

- **F:** Users of the system can create event for specific exercise activities. Users can see other events and sign up for them. Users can specify time and if the event is reoccurring. The user will be able to set preferences for what they would like to do.
- **A:** A couple of volunteers from the non-profit will be admins on the system. Everyone will be able to use the system as a common user.
- **C:** Created by a non profit organization. Aim is to increase exercise amount for users. Developed by a software campany in collaboration with volunteers in the non-profit organization and prospective users.
- **T:** The system will be running on a server in the non-profit organization and clients will run the users' smartphones.
- **O:** Event, Trainee, Schedule
- **R:** The system is responsible for keeping track of all the events, when these take place and who have signed up for them. The system is responsible for recommending and encouraging events based on user preferences.

## Assignment 1.2
It is not specified whether or not you are automatically signed up for your own event occurrences, so i will assume that you or not.

|                                              | User | Event | Event Occurrence | Event Participation |
| :---                                         | :--: | :---: | :--------------: | :-----------------: |
| user registered (date)                       |  +   |       |                  |                     |
| user left community (date)                   |  +   |       |                  |          *          |
| event created (date, exercise type)          |  *   |  *    |                  |                     |
| event occurrence created (date, time, place) |  *   |  *    |        *         |                     |
| event occurrence happened                    |      |  *    |        +         |                     |
| event completed (date)                       |      |   +   |                  |                     |
| signup opened (date)                         |      |       |        +         |          +          |
| signup closed (date)                         |      |       |        +         |          +          |
| user signed up (date)                        |  *   |       |        *         |          *          |
| user signup cancelled (date)                 |  *   |       |        *         |          *          |
| user participated                            |  *   |       |        *         |                     |
| event occurrence rated (rating)              |  *   |       |        +         |                     |

## Assignment 1.3
### User
TODO user can only rate event they participated in

```plantuml
state join1 <<fork>>
state join2 <<fork>>

[*] -> Registered : user registered
Registered -> [*] : user left community
Registered -up-> join1
join1 -down-> Registered : user signed up
join1 -down-> Registered : user signup cancelled
join1 -down-> Registered : event created
Registered -down-> join2
join2 -up-> Registered : user participated
join2 -up-> Registered : event occurrence rated
join2 -up-> Registered : event occurrence created
```

### Event
```plantuml
state join1 <<fork>>
state join2 <<fork>>

[*] -> Created : event created
Created -down-> join1
join1 -up-> Created : event occurrence created
Created -> Started : event occurrence happened
Started -down-> join2
join2 -up-> Started : event occurrence happened
Started -> [*] : event completed
```

### Event Occurrence
```plantuml
state join1 <<fork>>
state join2 <<fork>>
state join3 <<fork>>

[*] -> Created : event occurrence created
Created -> Cancelable : signup opened
state Cancelable {
    [*] -> Opened
    Opened --> join1
    join1 --> Opened : user signed up
    Opened -> Closed : signup closed
    Closed --> join3
    join3 --> Closed : user participated
}
Cancelable --> join2
join2 --> Cancelable : user signup cancelled
Cancelable -> [*] : event occurrence happened
```

### Event Participation
```plantuml
state join1 <<fork>>
state join2 <<fork>>

[*] -> Opened : signup opened
Opened -up-> join1
join1 -down-> Opened : user signed up
join1 -down-> Opened : user signupcancelled
Opened -down-> join2
join2 -up-> Opened : user left community
Opened -> [*] : signup closed
```
# Assignment 2
## Assignment 2.1
A class is an abstraction of a collection of objects that we what to model. To quote Lecture 2 slide 4

> A description of a collection of objects sharing: Structure, behavioral pattern, and attributes.

## Assignment 2.2
An Object is a specific thing that we can see what has happened to and we can identify it. It could be that one specifc bed in ikea. To queto Lecture 2 slide 4.

> An entity with: Identity, state, and behavior.

## Assignment 2.3
A class is the abstraction we use to describe a collection of similar objects. Every objects in this class can be described using the attributes and behavioral patterns that we have given the class. With a class we can say that a bed starts by being build than transported to a shop and then sold. A bed has a price and a list of materials. An object in this class will be a specific bed that might be a bed that has been build and transported to a shop but has yet to be sold. It has a price of 5000 dkk, and is made with oak wood.

# Assignment 3
## Assignment 3.1
|                  |  PD  |  AP  | Both | neither |
| :--------------- | :--: | :--: | :--: | :-----: |
| Company          |      |  x   |      |         |
| Customer         |      |      |      |   x     |
| Container        |  x   |      |      |         |
| Sales department |      |  x   |      |         |
| Dispatcher       |      |  x   |      |         |
| Driver           |      |      |  x   |         |
| Task             |  x   |      |      |         |
| Server           |      |      |      |   x     |
| Mobile computer  |      |      |      |   x     |

## Assingment 3.2
- **F:** Sales department can created tasks. A dispatcher should be able to divide the task into assignment which entail source and target location as well as which containers, truck and which drivers or 2 drivers and when it is expected to be completed. Drivers should be able to report back with progress on their assignment.
- **A:** Company, Sales department, Dispatcher and Driver.
- **C:** The system will be developed by an external software company. The sales department, dispatchers and drivers will be involved in this process.
- **T:** The sales department and dispatcher will use PCs connected to a centralized server in the company's headquarter. Each driver will have a mobile computer.
- **O:** Container, Truck, Driver, Task, Assignment
- **R:** The system is responsible for keeping track and tasks and assignments. Who are involved in each assignment, drivers, truck and containers. It should also keep track of the progress of each assignment, when it started and when it ended.

## Assignment 3.3
```plantuml
class Truck {
    license plate
}

class Driver {
    employee id
}

class Container {
    bar code
}

class Task {
    task number
    description
}

class Assignment {
    assignment number
    start date
    expected end date
    end date
    source
    target
}

Task "1" *-- "1..*" Assignment
Task "1" *-- "1..*" Container

Assignment "1" *-- "1" Container
Assignment "1" *-- "1,2" Driver
Assignment "1" *-- "1" Truck
```

## Assingment 3.4
Look at actual solution

# Assignment 4

## Assignment 4.1
- [ ] The role pattern
- [ ] The relation pattern
- [x] The hierarchy pattern
- [x] The item-descriptor pattern
- [ ] The stepwise relation pattern
- [ ] The stepwise role pattern
- [ ] The composite pattern

## Assignment 4.2
|                        | Customer | Wine | Bottle |
| :------------------    | :------: | :--: | :----: |
| Joined club            | +        |      |        |
| Left club              | +        |      |        |
| Bottle ordered         | *        |      | *      |
| Bottle order cancelled | *        |      | *      |
| Bottle delivered       | *        |      | +      |
| Bottle paid            | *        |      |        |
| Wine included          |          | +    |        |
| Wine excluded          |          | +    |        |
| Bottle received        |          | *    |   +    |

## Assignment 4.3
Look at actual solution
