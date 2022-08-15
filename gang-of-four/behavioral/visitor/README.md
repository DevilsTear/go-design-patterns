:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Behevioral Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/ "Behavioral Design Patterns Table of Contents")
# Visitor design pattern
In the next design pattern, we are going to delegate some logic of an object's type to an
external type called the visitor that will visit our object to perform operations on it.

In the Visitor design pattern, we are trying to separate the logic needed to work with a
specific object outside of the object itself. So we could have many different visitors that do
some things to specific types.

For example, imagine that we have a log writer that writes to console. We could make the
logger “visitable” so that you can prepend any text to each log. We could write a Visitor
pattern that prepends the date, the time, and the hostname to a field stored in the object.

## Objectives
With Behavioral design patterns we are mainly dealing with algorithms. Visitor patterns are
not an exception. The objectives that we are trying to achieve are as follows:
- To separate the algorithm of some type from its implementation within some
other type
- To improve the flexibility of some types by using them with little or no logic at all
so all new functionality can be added without altering the object structure
- To fix a structure or behavior that would break the open/closed principle in a
type

You might be thinking what the open/closed principle is. In computer science, the
open/closed principle states that: _entities should be open for extension but closed for modification_.
This simple state has lots of implications that allows building more maintainable software
and less prone to errors. And the Visitor pattern helps us to delegate some commonly
changing algorithm from a type that we need it to be “stable” to an external type that can
change often without affecting our original one.

## A log appender
We are going to develop a simple log appender as an example of the Visitor pattern.
Following the approach we have had in previous chapters, we will start with an extremely
simple example to clearly understand how the Visitor design pattern works before jumping
to a more complex one. We have already developed similar examples modifying texts too,
but in slightly different ways.

For this particular example, we will create a Visitor that appends different information to
the types it “visits”.

## Acceptance criteria
To effectively use the Visitor design pattern, we must have two roles–a visitor and a
visitable. The Visitor is the type that will act within a Visitable type. So a Visitable
interface implementation has an algorithm detached to the Visitor type:
- We need two message loggers: MessageA and MessageB that will print a
  message with an A: or a B: respectively before the message.
- We need a Visitor able to modify the message to be printed. It will append the
  text “Visited A” or “Visited B” to them, respectively.

## Wrap up the Visitor pattern
We have seen a powerful abstraction to add new algorithms to some types. However,
because of the lack of overloading in Go, this pattern could be limiting in some aspects 
(we have dealt with this limitation in the first example, where we had to create the `VisitA` and `VisitB`
implementations). In the second example, we haven't dealt with this limitation because we
have used an interface to the Visit method of the `Visitor` struct, but we just used one
type of visitor (`ProductInfoRetriever`) and we would have the same problem if we
implemented a `Visit` method for a second type, which is one of the objectives of the
original Gang of Four design patterns.
