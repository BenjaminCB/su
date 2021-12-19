# OOA&D, section 6.7, exercise 7 (page 136).
What are the key features of the procedural pattern?

> The procedural use-case pattern is the general solution to ensuring that many rules are observed.

In general it is a sequence of actions we must take to complete the use case.

# OOA&D, section 6.7, exercise 8 (page 136).
What are the key features of the material pattern?

This is where your system has a general state from which you can do a lot of different stuff, without having to do any of them sequentially, such as a text editor.

# OOA&D, section 6.7, exercise 12 (page 136).
Consider the computerized systems you use. Identify examples of use cases that can be described using the procedural pattern and the material pattern. Choose one from each group of use cases and provide a detailed description of these two use cases in a statechart diagram.

### See e-boks mail
```plantuml
state login
state awaiting_2FA_confiramation

[*] -> login : GET site
login -> awaiting_2FA_confiramation : type in password
awaiting_2FA_confiramation -> [*] : confirm 2FA on phone
```

### Watching videos on YouTube
```plantuml
state Watching
state Searching

[*] -> Watching : Click video
Watching -down-> Watching : Click video
Watching -up-> Searching : Search new video
Searching -> Watching : Click video

Watching -down-> [*] : exit
```
