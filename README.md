# The Arith Language
Arith is a [Racket](http://racket-lang.org/) [\#lang](https://docs.racket-lang.org/guide/languages.html) 
implementation of arith. What's arith? It's about as basic as you can get with a language when you
want to talk about the statics and dynamics of a language. Mostly this is used for instructional
purposes, not for anything real-life. What's a \#lang? This means that if you get 
[Racket](http://racket-lang.org/), install this package and then at the top of your file
you use \#lang arith, you'll see that you can run programs. It also supports the interactive
command line that Dr. Racket provides, which is always fun!

What's great about arith is that it's so simple (you can barely call it a language) that it's easy
to understand all the typechecking and evaluation rules around it. What's even better is that it
serves as an easy way to show you how to implement a \#lang using Racket because there are so few
rules to implement it it's about as basic a \#lang as you can get. Also, I don't do any serious
macro magic--I'm sure things could be written in "cooler" ways, but the purpose is to understand
how to implement a \#lang. 

Note, we do use LALR parsing for arith, so you can see an example of how to use the parser. In
addition, we do build an AST first using structs in Racket--I mean I'm sure it's great and all
to go straight to [s-expressions](https://en.wikipedia.org/wiki/S-expression) like you see a lot of people do, but that's only useful if your
language doesn't need to do any manipulation of the AST. Truthfully, for arith, you could get
away with this (my first implementation did), but then I wanted to add types and things become
messy with all those cars and cdrs (I'm sure the hardcore schemers love this approach...). 
Personally, I appreciate the advanced language features like pattern matching that make programming
a joy and not a chore! Instead I take my AST and convert it to an [s-exp](https://en.wikipedia.org/wiki/S-expression) 
and then this gets expanded via macros. 

# Syntax
The arith language really has a few terms in it:

| term | meaning  | 
|------|---------:|
| t ::=|   *terms*|
| succ t | *successor of t* |
| pred t | *predecessor of t* |
| iszero t | *iszero test term* |
| if t then t else t | *if test* |
| 0     |  *0 term* |
| true  |  *true term* |
| false |  *false term* | 


| values | meaning |
|--------|--------:|
| 0      | *0 value* |
| succ v | *numeric value*|
| true   | *true value* |
| false  | *false value* |



