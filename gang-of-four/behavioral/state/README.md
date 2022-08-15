:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Behevioral Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/ "Behavioral Design Patterns Table of Contents")
# State design pattern
State patterns are directly related to FSMs. A **Finite State Machines (FSM)**, in very simple terms, is something that
has one or more states and travels between them to execute some behaviors. Let's see how
the State pattern helps us to define FSM.

A light switch is a common example of an FSM. It has two states–on and off. One state can
transit to the other and vice versa. The way that the State pattern works is similar. We have
a State interface and an implementation of each state we want to achieve. There is also
usually a context that holds cross-information between the states.

With FSM, we can achieve very complex behaviors by splitting their scope between states.
This way we can model pipelines of execution based on any kind of inputs or create event 
driven software that responds to particular events in specified ways.

## Objectives
The main objectives of the State pattern is to develop FSM are as follows:
- To have a type that alters its own behavior when some internal things have changed
- Model complex graphs and pipelines can be upgraded easily by adding more
states and rerouting their output states

## A small guess the number game
We are going to develop a very simple game that uses FSM. This game is a number
guessing game. The idea is simple–we will have to guess some number between 0 and 10
and we have just a few attempts or we'll lose.

We will leave the player to choose the level of difficulty by asking how many tries the user
has before losing. Then, we will ask the player for the correct number and keep asking if
they don't guess it or if the number of tries reaches zero.

## Acceptance criteria
For this simple game, we have five acceptance criteria that basically describe the mechanics
of the game:
- The game will ask the player how many tries they will have before losing the game.
- The number to guess must be between 0 and 10.
- Every time a player enters a number to guess, the number of retries drops by one.
- If the number of retries reaches zero and the number is still incorrect, the game
 finishes and the player has lost.
- If the player guesses the number, the player wins.

# Wrap up the State pattern
You must be thinking now that you can extend this game forever with new states, and it's
true. The power of the State pattern is not only the capacity to create a complex FSM, but
also the flexibility to improve it as much as you want by adding new states and modifying
some old states to point to the new ones without affecting the rest of the FSM.