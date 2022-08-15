:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Concurrency Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/concurrency/ "Concurrency Design Patterns Table of Contents")
# Pipeline design pattern
We will use this pattern heavily in our concurrent structures, and we can consider it one of the most
useful too.

We already know what a pipeline is. Every time that we write any function that performs
some logic, we are writing a pipeline: If this then that, or else something else. Pipeline pattern
can be made more complex by using a few functions that call to each other. They can even
get looped in their out execution.

The Pipeline pattern in Go works in a similar fashion, but each step in the Pipeline will be in
a different Goroutine and communication, and synchronizing will be done using channels.

## Objectives
When creating a Pipeline, we are mainly looking for the following benefits:
- We can create a concurrent structure of a multistep algorithm
- We can exploit the parallelism of multicore machines by decomposing an
algorithm in different Goroutines

However, just because we decompose an algorithm in different Goroutines doesn't
necessarily mean that it will execute the fastest. We are constantly talking about CPUs, so
ideally the algorithm must be CPU-intensive to take advantage of a concurrent structure.
The overhead of creating Goroutines and channels could make an algorithm smaller.

## A concurrent multi-operation
We are going to do some math for our example. We are going to generate a list of numbers
starting with 1 and ending at some arbitrary number N. Then we will take each number,
power it to 2, and sum the resulting numbers to a unique result. So, if N=3, our list will be
[1,2,3]. After powering them to 2, our list becomes [1,4,9]. If we sum the resulting list, the
resulting value is 14.

## Acceptance criteria
Functionally speaking, our Pipeline pattern needs to raise to the power of 2 every number
and then sum them all. It will be divided into a number generator and two operations, so:
- Generate a list from 1 to N where N can be any integer number.
- Take each number of this generated list and raise it to the power of 2.
- Sum each resulting number into a final result and return it.

## Wrap up the Pipeline pattern
With the Pipeline pattern, we can create really complex concurrent workflows in a very
easy way. In our case, we created a linear workflow, but it could also have conditionals,
pools, and fan-in and fan-out behavior. We will see some of these in the following chapter.