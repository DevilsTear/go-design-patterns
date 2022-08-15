:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Behevioral Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/ "Behavioral Design Patterns Table of Contents")
# Observer design pattern
The Observer pattern, also known as publish/subscriber or publish/listener. 
With the State pattern, we defined our first event-driven architecture, 
but with the Observer pattern we will really reach a new level of abstraction.

The idea behind the Observer pattern is simple–to subscribe to some event that will trigger
some behavior on many subscribed types. Why is this so interesting? Because we uncouple
an event from its possible handlers.

For example, imagine a login button. We could code that when the user clicks the button,
the button color changes, an action is executed, and a form check is performed in the
background. But with the Observer pattern, the type that changes the color will subscribe to
the event of the clicking of the button. The type that checks the form and the type that
performs an action will subscribe to this event too.

## Objectives
The Observer pattern is especially useful to achieve many actions that are triggered on one
event. It is also especially useful when you don't know how many actions are performed
after an event in advance or there is a possibility that the number of actions is going to grow
in the near future. To resume, do the following:
- Provide an event-driven architecture where one event can trigger one or more actions
- Uncouple the actions that are performed from the event that triggers them
- Provide more than one event that triggers the same action

## The notifier
We will develop the simplest possible application to fully understand the roots of the
Observer pattern. We are going to make a Publisher struct, which is the one that triggers
an event, so it must accept new observers and remove them if necessary. When the
Publisher struct is triggered, it must notify all its observers of the new event with the data
associated.

## Acceptance criteria
The requirements must tell us to have some type that triggers some method in one or more
actions:
- We must have a publisher with a `NotifyObservers` method that accepts a
message as an argument and triggers a `Notify` method on every observer subscribed.
- We must have a method to add new subscribers to the publisher.
- We must have a method to remove the subscribers from the publisher.