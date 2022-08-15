:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Creational Design Patterns](https://github.com/DevilsTear/go-design-patterns/gang-of-four/creational/ "Creational Design Patterns Table of Contents")
# Prototype design pattern
Like all creational patterns, this too comes in handy when creating objects, and it is very common to see the
Prototype pattern surrounded by more patterns.

While with the Builder pattern, we are dealing with repetitive building algorithms and with
the factories we are simplifying the creation of many types of objects; with the Prototype
pattern, we will use an already created instance of some type to clone it and complete it
with the particular needs of each context.

The aim of the Prototype pattern is to have an object or a set of objects that is already
created at compilation time, but which you can clone as many times as you want at runtime.
This is useful, for example, as a default template for a user who has just registered with
your webpage or a default pricing plan in some service. The key difference between this
and a Builder pattern is that objects are cloned for the user instead of building them at
runtime. You can also build a cache-like solution, storing information using a prototype.

## Objective
The main objective for the Prototype design pattern is to avoid repetitive object creation.
Imagine a default object composed of dozens of fields and embedded types. We don't want
to write everything needed by this type every time that we use the object, especially if we
can mess it up by creating instances with different foundations:
- Maintain a set of objects that will be cloned to create new instances
- Provide a default value of some type to start working on top of it
- Free CPU of complex object initialization to take more memory resources
## Example
We will build a small component of an imaginary customized shirts shop that will have a
few shirts with their default colors and prices. Each shirt will also have a Stock Keeping
Unit (SKU), a system to identify items stored at a specific location) that will need an
update.

## Acceptance criteria
To achieve what is described in the example, we will use a prototype of shirts. Each time we
need a new shirt we will take this prototype, clone it and work with it. In particular, those
are the acceptance criteria for using the Prototype pattern design method in this example:

- To have a shirt-cloner object and interface to ask for different types of shirts (white, black, and blue at 15.00, 16.00, and 17.00 dollars respectively)
- When you ask for a white shirt, a clone of the white shirt must be made, and the new instance must be different from the original one
- The SKU of the created object shouldn't affect new object creation
- An info method must give me all the information available on the instance fields, including the updated SKU

## Wrap up the Prototype design pattern
The Prototype pattern is a powerful tool to build caches and default objects. You have
probably realized too that some patterns can overlap a bit, but they have small differences
that make them more appropriate in some cases and not so much in others.