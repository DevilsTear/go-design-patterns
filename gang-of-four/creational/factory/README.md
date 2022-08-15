:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Creational Design Patterns](https://github.com/DevilsTear/go-design-patterns/gang-of-four/creational/ "Creational Design Patterns Table of Contents")
# Factory method – delegating the creation of different types of payments
The purpose is to abstract the user from the knowledge
of the struct he needs to achieve for a specific purpose, such as retrieving some value,
maybe from a web service or a database. The user only needs an interface that provides him
this value. By delegating this decision to a Factory, this Factory can provide an interface that
fits the user needs. It also eases the process of downgrading or upgrading of the
implementation of the underlying type if needed.


When using the Factory method design pattern, we gain an extra layer of encapsulation so
that our program can grow in a controlled environment. With the Factory method, we
delegate the creation of families of objects to a different package or object to abstract us
from the knowledge of the pool of possible objects we could use. Imagine that you want to
organize your holidays using a trip agency. You don't deal with hotels and traveling, and
you just tell the agency the destination you are interested in so that they provide you with
everything you need. The trip agency represents a Factory of trips.
## Objectives
After the previous description, the following objectives of the Factory Method design
pattern must be clear to you:
- Delegating the creation of new instances of structures to a different part of the
program
- Working at the interface level instead of with concrete implementations
- Grouping families of objects to obtain a family object creator
## The example – a factory of payment methods for a shop
For our example, we are going to implement a payments method Factory, which is going to
provide us with different ways of paying at a shop. In the beginning, we will have two
methods of paying–cash and credit card. We'll also have an interface with the method, Pay,
which every struct that wants to be used as a payment method must implement.
## Acceptance criteria
Using the previous description, the requirements for the acceptance criteria are the following:
- To have a common method for every payment method called Pay
- To be able to delegate the creation of payments methods to the Factory
- To be able to add more payment methods to the library by just adding it to the factory method
## Wrapping up the Factory method
With the Factory method pattern, we have learned how to group families of objects so that
their implementation is outside of our scope. We have also learned what to do when we
need to upgrade an implementation of a used structs. Finally, we have seen that tests must
be written with care if you don't want to tie yourself to certain implementations that don't
have anything to do with the tests directly.
