:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/ "Structural Design Patterns Table of Contents")
# Flyweight design pattern
Flyweight design pattern is very commonly used in computer
graphics and the video game industry, but not so much in enterprise applications.

Flyweight is a pattern which allows sharing the state of a heavy object between many
instances of some type. Imagine that you have to create and store too many objects of some
heavy type that are fundamentally equal. You'll run out of memory pretty quickly. This
problem can be easily solved with the Flyweight pattern, with additional help of the Factory
pattern. The factory is usually in charge of encapsulating object creation, as we saw
previously.
## Objectives
Thanks to the Flyweight pattern, we can share all possible states of objects in a single
common object, and thus minimize object creation by using pointers to already created
objects.

## Example
To give an example, we are going to simulate something that you find on betting webpages.
Imagine the final match of the European championship, which is viewed by millions of
people across the continent. Now imagine that we own a betting webpage, where we
provide historical information about every team in Europe. This is plenty of information,
which is usually stored in some distributed database, and each team has, literally,
megabytes of information about their players, matches, championships, and so on.

If a million users access information about a team and a new instance of the information is
created for each user querying for historical data, we will run out of memory in the blink of
an eye. With our Proxy solution, we could make a cache of the n most recent searches to
speed up queries, but if we return a clone for every team, we will still get short on memory
(but faster thanks to our cache). Funny, right?

Instead, we will store each team's information just once, and we will deliver references to
them to the users. So, if we face a million users trying to access information about a match,
we will actually just have two teams in memory with a million pointers to the same
memory direction.

## Acceptance criteria
The acceptance criteria for a Flyweight pattern must always reduce the amount of memory
that is used, and must be focused primarily on this objective:
- We will create a Team struct with some basic information such as the team's
name, players, historical results, and an image depicting their shield.
- We must ensure correct team creation (note the word creation here, candidate for
a creational pattern), and not having duplicates.
- When creating the same team twice, we must have two pointers pointing to the
same memory address.