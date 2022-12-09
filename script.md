# CSCI 3155 Mini Project

# Marie Resman and Nic Perrault

# Script
## History
```
1930: Alonzo Church develops lambda calculus, a simple but powerful theory of function
1950: John McCarthy develops Lisp, the first functional language, with some influences from the lambda calculus, but retaining variable assignments
1960: Peter Landin develops If you See What I Mean, the first pure functional language, based strongly on the lambda calculus, with no assignments
1970: John Backus develops FP, a functional language that emphasizes higher-order functions and reasoning about programs. 
Robin Milner and others develop ML, the first modern functional language, which introduced type inference and polymorphic types.
1970-1980: David Turner develops a number of lazy functional languages, culminating in the Miranda system.
1987: An international committee of researchers initiates the development of Haskell, a standard lazy functional language.
2003: The committee publishes the Haskell 98 report, defining a stable version of the language.
```
## Background & Basics
```
Functional Programming:
Haskell is a purely functional programming language. Functional programming is style of programming in which the basic method of computation is the application of functions to arguments.
In imperative languages you get things done by giving the computer a sequence of tasks and then it executes them. While executing them, it can change state. For instance, you set variable a to 5 and then do some stuff and then set it to something else. You have control flow structures for doing some action several times. In purely functional programming you don't tell the computer what to do as such but rather you tell it what stuff is. The factorial of a number is the product of all the numbers from 1 to that number, the sum of a list of numbers is the first number plus the sum of all the other numbers, and so on. You express that in the form of functions. You also can't set a variable to something and then set it to something else later. If you say that a is 5, you can't say it's something else later because you just said it was 5. So in purely functional languages, a function has no side-effects. The only thing a function can do is calculate something and return it as a result. At first, this seems kind of limiting but it actually has some very nice consequences: if a function is called twice with the same parameters, it's guaranteed to return the same result. That's called referential transparency and not only does it allow the compiler to reason about the program's behavior, but it also allows you to easily deduce (and even prove) that a function is correct and then build more complex functions by gluing simple functions together.

Example Java: summing integers from 1 to 10 in java – computation method is variable assignment

Example Haskell : summing integers from 1 to 10 in Haskell – computation method is function application

Laziness:
A lazy language means that functions and data constructors don’t evaluate their arguments until they need them 

That means that unless specifically told otherwise, Haskell won't execute functions and calculate things until it's really forced to show you a result. That goes well with referential transparency and it allows you to think of programs as a series of transformations on data. It also allows cool things such as infinite data structures. Say you have an immutable list of numbers xs = [1,2,3,4,5,6,7,8] and a function doubleMe which multiplies every element by 2 and then returns a new list. If we wanted to multiply our list by 8 in an imperative language and did doubleMe(doubleMe(doubleMe(xs))), it would probably pass through the list once and make a copy and then return it. Then it would pass through the list another two times and return the result. In a lazy language, calling doubleMe on a list without forcing it to show you the result ends up in the program sort of telling you "Yeah yeah, I'll do it later!". But once you want to see the result, the first doubleMe tells the second one it wants the result, now! The second one says that to the third one and the third one reluctantly gives back a doubled 1, which is a 2. The second one receives that and gives back 4 to the first one. The first one sees that and tells you the first element is 8. So it only does one pass through the list and only when you really need it. That way when you want something from a lazy language you can just take some initial data and efficiently transform and mend it so it resembles what you want at the end.

Statically Typed:
When you compile your program, the compiler knows which piece of code is a number, which is a string and so on. That means that a lot of possible errors are caught at compile time. If you try to add together a number and a string, the compiler will whine at you. Haskell uses a very good type system that has type inference. That means that you don't have to explicitly label every piece of code with a type because the type system can intelligently figure out a lot about it. If you say a = 5 + 4, you don't have to tell Haskell that a is a number, it can figure that out by itself. Type inference also allows your code to be more general. If a function you make takes two parameters and adds them together and you don't explicitly state their type, the function will work on any two parameters that act like numbers.

Core Haskell:
Good to write tests as you write code. We did that often in this class. Haskell has a library to test interactively. Since Haskell is Purely functional, it makes pure functions easy to test

```