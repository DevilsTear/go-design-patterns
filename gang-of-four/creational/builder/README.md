:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Creational Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/creational/ "Creational Design Patterns Table of Contents")
# Builder design pattern – reusing an algorithm to create many implementations of an interface
Talking about Creational design patterns, it looks pretty semantic to have a Builder design
pattern. The Builder pattern helps us construct complex objects without directly
instantiating their struct, or writing the logic they require. Imagine an object that could have
dozens of fields that are more complex structs themselves. Now imagine that you have
many objects with these characteristics, and you could have more. We don't want to write
the logic to create all these objects in the package that just needs to use the objects.

Instance creation can be as simple as providing the opening and closing braces {} and
leaving the instance with zero values, or as complex as an object that needs to make some
API calls, check states, and create objects for its fields. You could also have an object that is
composed of many objects, something that's really idiomatic in Go, as it doesn't support
inheritance.
At the same time, you could be using the same technique to create many types of objects.
For example, you'll use almost the same technique to build a car as you would build a bus,
except that they'll be of different sizes and number of seats, so why don't we reuse the
construction process? This is where the Builder pattern comes to the rescue.
## Objectives
A Builder design pattern tries to:
- Abstract complex creations so that object creation is separated from the object user
- Create an object step by step by filling its fields and creating the embedded objects
- Reuse the object creation algorithm between many objects

## Example – vehicle manufacturing
The Builder design pattern has been commonly described as the relationship between a
director, a few Builders, and the product they build. Continuing with our example of the
car, we'll create a vehicle Builder. The process (widely described as the algorithm) of
creating a vehicle (the product) is more or less the same for every kind of vehicle–choose
vehicle type, assemble the structure, place the wheels, and place the seats. If you think
about it, you could build a car and a motorbike (two Builders) with this description, so we
are reusing the description to create cars in manufacturing. The director is represented by
the ManufacturingDirector type in our example.

## Requirements and acceptance criteria
As far as we have described, we must dispose of a Builder of type Car and Motorbike and
a unique director called ManufacturingDirector to take builders and construct products.
So the requirements for a Vehicle builder example would be the following:
- I must have a manufacturing type that constructs everything that a vehicle needs 
- When using a car builder, the VehicleProduct with four wheels, five seats, and a structure defined as Car must be returned
- When using a motorbike builder, the VehicleProduct with two wheels, two
seats, and a structure defined as Motorbike must be returned
- A VehicleProduct built by any BuildProcess builder must be open to modifications

## Wrapping up the Builder design pattern
The Builder design pattern helps us maintain an unpredictable number of products by
using a common construction algorithm that is used by the director. The construction
process is always abstracted from the user of the product.
At the same time, having a defined construction pattern helps when a newcomer to our
source code needs to add a new product to the pipeline. The BuildProcess interface
specifies what he must comply to be part of the possible builders.
However, try to avoid the Builder pattern when you are not completely sure that the
algorithm is going to be more or less stable because any small change in this interface will
affect all your builders and it could be awkward if you add a new method that some of your
builders need and others Builders do not.