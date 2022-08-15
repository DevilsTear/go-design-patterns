:house:[Home](https://github.com/DevilsTear/go-design-patterns/ "Table of Contents") | :file_folder:[Behevioral Design Patterns](https://github.com/DevilsTear/go-design-patterns/tree/main/gang-of-four/behavioral/ "Behavioral Design Patterns Table of Contents")
# Interpreter design pattern
Now we are going to dig into a quite complex pattern. The **Interpreter** pattern is, in fact,
widely used to solve business cases where it's useful to have a language to perform
common operations. Let's see what we mean by language.

The most famous interpreter we can talk about is probably SQL. 
It's defined as a special purpose programming language for managing data held in relational databases. 
SQL is quite complex and big but, all in all, is a set of words and operators that allow us to perform
operations such as insert, select, or delete.
Another typical example is musical notation. It's a language itself and the interpreter is the
musician who knows the connection between a note and its representation on the
instrument they are playing.

In computer science, it can be useful to design a small language for a variety of reasons:
repetitive tasks, higher-level languages for non-developers, or **Interface Definition
Languages (IDL)** such as **Protocol buffers** or **Apache Thrift.**

## Objectives
Designing a new language, big or small, can be a time consuming task so it's very important
to have the objectives clear before investing time and resources on writing an interpreter of
it:
- Provide syntax for very common operations in some scope (such as playing
notes).
- Have a intermediate language to translate actions between two systems. For
example, the apps that generate the **Gcode** needed to print with 3D printers.
- Ease the use of some operations in an easier-to-use syntax.

SQL allows the use of relational databases in a very easy-to-use syntax (that can become
incredibly complex too) but the idea is to not need to write your own functions to make
insertions and searches.

## Example – a polish notation calculator
A very typical example of an interpreter is to create a reverse polish notation calculator. For
those who don't know what polish notation is, it's a mathematical notation to make
operations where you write your operation first (sum) and then the values (3 4), so + 3 4 is
equivalent to the more common 3 + 4 and its result would be 7. So, for a reverse polish
notation, you put first the values and then the operation, so 3 4 + would also be 7.

## Acceptance criteria for the calculator
For our calculator, the acceptance criteria we should pass to consider it done are as follows:
- Create a language that allows making common arithmetic operations (sums,
subtractions, multiplications, and divisions). The syntax is sum for sums, mul for
multiplications, sub for subtractions, and div for divisions.
- It must be done using reverse polish notation.
- The user must be able to write as many operations in a row as they want.
- The operations must be performed from left to right.

So the 3 4 sum 2 sub notation is the same than (3 + 4) – 2 and result would be 5.

## Wrap up the Interpreter pattern
This pattern is extremely powerful but it must also be used carefully. To create a language,
it generates a strong coupling between its users and the functionality it provides. One can
fall into the error of trying to create a too flexible language that is incredibly complex to use
and maintain. Also, one can create a fairly small and useful language that doesn't interpret
correctly sometimes and it could be a pain for its users.

In our example, we have omitted quite a lot of error-checking to focus on the
implementation of the Interpreter. However, you'll need quite a lot of error checking and
verbose output on errors to help the user correct its syntax errors. So, have fun writing your
language but be nice to your users.