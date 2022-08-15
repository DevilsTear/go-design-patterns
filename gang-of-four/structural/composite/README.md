:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/gangs-of-four/structural/ "Structural Design Patterns Table of Contents")
# Composite design pattern
The Composite design pattern favors composition (commonly defined as a has a
relationship) over inheritance (an is a relationship). The composition over inheritance approach
has been a source of discussions among engineers since the nineties. We will learn how to
create object structures by using a has an approach. All in all, Go doesn't have inheritance
because it doesn't need it!

In the Composite design pattern, you will create hierarchies and trees of objects. Objects
have different objects with their own fields and methods inside them. This approach is very
powerful and solves many problems of inheritance and multiple inheritances. For example,
a typical inheritance problem is when you have an entity that inherits from two completely
different classes, which have absolutely no relationship between them. Imagine an athlete
who trains, and who is a swimmer who swims:
- The Athlete class has a Train() method
- The Swimmer class has a Swim() method

The Swimmer class inherits from the Athlete class, so it inherits its Train method and
declares its own Swim method. You could also have a cyclist who is also an athlete, and
declares a Ride method.
But now imagine an animal that eats, like a dog that also barks:
- The Cyclist class has a Ride() method
- The Animal class has Eat(), Dog(), and Bark() methods

Nothing fancy. You could also have a fish that is an animal, and yes, swims! So, how do you
solve it? A fish cannot be a swimmer that also trains. Fish don't train (as far as I know!). You
could make a Swimmer interface with a Swim method, and make the swimmer athlete and
fish implement it. This would be the best approach, but you still would have to implement
swim method twice, so code reusability would be affected. What about a triathlete? They are
athletes who swim, run, and ride. With multiple inheritances, you could have a sort of
solution, but that will become complex and not maintainable very soon.

## Objectives
As you have probably imagined already, the objective of the composition is to avoid this
type of hierarchy hell where the complexity of an application could grow too much, and the
clarity of the code is affected.

## The swimmer and the fish
We will solve the described problem of the athlete and the fish that swims in a very
idiomatic Go way. With Go, we can use two types of composition–the direct composition
and the embedding composition. We will first solve this problem by using direct
composition which is having everything that is needed as fields within the struct.

## Requirements and acceptance criteria
Requirements are like the ones described previously. We'll have an athlete and a swimmer.
We will also have an animal and a fish. The Swimmer and the Fish methods must share the
code. The athlete must train, and the animal must eat:
- We must have an Athlete struct with a Train method
- We must have a Swimmer with a Swim method
- We must have an Animal struct with an Eat method
- We must have a Fish struct with a Swim method that is shared with the Swimmer, and not have inheritance or hierarchy issues

## Wrap up the Composite pattern
At this point, you should be really comfortable using the Composite design pattern. It's a
very idiomatic Go feature, and the switch from a pure object-oriented language is not very
painful. The Composite design pattern makes our structures predictable but also allows us
to create most of the design patterns as we will see in other chapters.
