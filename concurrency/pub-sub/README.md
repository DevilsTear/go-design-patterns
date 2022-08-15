:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Concurrency Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/concurrency/ "Concurrency Design Patterns Table of Contents")
# Concurrent Publish/Subscriber design pattern
In this section, we will implement the Observer design pattern which is a Behavioral pattern, 
but with a concurrent structure and thread safety.

The Observer pattern maintains a list of
observers or subscribers that want to be notified of a particular event. In this case, each
subscriber is going to run in a different Goroutine as well as the publisher. We will have
new problems with building this structure:
- Now, the access to the list of subscribers must be serialized. If we are reading the
list with one Goroutine, we cannot be removing a subscriber from it, or we will
have a race.
- When a subscriber is removed, the subscriber's Goroutine must be closed too, or
it will keep iterating forever, and we will run into Goroutine leaks.
- When stopping the publisher, all subscribers must stop their Goroutines, too.

## Objectives
The objectives of this publish/subscriber are the same as the Observer pattern. 
The difference here is the way we will develop it. The idea is to make a concurrent
structure to achieve the same functionality, which is as follows:
- Providing an event-driven architecture where one event can trigger one or more actions
- Uncoupling the actions that are performed from the event that triggers them
- Providing more than one source event that triggers the same action

The idea is to uncouple senders from receivers, hiding from the sender the identity of the
receivers that will process its event, and hiding the receivers from the number of senders
that can communicate with them.

In particular, if I develop a click in a button in some application, it could do something
(such as log us in somewhere). Weeks later, we might decide to make it show a popup, too.
If, every time we want to add some functionality to this button, we have to change the code
where it handles the click action, that function will become huge and not very portable to
other projects. If we use a publisher and one observer for every action, the click function
only needs to publish one single event using a publisher, and we will just write subscribers
to this event every time we want to improve the functionality. This is especially important
in applications with user interfaces where many things to do in a single UI action can slow
the responsiveness of an interface, completely destroying the user experience.

By using a concurrent structure to develop the Observer pattern, a UI cannot feel all the
tasks that are being executed in the background if a concurrent structure is defined and the
device allows us to execute parallel tasks.

## Example – a concurrent notifier
We will develop a notifier similar to the one we developed in Chapter 7, Behavioral Patterns
– Visitor, State, Mediator, and Observer Design Patterns. This is to focus on the concurrent
nature of the structure instead of detailing too many things that have already been
explained. We have developed an observer already, so we are familiar with the concept.

This particular notifier will work by passing around interface{} values, like in the
workers pool example. This way, we can use it for more than a single type by introducing
some overhead when casting on the receiver.

We will work with two interfaces now. First, a Subscriber interface:
```
type Subscriber interface {
    Notify(interface{}) error
    Close()
}
```
Like in the previous example, it must have a Notify method in the Subscriber interface
of new events. This is the Notify method that accepts an interface{} value and returns
an error. The Close() method, however, is new, and it must trigger whatever actions are
needed to stop the Goroutine where the subscriber is listening for new events.
The second and final interface is the Publisher interface:

```
type Publisher interface {
    start()
    AddSubscriberCh() chan<- Subscriber
    RemoveSubscriberCh() chan<- Subscriber
    PublishingCh() chan<- interface{}
    Stop()
}
```

The Publisher interface has the same actions we already know for a publisher but to work
with channels. The AddSubscriberCh and RemoveSubscriberCh methods accepts a
Subscriber interface (any type that satisfies the Subscriber interface). It must have a
method to publish messages and a Stop method to stop them all (publisher and subscriber
Goroutines)

## Acceptance criteria
Requirements between this example and the one in the Chapter 7, Behavioral patterns –
Visitor, State, Mediator, and Observer Design Patterns must not change. The objective in both
examples is the same so the requirements must also be the same. In this case, our
requirements are technical, so we actually need to add some more acceptance criteria:
- We must have a publisher with a PublishingCh method that returns a channel 
  to send messages through and triggers a Notify method on every observer subscribed.
- We must have a method to add new subscribers to the publisher.
- We must have a method to remove new subscribers from the publisher.
- We must have a method to stop a subscriber.
- We must have a method to stop a Publisher interface that will also stop all subscribers.
- All inter Goroutine communication must be synchronized so that no Goroutine is
  locked waiting for a response. In such cases, an error is returned after the
  specified timeout period has passed.

Well, these criteria seem quite daunting. We have left out some requirements that would
add even more complexity, such as removing non-responding subscribers or checks to
monitor that the publisher Goroutine is always on.

## Wrap up the concurrent Observer pattern
Example demonstrates how to take advantage of multi-core CPUs to build a
concurrent message publisher by implementing the Observer pattern. 
We have tried to show a common pattern when developing concurrent apps in Go
