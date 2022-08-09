:house:[Home](https://github.com/DevilsTear/go-design-patterns/README.md "Table of Contents") | :file_folder:[Structural Design Patterns](https://github.com/DevilsTear/go-design-patterns/gangs-of-four/structural/README.md "Structural Design Patterns Table of Contents")
# Facade design pattern
We'll see in this chapter is the Facade pattern. When we discussed the
Proxy pattern, you got to know that it was a way to wrap a type to hide some of its
features of complexity from the user. Imagine that we group many proxies in a single point
such as a file or a library. This could be a Facade pattern.

A facade, in architectural terms, is the front wall that hides the rooms and corridors of a
building. It protects its inhabitants from cold and rain, and provides them privacy. It orders
and divides the dwellings.

The Facade design pattern does the same, but in our code. It shields the code from
unwanted access, orders some calls, and hides the complexity scope from the user.

## Objectives
You use Facade when you want to hide the complexity of some tasks, especially when most
of them share utilities (such as authentication in an API). A library is a form of facade,
where someone has to provide some methods for a developer to do certain things in a
friendly way. This way, if a developer needs to use your library, he doesn't need to know all
the inner tasks to retrieve the result he/she wants.

So, you use the Facade design pattern in the following scenarios:
- When you want to decrease the complexity of some parts of our code. You hide
that complexity behind the facade by providing a more easy-to-use method.
- When you want to group actions that are cross-related in a single place.
- When you want to build a library so that others can use your products without
worrying about how it all works.

## Example
As an example, we are going to take the first steps toward writing our own library that
accesses OpenWeatherMaps service. In case you are not familiar with OpenWeatherMap
service, it is an HTTP service that provides you with live information about weather, as well
as historical data on it. The HTTP REST API is very easy to use, and will be a good example
on how to create a Facade pattern for hiding the complexity of the network connections
behind the REST service.

## Acceptance criteria
The OpenWeatherMap API gives lots of information, so we are going to focus on getting live
weather data in one city in some geo-located place by using its latitude and longitude
values. The following are the requirements and acceptance criteria for this design pattern:
- Provide a single type to access the data. All information retrieved from
OpenWeatherMap service will pass through it.
- Create a way to get the weather data for some city of some country.
- Create a way to get the weather data for some latitude and longitude position.
- Only second and third point must be visible outside of the package; everything
else must be hidden (including all connection-related data).

## What's the difference between Singleton and Flyweight then?
Well, the difference is subtle but it's just there. With the Singleton pattern, we ensure that
the same type is created only once. Also, the Singleton pattern is a Creational pattern. With
Flyweight, which is a Structural pattern, we aren't worried about how the objects are
created, but about how to structure a type to contain heavy information in a light way. The
structure we are talking about is the map[int]*Team structure in our example. Here, we
really didn't care about how we created the object; we have simply written an
uncomplicated the getTeamFactory method for it. We gave major importance to having a
light structure to hold a shareable object (or objects), in this case, the map.