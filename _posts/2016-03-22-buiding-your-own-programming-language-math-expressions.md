---
layout: post
title: "Building your own programming language: Math Expressions"
categories: [programming language, open source]
---


Mathematical expressions are one of the most complex points when we are talking about compilers and interpreters.

> We will pass through how an interpreter works. If you want read the code before, just check the [tiny-lang repository on Github](https://github.com/vgsantoniazzi/tiny-lang).

## Solving Math
[There are countless ways to solve](https://archive.codeplex.com/?p=fastmathparser), and the easiest could be to use a mathematical expression parser, which is not the case with us. We want to create our own parser and make it more and more intelligent.

What makes this operation difficult is that we have to worry about countless cases: Transform this expression into reverse [Polish notation](https://www.technical-recipes.com/2011/a-mathematical-expression-parser-in-java-and-cpp/), use variables in the middle of the expression, validate the type (integer, floating-point, etc.), mandatory parentheses and even the type of algorithm to use.

## Math Operations
We will start with a case of expressions with the following operations: sum, subtraction, division, and multiplication. And for these operations, we have the following characteristics: Optional parentheses, expressions in common order, and variables.

Our interpreter now has to be able to prioritize parentheses and multiplications over addition and subtraction.

This type of analysis is a very good example of which we can use recursion. I actually find recursion to be one of the most fascinating points in software development. We will not hesitate to use it.

## Prioritize Math Operations
We have to do the [syntactic analysis](https://en.wikipedia.org/wiki/Parsing) of the mathematical expression, that is, prioritize the execution.[ Jack W. Crenshaw wrote this prioritization very intelligently](https://compilers.iecc.com/crenshaw/tutor4.txt). It consists of thinking that we have terms, expressions, and factors.
Terms are multiplications and divisions, expressions are sums and subtractions and factors are terms and expressions within parentheses.
Recursion should start with the lowest value operations until reaching the highest value. In other words: **When we have a mathematical expression (to be analyzed), we must follow the flow**:

- 1. Before executing a expression (addition and subtraction), search for terms. After the terms are processed, process the expression.
- 3. Before executing a term (multiplication and division), search for factors. After factors are processed, process the term.
- 2. Execute a factor (parentheses)
  - 2.1. There is nothing to do here, just call first point and use it recursively.

This value, it always starts from zero and is increased, decreased, multiplied and divided according to the operation we are carrying out.

Quite complex, [maybe with code is easier](https://github.com/vgsantoniazzi/tiny-lang/blob/master/src/evaluates/Evaluate.cpp).

## First problems
In this form of execution, we always work with integers, and this has a serious problem: 1/3 = 0; But as I mentioned: We want to create our own parser and make it more and more intelligent. In this initial idea with recursion, parentheses are optional and we have the correct order of priority.

Through this series of posts, we want to arouse curiosity in the creation of compilers and interpreters and offer valuable content to start the development of your language with its syntax.

## future.look()
The next and last step is to create control structures. See you there!
