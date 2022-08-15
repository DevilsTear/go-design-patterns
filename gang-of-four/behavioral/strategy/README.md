:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Behevioral Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/ "Behavioral Design Patterns Table of Contents")
# Strategy design pattern
The Strategy pattern is probably the easiest to understand of the Behavioral patterns. We
have used it a few times while developing the other patterns but without stopping to
talk about it. Now we will.

The Strategy pattern uses different algorithms to achieve some specific functionality. These
algorithms are hidden behind an interface and, of course, they must be interchangeable. All
algorithms achieve the same functionality in a different way. For example, we could have a
`Sort` interface and few sorting algorithms. The result is the same, some list is sorted, but we
could have used quick sort, merge sort, and so on.

Can you guess when we used a Strategy pattern in the previous chapters? Three, two, one…
Well, we heavily used the strategy pattern when we used the `io.Writer` interface. The
`io.Writer` interface defines a strategy to write, and the functionality is always the same–to
write something. We could write it to the standard out, to some file or to a user-defined
type, but we do the same thing at the end–to write. We just change the strategy to write (in
this case, we change the place where we write).

## Objectives
The objectives of the Strategy pattern are really clear. The pattern should do the following:
- Provide a few algorithms to achieve some specific functionality
- All types achieve the same functionality in a different way but the client of the
  strategy isn't affected

The problem is that this definition covers a huge spectrum of possibilities. This is because
Strategy pattern is actually used for a variety of scenarios and many software engineering
solutions come with some kind of strategy within. Therefore it's better to see it in action
with a real example.

## Rendering images or text
We are going to do something different for this example. Instead of printing text on the
console only, we are also going to paint objects on a file.

In this case, we will have two strategies: console and file. But the user of the library won't
have to deal with the complexity behind them.

The key feature is that the “caller” doesn´t know how the underlying library is working and
he just knows the information available on the defined strategy.

We have chosen to print to console but we won´t deal with the
`ConsoleStrategy` type directly, we´ll always use an interface that represents it.
The `ConsoleStrategy` type will hide the implementation details of printing to console to
caller in main function. FileStrategy hides its implementation details as well as any future
strategy.

##Acceptance criteria
A strategy must have a very clear objective and we will have two ways to achieve it. Our
objectives will be as follows:
- Provide a way to show to the user an object (a square) in text or image
- The user must choose between image or text when launching the app
- The app must be able to add more visualization strategies (audio, for example)
- If the user selects text, the word Square must be printed in the console
- If the user selects image, an image of a white square on a black background will
  be printed on a file

## Wrap up the Strategy pattern
We have learned a powerful way to encapsulate algorithms in different structs. We have
also used embedding instead of inheritance to provide cross-functionality between types,
which will come in handy very often in our apps. You'll find yourself combining strategies
here and there as we have seen in the second example, where we have strategies for logging
and writing by using the `io.Writer` interface, a strategy for byte-streaming operations.