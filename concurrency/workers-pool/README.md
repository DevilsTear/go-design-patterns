:house:[Home](https://github.com/DevilsTear/go-design-patterns/README.md "Table of Contents") | :file_folder:[Concurrency Design Patterns](https://github.com/DevilsTear/go-design-patterns/concurrency/README.md "Concurrency Design Patterns Table of Contents")
# Workers pool
One problem we may face with some of the previous approaches to concurrency is their
unbounded context. We cannot let an app create an unlimited amount of Goroutines.

Goroutines are light, but the work they perform could be very heavy. A workers pool helps
us to solve this problem.

With a pool of workers, we want to bound the amount of Goroutines available so that we
have a deeper control of the pool of resources. This is easy to achieve by creating a channel
for each worker and having workers with either an idle or busy status. The task can seem
intimidating(daunting), but it's not at all.

## Objectives
Creating a Worker pool is all about resource control: CPU, RAM, time, connections, and so
on. The workers pool design pattern helps us to do the following:
- Control access to shared resources using quotas
- Create a limited amount of Goroutines per app
- Provide more parallelism capabilities to other concurrent structures

## A pool of pipelines
In the previous chapter, we saw how to work with a pipeline. Now we will launch a
bounded number of them so that the Go scheduler can try to process requests in parallel.
The idea here is to control the number of Goroutines, stop them gracefully when the app
has finished, and maximize parallelism using a concurrent structure without race
conditions.

The pipeline we will use is similar to the one we used in the previous chapter, where we
were generating numbers, raising them to the power of 2, and summing the final results. In
this case, we are going to pass strings to which we will append and prefix data.

## Acceptance criteria
In business terms, we want something that tells us that, worker has processed a request, a
predefined ending, and incoming data parsed to uppercase:
- When making a request with a string value (any), it must be uppercase.
- Once the string is uppercase, a predefined text must be appended to it. This text should not be uppercase.
- With the previous result, the worker ID must be prefixed to the final string.
- The resulting string must be passed to a predefined handler.
We haven't talked about how to do it technically, just what the business wants. With the
entire description, we'll at least have workers, requests, and handlers.
# Wrapping up the Workers pool
With the workers pool, we have our first complex concurrent application that can be used in
real-world production systems. It also has room to improve, but it is a very good design
pattern to build concurrent bounded apps.

It is key that we always have the number of Goroutines that are being launched under
control. While it's easy to launch thousands to achieve more parallelism in an app, we must
be very careful that they don't have code that can hang them in an infinite loop, too.

With the workers pool, we can now fragment a simple operation in many parallel tasks.
Think about it; this could achieve the same result with one simple call to fmt.Printf, but
we have done a pipeline with it; then, we launched few instances of this pipeline and
finally, distributed the workload between all those pipes.