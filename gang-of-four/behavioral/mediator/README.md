:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Behevioral Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/ "Behavioral Design Patterns Table of Contents")
# Mediator design pattern
As its name implies, it's a pattern that will be in
between two types to exchange information. But, why will we want this behavior at all?
Let's look at this in detail.

One of the key objectives of any design pattern is to avoid tight coupling between objects.
This can be done in many ways, as we have known already.

But one particularly effective method when the application grows a lot is the Mediator
pattern. The Mediator pattern is the perfect example of a pattern that is commonly used by
every programmer without thinking very much about it.

Mediator pattern will act as the type in charge of exchanging communication between two
objects. This way, the communicating objects don't need to know each other and can change
more freely. The pattern that maintains which objects give what information is the Mediator.

## Objectives
As previously described, the main objectives of the Mediator pattern are about loose
coupling and encapsulation. The objectives are:
- To provide loose coupling between two objects that must communicate between them
- To reduce the amount of dependencies of a particular type to the minimum by
passing these needs to the Mediator pattern

## A calculator
For the Mediator pattern, we are going to develop an extremely simple arithmetic
calculator. You're probably thinking that a calculator is so simple that it does not need any
pattern. But we will see that this is not exactly true.

Our calculator will only do two very simple operations: sum and subtract.

## Acceptance criteria
It sounds quite funny to talk about acceptance criteria to define a calculator, but let's do it
anyway:
- Define an operation called Sum that takes a number and adds it to another number.
- Define an operation called Subtract that takes a number and subtracts it to another number.

## Wrap up the Mediator
We have carried out a disruptive example to try to think outside the box and reason deeply
about the Mediator pattern. Tight coupling between entities in an app can become really
complex to deal with in the future and allow more difficult refactoring if needed.

Just remember that the Mediator pattern is there to act as a managing type between two
types that don't know about each other so that you can take one of the types without
affecting the other and replace a type in a more easy and convenient way.