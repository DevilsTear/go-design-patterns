:house:[Home](https://github.com/DevilsTear/go-design-patterns/README.md "Table of Contents")
# Concurrency Design Patterns
After we are familiar with the concepts of concurrency and parallelism, and we have
understood how to achieve them by using Go's concurrency primitives, we can see some
patterns regarding concurrent work and parallel execution. 

We'll see the following patterns:
- [Barrier](https://github.com/DevilsTear/go-design-patterns/concurrency/barrier/README.md "Barrier Design Pattern in Go") is a very common pattern, especially when we have to wait for more than
  one response from different Goroutines before letting the program continue
- Future pattern allows us to write an algorithm that will be executed eventually in
  time (or not) by the same Goroutine or a different one
- Pipeline is a powerful pattern to build complex synchronous flows of Goroutines
  that are connected with each other according to some logic
- Workers pool is one way to develop a pool of workers. This is useful to control the
  number of Goroutines in an execution.
- Pub/Sub is a rewrite of the Observer pattern, which we saw on 
  Behavioral Patterns – Visitor, State, Mediator, and Observer Design
  Patterns, written with a concurrent structure. With this example we'll dig a bit
  more into the concurrent structures and look at how they can differ from a
  common approach.

Take a quick look at the description of the patterns. They all describe some sort of
logic to synchronize execution in time. It's very important to keep in mind that we are now
developing concurrent structures with all the tools and patterns we have seen in the
Gang of Four chapters. With Creational patterns we were dealing with creating objects. With
the Structural patterns we were learning how to build idiomatic structures and in
Behavioral patterns we were managing mostly with algorithms. Now, with Concurrency
patterns, we will mostly manage the timing execution and order execution of applications
that has more than one flow.
