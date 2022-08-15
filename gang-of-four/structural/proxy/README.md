:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/gang-of-four/structural/ "Structural Design Patterns Table of Contents")
# Proxy design pattern
It's a simple pattern that provides interesting features and possibilities with very little effort.

The Proxy pattern usually wraps an object to hide some of its characteristics. These
characteristics could be the fact that it is a remote object (remote proxy), a very heavy object
such as a very big image or the dump of a terabyte database (virtual proxy), or a restricted
access object (protection proxy).

## Objectives
The possibilities of the Proxy pattern are many, but in general, they all try to provide the
same following functionalities:
- Hide an object behind the proxy so the features can be hidden, restricted, and so on
- Provide a new abstraction layer that is easy to work with, and can be changed easily

## Example
For our example, we are going to create a remote proxy, which is going to be a cache of
objects before accessing a database. Let's imagine that we have a database with many users,
but instead of accessing the database each time we want information about a user, we will
have a `First In First Out (FIFO)` stack of users in a Proxy pattern (FIFO is a way of saying
that when the cache needs to be emptied, it will delete the first object that entered first).

## Acceptance criteria
We will wrap an imaginary database, represented by a slice, with our Proxy pattern. Then,
the pattern will have to stick to the following acceptance criteria:
- All access to the database of users will be done through the Proxy type.
- A stack of n number of recent users will be kept in the Proxy.
- If a user already exists in the stack, it won't query the database, and will return the stored one
- If the queried user doesn't exist in the stack, it will query the database, remove the oldest user in the stack if it's full, store the new one, and return it.

## Wrap up the Proxy pattern
Wrap proxies around types that need some intermediate action, like giving authorization to
the user or providing access to a database, like in our example.

The example is a good way to separate application needs from database needs. If our
application accesses the database too much, a solution for this is not in your database.
Remember that the Proxy uses the same interface as the type it wraps, and, for the user,
there shouldn't be any difference between the two.
