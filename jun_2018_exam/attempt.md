# Assignment 1
## Assignment 1.1
- F: De administrativt  ansatte kan registrere en studerende med kategori, registrere en lærer og knytte en lærer  til en kategori af studerende. Administrativt ansatte, lærere og studerende kan se, hvilken  kategori en studerende er og hvilken kategori af studerende en lærer er knyttet til.
- A: Et IT‐system til administration af relationen mellem lærere og studerende. Systemet skal  bruges på en uddannelsesinstitution, hvor der er studerende i to kategorier  (fultidsstuderende og deltidsstuderende), samt lærere, som er lærere for enten den ene  eller anden kategori af studerende. Systemet skal bruges af dels administrativt personale,  der er ansat på uddannelsesinstitutionen, dels lærere og studerende.
- C: Systemet udvikles af et eksternt softwarefirma i samarbejde med de  administrativt ansatte og en udvalgt lærer og studerende.
- T: Det skal køre på en PC‐platform,  som allerede anvendes i administrationen, samt på studerende og læreres mobiltelefoner.
- O: Student, Teacher, Category
- R: Målet  med systemet er at få klarhed over de studerendes kategori og lærernes tilknytning til en  kategori af studerende og at give administrativt ansatte, lærere og studerende adgang til  denne information.

## Assignment 1.2
- [ ] Der er objekter af klassen Person
- [x] Der er objekter af klassen Lærer
- [x] Der er objekter af klassen Studerende
- [ ] Der er objekter af klassen Kategori
- [x] Der er et objekt af klassen Fuldtids
- [ ] Der er mange objekter af klassen Fuldtids
- [x] En studerende har et objekt enten af klassen Fuldtids eller klassen Deltids
- [ ] En studerende kan have både et objekt af klassen Fuldtids og et objekt af klassen Deltids

## Assignment 1.3
```plantuml
abstract class Person {
    name
}

class Teacher

class Student {
    student id
}

abstract class Category {
    number of hours
}

class Fulltime

class Parttime

Person <|-- Teacher
Person <|-- Student

Teacher "0..*" *-- "1" Category
Student "0..*" *-- "1" Category

Category <|-- Fulltime
Category <|-- Parttime
```

# Assignment 2
## Assignment 2.1
Do net really know how to split this up as the only functionality we have been given is the user interaction and not what the administrators want to do.
- F:
- A:
- C: Systemet udvikles i samarbejde med et eksternt software firma, det administrative personale og potentielle kunder.
- T: Tjenesten køres på firmaets egne servere, hvor client siden vil køre gennem kundernes browser på pc eller mobil.
- O: Film, Nummer, Kunde, Regning
- R: Systemet skal registrere, hvilke film kunderne ser, og hvilke musiknumre, kunden lytter til, samt understøtte afregning med kunderne for deres forbrug af disse film og musiknumre.

## 2.2
```plantuml
class Customer {
    name
    address
}

class Movie {
    number
    title
    length
}

class Music {
    number
    title
    length
    contained in album
}

class Bill {
    start date
    end date
    due date
    amount
}

class Session {
    date
    start time
    end time
}

Class Content

Customer "1" *- "0..*" Session
Customer "1" *-- "0..*" Bill

Content <|-- Movie
Content <|-- Music

Session "1" *-- "1" Content

Bill "1" -- "1..*" Session
```

## Assignment 2.3
|                 | Meget vigtigt | Vigtigt | Mindre vigtigt | Irrelevant | Trivielt opfyldt |
| :-------------- | :-----------: | :-----: | :------------: | :--------: | :--------------: |
| Brugbart        | x             |         |                |            |                  |
| Sikkert         |               | x       |                |            |                  |
| Effektivt       |               | x       |                |            |                  |
| Korrekt         |               | x       |                |            |                  |
| Pålideligt      |               |         |  x             |            |                  |
| Vedligeholdbart | x             |         |                |            |                  |
| Testbart        |               |         |                |            |  x               |
| Fleksibelt      | x             |         |                |            |                  |
| Forståeligt     | x             |         |                |            |                  |
| Genbrugbart     |               |         |                | x          |                  |
| Flytbart        |               | x       |                |            |                  |
| Integrerbart    |               |         |                | x          |                  |

# Assignment 3
## Assignment 3.1
|                                | Kunde | Opgave | Del-opgave | Lastbil | Chauffør | Container |
| :----------------------------- | :---: | :----: | :--------: | :-----: | :------: | :-------: |
| kunde oprettet                 |   +   |        |            |         |          |           |
| kunde nedlagt                  |   +   |        |            |         |          |           |
| opgave oprettet                |   *   |   +    |            |         |          |           |
| container registreret          |       |   *    |            |         |          |     +     |
| opgave afsluttet               |   *   |   +    |            |         |          |           |
| delopgave defineret            |       |   *    |     +      |         |          |           |
| lastbil tilknyttet             |       |        |     +      |    *    |          |           |
| chauffør tilknyttet            |       |        |     *      |         |    *     |           |
| lastbil ankommet til startsted |       |        |     +      |    *    |          |           |
| container lastet               |       |        |     +      |    *    |          |     +     |
| lastbil ankommet til slutsted  |       |        |     +      |    *    |          |           |
| container losset               |       |        |     +      |    *    |    *     |     +     |

## Assignment 3.2
### Kunde
```plantuml
[*] --> Oprettet : kunde oprettet
Oprettet -> Oprettet : opgave oprettet
Oprettet -> Oprettet : opgave afsluttet
Oprettet --> [*] : kunde nedlagt
```

### Opgave
```plantuml
[*] --> Oprettet : opgave oprettet
Oprettet -> Oprettet : container registreret
Oprettet --> Udføres : delopgave defineret
Udføres -> Udføres : delopgave defineret
Udføres --> [*] : opgave afsluttet
```

### Del-opgave
```plantuml
[*] --> Defineret : delopgave defineret
Defineret --> Lastbil : lastbil tilknyttet
Lastbil --> Chauffør : chauffør tilknyttet
Chauffør -> Chauffør : chauffør tilknyttet
Chauffør --> Start : last ankommet til startsted
Start --> Lastet : container lastet
Lastet --> Slut : lastbil ankommet til slutsted
Slut --> [*] : container losset
```

### Lastbil

### Chauffør
### Container

# Assignment 4
## Assignment 4.1
```plantuml
class Bruger {
    navn
    adresse
    foretrukket motionsform
    registrerings dato
    udmeldings dato
}

class Event {
    motionsform
    event skabt dato
    event afsluttet dato
}

class EventDeltagelse {
    bruger tilmeldt dato
    brugertilmelding slettet dato
    bruger deltaget
    event-forekomst vurderet
}

class EventForekomst {
    event forekomst skabt dato
    event forekomst gennemført dato
}

Bruger "1" *-- "0..*" Event
Bruger "1" *-- "0..*" EventDeltagelse
Event "1" - "0..*" EventDeltagelse
Event "1" *-- "0..*" EventForekomst
```
