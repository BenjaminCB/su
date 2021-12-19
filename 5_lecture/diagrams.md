```plantuml
state Member
state join1 <<fork>>
state join2 <<fork>>
state join3 <<fork>>
state join4 <<fork>>

[*] -> Member : joined(date)

join1 -down-> Member
Member -up-> join1 : consumption invoiced(date, amount)

join2 -down-> Member
Member -up-> join2 : invoice paid(date)

join3 -up-> Member
Member -down-> join3 : movie selected

join4 -up-> Member
Member -down-> join4 : song selected

Member -> [*] : left(date)
```

```plantuml
state Active {
    state Selected
    state Watching
    Selected --> Watching : movie started(time)
}

[*] --> Selected : movie selected
Watching --> [*] : movie ended(time)
Active --> [*] : movie cancelled
```
