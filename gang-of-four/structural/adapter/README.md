:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/gang-of-four/structural/ "Structural Design Patterns Table of Contents")
# Adapter design pattern
One of the most commonly used structural patterns is the Adapter pattern. Like in real life,
where you have plug adapters and bolt adapters, in Go, an adapter will allow us to use
something that wasn't built for a specific task at the beginning.

The Adapter pattern is very useful when, for example, an interface gets outdated and it's
not possible to replace it easily or fast. Instead, you create a new interface to deal with the
current needs of your application, which, under the hood, uses implementations of the old
interface.
Adapter also helps us to maintain the open/closed principle in our apps, making them more
predictable too. They also allow us to write code which uses some base that we can't
modify.

The open/closed principle was first stated by Bertrand Meyer in his book
Object-Oriented Software Construction. He stated that code should be open
to new functionality, but closed to modifications. What does it mean?
Well, it implies a few things. On one hand, we should try to write code
that is extensible and not only one that works. At the same time, we
should try not to modify the source code (yours or other people's) as much
as we can, because we aren't always aware of the implications of this
modification. Just keep in mind that extensibility in code is only possible
through the use of design patterns and interface-oriented programming

## Objectives
The Adapter design pattern will help you fit the needs of two parts of the code that are
incompatible at first. This is the key to being kept in mind when deciding if the Adapter
pattern is a good design for your problem–two interfaces that are incompatible, but which
must work together, are good candidates for an Adapter pattern (but they could also use
the facade pattern, for example).
## Using an incompatible interface with an Adapter object
For our example, we will have an old Printer interface and a new one. Users of the new
interface don't expect the signature that the old one has, and we need an Adapter so that
users can still use old implementations if necessary (to work with some legacy code, for
example).
## Requirements and acceptance criteria
Having an old interface called LegacyPrinter and a new one called ModernPrinter,
create a structure that implements the ModernPrinter interface and can use the
LegacyPrinter interface as described in the following steps:
- Create an Adapter object that implements the ModernPrinter interface.
- The new Adapter object must contain an instance of the LegacyPrinter interface.
- When using ModernPrinter, it must call the LegacyPrinter interface under the hood, prefixing it with the text Adapter.

## Wrap up the Adapter pattern
With the Adapter design pattern, we can implement a quick way to achieve the open/close
principle in your applications. Instead of modifying your old source code (something which
could not be possible in some situations), we might be created a way to use the old
functionality with a new signature.