:house:[Home](https://github.com/DevilsTear/go-design-patterns/README.md "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/gangs-of-four/structural/README.md "Structural Design Patterns Table of Contents")
# Bridge design pattern
The Bridge pattern is a design with a slightly cryptic definition from the original Gang of
Four book. It decouples an abstraction from its implementation so that the two can vary
independently. This cryptic explanation just means that you could even decouple the most
basic form of functionality: decouple an object from what it does.

The Bridge pattern tries to decouple things as usual with design patterns. It decouples
abstraction (an object) from its implementation (the thing that the object does). This way, we
can change what an object does as much as we want. It also allows us to change the
abstracted object while reusing the same implementation.

## Objectives
The objective of the Bridge pattern is to bring flexibility to a struct that change often.
Knowing the inputs and outputs of a method, it allows us to change code without knowing
too much about it and leaving the freedom for both sides to be modified more easily.

## Two printers and two ways of printing for each
For our example, we will go to a console printer abstraction to keep it simple. We will have
two implementations. The first will write to the console. Having learned about the
io.Writer interface in the previous section, we will make the second write to an
io.Writer interface to provide more flexibility to the solution. We will also have two
abstracted object users of the implementations–a Normal object, which will use each
implementation in a straightforward manner, and a `Packt` implementation, which will
append the sentence `Message from Packt:` to the printing message.

At the end of this section, we will have two abstraction objects, which have two different
implementations of their functionality. So, actually, we will have 22
possible combinations
of object functionality.
## Requirements and acceptance criteria
As we mentioned previously, we will have two objects (`Packt` and `Normal` printer) and
two implementations (`PrinterImpl1` and `PrinterImpl2`) that we will join by using the
Bridge design pattern. More or less, we will have the following requirements and
acceptance criteria:
- A `PrinterAPI` that accepts a message to print
- An implementation of the API that simply prints the message to the console
- An implementation of the API that prints to an `io.Writer` interface
- A Printer abstraction with a `Print` method to implement in printing types
- A `normal` printer object, which will implement the `Printer` and the `PrinterAPI` interface
- The `normal` printer will forward the message directly to the implementation
- A Packt printer, which will implement the Printer abstraction and the PrinterAPI interface
- The Packt printer will append the message `Message from Packt:` to all prints

## Wrap up the Bridge pattern
With the Bridge pattern, we have learned how to uncouple an object and its implementation
for the PrintMessage method. This way, we can reuse its abstractions as well as its
implementations. We can swap the printer abstractions as well as the printer APIs as much
as we want without affecting the user code.

We have also tried to keep things as simple as possible, but you have definitely realized
that all implementations of the PrinterAPI interface could have been created using a
factory. This would be very natural, and you could find many implementations that have
followed this approach. However, we shouldn't get into over-engineering, but should
analyze each problem to make a precise design of its needs and finds the best way to create
a reusable, maintainable, and readable source code. Readable code is commonly forgotten,
but a robust and uncoupled source code is useless if nobody can understand it to maintain
it. It's like a book of the tenth century–it could be a precious story but pretty frustrating if
we have difficulty understanding its grammar.