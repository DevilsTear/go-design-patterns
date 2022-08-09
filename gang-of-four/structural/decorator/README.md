:house:[Home](https://github.com/DevilsTear/go-design-patterns/README.md "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/gangs-of-four/structural/README.md "Structural Design Patterns Table of Contents")
# Decorator design pattern
This pattern is the big brother of the Proxy pattern, and maybe, one of the
most powerful design patterns of all. The **Decorator** pattern is pretty simple, but, for
instance, it provides a lot of benefits when working with legacy code.

The Decorator design pattern allows you to decorate an already existing type with more
functional features without actually touching it. How is it possible? Well, it uses an
approach similar to `matryoshka dolls`, where you have a small doll that you can put inside a
doll of the same shape but bigger, and so on and so forth.

The Decorator type implements the same interface of the type it decorates, and stores an
instance of that type in its members. This way, you can stack as many decorators (dolls) as
you want by simply storing the old decorator in a field of the new one.

## Objectives
When you think about extending legacy code without the risk of breaking something, you
should think of the Decorator pattern first. It's a really powerful approach to deal with this
particular problem.

A different field where the Decorator is very powerful may not be so obvious though it
reveals itself when creating types with lots of features based on user inputs, preferences, or
similar inputs. Like in a Swiss knife, you have a base type (the frame of the knife), and from
there you unfold its functionalities.

So, precisely when are we going to use the Decorator pattern? Answer to this question:
- When you need to add functionality to some code that you don't have access to,
or you don't want to modify to avoid a negative effect on the code, and follow the
open/close principle (like legacy code)
- When you want the functionality of an object to be created or altered
dynamically, and the number of features is unknown and could grow fast
- 
## Example
In our example, we will prepare a Pizza type, where the core is the pizza and the
ingredients are the decorating types. We will have a couple of ingredients for our
pizza–onion and meat.

## Acceptance criteria
The acceptance criteria for a Decorator pattern is to have a common interface and a core
type, the one that all layers will be built over:
- We must have the main interface that all decorators will implement. This
interface will be called `IngredientAdd`, and it will have the `AddIngredient()`
string method.
- We must have a core `PizzaDecorator` type (the decorator) that we will add
ingredients to.
- We must have an ingredient “onion” implementing the same IngredientAdd interface that will add the string `onion` to the returned pizza.
- We must have an ingredient “meat” implementing the `IngredientAdd` interface that will add the string `meat` to the returned pizza.
- When calling `AddIngredient` method on the top object, it must return a fully decorated pizza with the text `Pizza with the following ingredients: meat, onion`.

## Wrap up the Decorator design pattern – Proxy versus Decorator
You might be wondering, what's the difference between the Decorator pattern and the
Proxy pattern? In the Decorator pattern, we decorate a type dynamically. This means that
the decoration may or may not be there, or it may be composed of one or many types. If you
remember, the Proxy pattern wraps a type in a similar fashion, but it does so at compile
time, and it's more like a way to access some type.

At the same time, a decorator might implement the entire interface that the type it decorates
also implements or not. So you can have an interface with 10 methods and a decorator that
just implements one of them, and it will still be valid. A call on a method not implemented
by the decorator will be passed to the decorated type. This is a very powerful feature but
also very prone to undesired behaviors at runtime if you forget to implement any interface
method.

In this aspect, you may think that the Proxy pattern is less flexible, and it is. But the
Decorator pattern is weaker, as you could have errors at runtime, which you can avoid at
compile time by using the Proxy pattern. Just keep in mind that the Decorator is commonly
used when you want to add functionality to an object at runtime, like in our web server. It's
a compromise between what you need and what you want to sacrifice to achieve it.