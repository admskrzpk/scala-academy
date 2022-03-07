# Day 1

## Operating System

The workshop is on Windows 11 with Windows Subsystem for Linux (WSL) / Ubuntu.

## Development Tools

Installing the development tools:

1. OpenJDK 11 (WSL/Ubuntu and Windows)
1. IntelliJ IDEA (Windows) + the Scala plugin
1. sbt

## Topics

1. Created a Scala project to display "hello world" in IntelliJ IDEA (a Scala/sbt project)
    * `object`
    * `extends App`
    * `println`
1. Using sbt
    * `compile`
    * `run`
    * `~` + `~run`
    * `console`
    * `build.properties`
1. Scala REPL using `sbt console`
    * `build.sbt` to set the Scala version
    * REPL = read-eval-print loop
    * Scala types (String, Integer, Long, Char, Boolean)
    * `res` values
    * `val` keyword
    * TAB completion
1. [Scala for the Impatient](https://horstmann.com/scala/) book
    * Parts of Chapter 1 "The Basics"
    * Up to and including the Exercises on page 11
    * Optional parentheses for methods with no parameters
    * Optional semicolon
# Day 2

## Topics

Working with the [Scala for the Impatient](https://horstmann.com/scala/) book

### Chapter 1

1.2 Declaring Values and Variables

* `val`s
* Optional types

1.3 Commonly Used Types

* All types are classes
* Invoking methods
* [StringOps](https://scala-lang.org/api/2.13.8/scala/collection/StringOps.html)

1.5 Calling Functions and Methods

* [Function vs Method](https://docs.scala-lang.org/tour/basics.html)

1.6 The apply Method

* [With apply you don't need new](https://docs.scala-lang.org/overviews/scala-book/case-classes.html#with-apply-you-dont-need-new)

1.7 Scaladoc

* <https://docs.scala-lang.org/style/scaladoc.html>
* <https://www.scala-lang.org/api/2.13.8/>

### Chapter 2

Expressions

2.1 Conditional Expressions

* `if`s

2.3 Block Expressions and Assignments

2.4 Input and Output

* `print`
* `println`
* `readLine(prompt)`
* `read` methods

2.7 Functions

2.8 Default and Named Arguments

2.12 Exceptions

* `try-finally` statement

Exercises (page 26)

* 1
* 5

# Day 3 (Thu)

## Opening Questions

1. Are there any questions about the Scala topics covered?
1. What do you think was the most important Scala feature covered yesterday?

## Topics

Continuing development of `calculator` project as the foundation to teach the following:

1. Refactoring in IntelliJ IDEA
    * Rename
    * Extract Method
    * Override
1. `if` expression
    * Predicates as Scala methods
    * Complex conditions using `&&` and `||`
    * Expressions vs statements

Others:

Working with the [Learning Scala](https://www.oreilly.com/library/view/learning-scala/9781449368814/) book

1. `sbt console`, Scala REPL and `:paste`
1. Scala worksheet
1. `class User(name: String)`
1. `def toString`

# Day 4 (Fri)

## Opening Questions

1. Are there any questions about the Scala topics covered?
1. What was the most important Scala feature that we covered during the last session?

## Exercise: User Class

Define `User` class with `greet` method that says "Hello from $name" when executed.

## Scala Topics

1. `val` vs `def`

    size("hello")  // funkcja
    "hello".size   // metoda

1. `class User(name: String)` vs `class User(val name: String)` (note `name` parameter)

## git

* git installation on Windows 11
* git commmands
  * `init`
  * `status`
  * `add`
  * `commit`
  * `log`
  * `diff` (`head..head~1`, using commit shas)

## Scala Topics

* [scala.Predef](https://www.scala-lang.org/api/2.13.8/scala/Predef$.html)
* [Scaladoc](https://www.scala-lang.org/api/2.13.8/)
* `String` (it's `java.lang.String`)
  * [scala.collection.StringOps](https://www.scala-lang.org/api/2.13.8/scala/collection/StringOps.html)
* Higher-Order Functions (HOFs)
  * `filter`
  * `sortBy`
  * `foreach`
* Underscore to mark unused input arguments to a function

      val size: String => Int = _ => 5

* `assert`

      assert(size("hello") == "hello".size)
  
      assert("hello".sortBy(c => c.toInt) == "ehllo")
      assert("hello".sortBy(_.toInt) == "ehllo")

* procedure vs method vs function
  * methods = class members
  * functions = standalone named executable block
  * procedure = method that returns nothing (`Unit`)

## Exercise: StringOps Favorities

Pick two methods of [scala.collection.StringOps](https://www.scala-lang.org/api/2.13.8/scala/collection/StringOps.html) and use Scala Worksheet with `sbt console` to learn how to use them:

1. `++`, `concat`
1. `filter`
1. `drop`
1. `apply`
1. `sortBy`
1. `tail`
1. `foreach`

## Exercise: Convert function to method

Convert the `f` function to be a `def` to be used in `filter`.

    val f: Char => Boolean = c => c != 'e' && c != 'o'

    def f_def... = ???
    "hello".filter(f_def) == "hll"

## Exercise

Write `last` function that works like `StringOps.last` and uses the methods of `StringOps` we talked about today (except `last`).

    val last: String => Char = ???

Hint: Use `size` and `apply`

## Learning Scala

Working with the [Learning Scala](https://www.oreilly.com/library/view/learning-scala/9781449368814/) book, Chapter 8 "Classes".

## Homework

Write `nth` function that returns the character at `n`-th position.

    nth(s: String, n: Int): Char

Assume `n` as `0 <= n < s.length`.

# Day 5 (Mon)

## Opening Questions

1. Are there any questions about the Scala topics we covered so far?
1. What was the most important Scala feature that we covered during the last session?

## Review Homework

Write `nth` function that returns the character at `n`-th position.

    nth(s: String, n: Int): Char

Assume `n` as `0 <= n < s.length`.

## Placeholder Syntax

[Learning Scala](https://www.oreilly.com/library/view/learning-scala/9781449368814/) book, page 72

1. Function literals
    * Rocket operator `=>`
1. Demo: `doubler: Int => Int` function
1. Demo: `safeStringOp(s: String, f: String => String): String` to return the result of executing `f` on the input `s` string when `s != null`
1. Exercise: Write a higher-order function (similar to the above) that accepts three input arguments (`x` and `y` ints and a `f` function that accepts two ints to produce an int) that executes `f` on the two ints. How to execute it?

       def combination(x: Int, y: Int, f: (Int, Int) => Int): Int

1. Very useful for Scala Collections library (that's coming up next)

## Scala Collections Library

[Learning Scala](https://www.oreilly.com/library/view/learning-scala/9781449368814/) book, Chapter 6, page 83

Package: [scala.collections](https://www.scala-lang.org/api/2.13.8/scala/collection/index.html)

* [immutable](https://www.scala-lang.org/api/2.13.8/scala/collection/immutable/index.html)
* [mutable](https://www.scala-lang.org/api/2.13.8/scala/collection/mutable/index.html)

Data structures for collecting one or more values of a given type:

1. `Array`
1. `List`
1. `Map`
1. `Set`
1. _others_

Building block of modern software projects

[Iterable](https://www.scala-lang.org/api/2.13.8/scala/collection/Iterable.html) - the foundation for iteration and manipulation

**Demo**: Creating instances of `List`, `Set` and `Map`

**Exercise**: Review the scaladoc of `List`. Pick two higher-order methods (methods with a function argument). Write a sample code for each (to demo how they work).

**Exercise**: Create a `List` of `List`s.

`Nil` special "end" object

**Exercise**: Create a `List` of 5 numbers and find the ones that are less than 3.

**Exercise**: Create a `List` of strings and apply `toUpperCase` on each

1. Mapping List, p. 92
1. Reducing Lists, p. 93-94
1. List folding, p. 97
1. Converting Collections, p. 98

## Exercises

[Learning Scala](https://www.oreilly.com/library/view/learning-scala/9781449368814/) book, page 102:

1. 1, 2, 3, 4, 5, 6

