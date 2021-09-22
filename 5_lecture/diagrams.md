```plantuml
state Member
state join1 <<fork>>
state join2 <<fork>>

[*] -> Member : joined(date)

Member -up-> join1 : consumption invoiced(date, amount)
join1 -down-> Member

Member -up-> join2 : invoice paid(date)
join2 -down-> Member

Member -down-> Member : movie selected
Member -down-> Member : song selected
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
