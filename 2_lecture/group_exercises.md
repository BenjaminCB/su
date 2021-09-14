# Section 3.6, Exercise 16
Elevator control. Consider a system to control elevator movement in a building. Several processors keep track of movements and signals. There is one processor for each of the N elevators. It controls the engine and doors, and reads the push buttons and sensors associated with the elevator. There is one processor at each of the M floors. It reads the  push buttons associated with the floor. Finally, there is one processor that controls all requests from all push buttons. Your solution can be centralized or decentralized, but it should meet the following requirements:

- Each elevator has a button for each floor. The buttons are illuminated when pressed and cause the elevator to visit that floor.
- Each floor has two buttons (except ground and top): one to request up-elevator and one to request down-elevator. The buttons illuminate when pressed and cancel when a suitable elevator visits the floor.
- All requests for elevators from the different floors must be serviced eventually with all floors given equal priority.
- All requests for floors from within elevators must be served evetually, with floors being serviced sequentially in the travel direction.

Add details and assumptions as needed and address the following problems. List class candidates in the elevator control system, List.
