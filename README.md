# Gang of Four Design Patterns
Over 20 years ago the iconic computer science book “[Design Patterns: Elements of Reusable Object-Oriented Software](https://www.amazon.com/gp/product/0201633612/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0201633612&linkCode=as2&tag=triatcraft-20&linkId=XRGUDJCGWC6AJNZM "Design Patterns: Elements of Reusable Object-Oriented Software")” was first published. The four authors of the book: Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, have since been dubbed “The Gang of Four”. In technology circles, you’ll often see this nicknamed shorted to GoF. Even though the GoF  [Design Patterns](https://www.amazon.com/gp/product/0201633612/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0201633612&linkCode=as2&tag=triatcraft-20&linkId=XRGUDJCGWC6AJNZM "Design Patterns: Elements of Reusable Object-Oriented Software")  book was published over 20 years ago, it still continues to be an Amazon bestseller.

The GoF wrote the book in a C++ context but it still remains very relevant to Java programming. C++ and Go are both object-oriented languages. The GoF authors, through their experience in coding large scale enterprise systems using C++, saw common patterns emerge. These design patterns are not unique to C++. The design patterns can be applied in any object oriented language.

As a Go developer to develop enterprise class applications, you will encounter the GoF Design Patterns on a daily basis.

The GoF Design Patterns are broken into three categories: Creational Patterns for the creation of objects; Structural Patterns to provide relationship between objects; and finally, Behavioral Patterns to help define how objects interact.

## Gang of Four Design Patterns

### Creational Design Patterns

-   [Abstract Factory](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/creational/abstract-factory/ "Abstract Factory Design Pattern in Go"). Allows the creation of objects without specifying their concrete type.
-   [Builder](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/creational/builder/ "Builder Design Pattern in Go"). Uses to create complex objects.
-   [Factory Method](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/creational/factory/ "Factory Method Design Pattern in Go"). Creates objects without specifying the exact class to create.
-   [Prototype](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/creational/prototype/ "Prototype Design Pattern in Go"). Creates a new object from an existing object.
-   [Singleton](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/creational/singleton/ "Singleton Design Pattern in Go"). Ensures only one instance of an object is created.

### Structural Design Patterns

-   [Adapter](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/adapter/ "Adapter Design Pattern in Go"). Allows for two incompatible classes to work together by wrapping an interface around one of the existing classes.
-   [Bridge](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/bridge/ "Bridge Design Pattern in Go"). Decouples an abstraction so two classes can vary independently.
-   [Composite](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/composite/ "Composite Design Pattern"). Takes a group of objects into a single object.
-   [Decorator](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/decorator/ "Decorator Pattern in Go"). Allows for an object’s behavior to be extended dynamically at run time.
-   [Facade](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/facade/ "Facade Design Pattern in Go"). Provides a simple interface to a more complex underlying object.
-   [Flyweight](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/flyweight/ "Flyweight Design Pattern in Go"). Reduces the cost of complex object models.
-   [Proxy](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/structural/proxy/ "Proxy Design Pattern in Go"). Provides a placeholder interface to an underlying object to control access, reduce cost, or reduce complexity.

### Behavior Design Patterns

-   [Chain of Responsibility](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/chain-of-responsibility/ "Chain of Responsibility Design Pattern in Go"). Delegates commands to a chain of processing objects.
-   [Command](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/command/ "Command Design Pattern in Go"). Creates objects which encapsulate actions and parameters.
-   [Interpreter](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/interpreter/ "Interpreter Design Pattern in Go"). Implements a specialized language.
-   [Iterator](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/iterator/ "Iterator Design Pattern in Go"). Accesses the elements of an object sequentially without exposing its underlying representation.
-   [Mediator](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/mediator/ "Mediator Design Pattern in Go"). Allows loose coupling between classes by being the only class that has detailed knowledge of their methods.
-   [Memento](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/memento/ "Memento Design Pattern in Go"). Provides the ability to restore an object to its previous state.
-   [Observer](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/observer/ "Observer Design Pattern in Go"). Is a publish/subscribe pattern which allows a number of observer objects to see an event.
-   [State](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/state/ "State Design Pattern in Go"). Allows an object to alter its behavior when its internal state changes.
-   [Strategy](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/strategy/ "Strategy Design Pattern in Go"). Allows one of a family of algorithms to be selected on-the-fly at run-time.
-   [Template Method](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/template/ "Template Method Design Pattern in Go"). Defines the skeleton of an algorithm as an abstract class, allowing its sub-classes to provide concrete behavior.
-   [Visitor](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/visitor/ "Visitor Design Pattern in Go"). Separates an algorithm from an object structure by moving the hierarchy of methods into one object.