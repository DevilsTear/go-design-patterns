:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Concurrency Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/concurrency/ "Concurrency Design Patterns Table of Contents")
# Future design pattern
The Future design pattern (also called Promise) is a quick and easy way to achieve
concurrent structures for asynchronous programming. We will take advantage of first class
functions in Go to develop Futures.

In short, we will define each possible behavior of an action before executing them in
different Goroutines. Node.js uses this approach, providing event-driven programming by
default. The idea here is to achieve a fire-and-forget that handles all possible results in an
action.

To understand it better, we can talk about a type that has embedded the behavior in case an
execution goes well or in case it fails.

The interesting thing here is that we can launch a new Future within a Future and embed as
many Futures as we want in the same Goroutine (or new ones). The idea is to take
advantage of the result of one Future to launch the next.

This is a kind of lazy programming, where a Future could be calling to itself indefinitely or
just until some rule is satisfied. The idea is to define the behavior in advance and let the
future resolve the possible solutions.

## Objectives
With the Future pattern, we can launch many new Goroutines, each with an action and its
own handlers. This enables us to do the following:
- Delegate the action handler to a different Goroutine
- Stack many asynchronous calls between them (an asynchronous call that calls
another asynchronous call in its results)

## A simple asynchronous requester
We are going to develop a very simple example to try to understand how a Future works.
In this example, we will have a method that returns a string or an error, but we want to
execute it concurrently. We have learned ways to do this already. Using a channel, we can
launch a new Goroutine and handle the incoming result from the channel.

But in this case, we will have to handle the result (string or error), and we don't want this.
Instead, we will define what to do in case of success and what to do in case of error and fireand-forget the Goroutine.

## Acceptance criteria
We don't have functional requirements for this task. Instead, we will have technical
requirements for it:
- Delegate the function execution to a different Goroutine
- The function will return a string (maybe) or an error
- The handlers must be already defined before executing the function
- The design must be reusable

## Wrap up the Future pattern
We have seen a good way to achieve asynchronous programming by using a function type
system. However, we could have done it without functions by setting an interface with
Success, Fail, and Execute methods and the types that satisfy them, and using the
Template pattern to execute them asynchronously. It is up to developer!