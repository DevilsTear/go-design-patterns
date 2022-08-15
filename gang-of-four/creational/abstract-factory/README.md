:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Creational Design Patterns](https://github.com/DevilsTear/go-design-patterns/gang-of-four/creational/ "Creational Design Patterns Table of Contents")
# Abstract Factory – a factory of factories
The Abstract Factory design pattern is a new layer of grouping to achieve a bigger (and
more complex) composite object, which is used through its interfaces. The idea behind
grouping objects in families and grouping families is to have big factories that can be
interchangeable and can grow more easily. In the early stages of development, it is also
easier to work with factories and abstract factories than to wait until all concrete
implementations are done to start your code. Also, you won't write an Abstract Factory
from the beginning unless you know that your object's inventory for a particular field is
going to be very large and it could be easily grouped into families.
## The objectives
Grouping related families of objects is very convenient when your object number is growing
so much that creating a unique point to get them all seems the only way to gain
the flexibility of the runtime object creation. The following objectives of the Abstract Factory
method must be clear to you:
Provide a new layer of encapsulation for Factory methods that return a common
interface for all factories
Group common factories into a super Factory (also called a factory of factories)
## The vehicle factory example, again?
For our example, we are going to reuse the Factory we created in the Builder design pattern.
We want to show the similarities to solve the same problem using a different approach so
that you can see the strengths and weaknesses of each approach. This is going to show you
the power of implicit interfaces in Go, as we won't have to touch almost anything. Finally,
we are going to create a new Factory to create shipment orders.

## Acceptance criteria
The following are the acceptance criteria for using the Vehicle object's Factory method:
- We must retrieve a Vehicle object using a factory returned by the abstract
factory.
- The vehicle must be a concrete implementation of a Motorbike or a Car that
implements both interfaces (Vehicle and Car or Vehicle and Motorbike).

## Wrap up the Abstract Factory method
This pattern is commonly used in many applications and libraries,
such as cross-platform GUI libraries. Think of a button, a generic object, and button factory
that provides you with a factory for Microsoft Windows buttons while you have another
factory for Mac OS X buttons. You don't want to deal with the implementation details of
each platform, but you just want to implement the actions for some specific behavior raised
by a button.

Also, we have seen the differences when approaching the same problem with two different
solutions–the Abstract factory and the Builder pattern. As you have seen, with the Builder
pattern, we had an unstructured list of objects (cars with motorbikes in the same factory).
Also, we encouraged reusing the building algorithm in the Builder pattern. In the Abstract
factory, we have a very structured list of vehicles (the factory for motorbikes and a factory
for cars). We also didn't mix the creation of cars with motorbikes, providing more flexibility
in the creation process. The Abstract factory and Builder patterns can both resolve the same
problem, but your particular needs will help you find the slight differences that should lead
you to take one solution or the other.