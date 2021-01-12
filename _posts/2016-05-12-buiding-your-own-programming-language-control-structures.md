---
layout: post
title: "Building your own programming language: Control Structures"
categories: [programming language, open source]
---


Well, we have reached the last part of this series. The idea so far was to give a little more understanding of how an interpreter works in a minimalist way.

> We will pass through how an interpreter works. If you want read the code before, just check the [tiny-lang repository on Github](https://github.com/vgsantoniazzi/tiny-lang).

In the second post, we talked about tokens and tokenizer. The goal here is to use this mechanism to implement a module in our interpreter: Understand a measly if.

## Control Structures
To begin with, the level control structure is enough to confuse you. We then need to create a module and think of an ideal flow.

When we need to support nested control structures, it become difficulty.

We have the program object, a Tokenizer object that has an array of Token objects and methods to perform some actions that we want. For example `program.Match(IF);`.

When used, we expect the string if to be present exactly in the next token to be consumed. If so, the next token in the list is the second one, and it is repeated until you finish reading the file. If false, we have to throw an exception because we expected a string in the program, and this condition was not met.

## Optional Parenthesis
To have optional parentheses, we need to have a slightly different action. The idea is the same but we do not throw an exception.

```cpp
    program.MatchIf(OPEN_PARENTHESIS);
```

These behaviors can be found in more detail [here](https://github.com/vgsantoniazzi/tiny-lang/blob/master/src/tokenizer/Tokenizer.cpp).

Now that we have a base of how we need to do it, we need to follow a basic flow:

Read and store the test value within the if;

- Save all the next Statements in an array until reaching the end of the if (Token END or string “end”);
- Test the if condition, if true, execute all Statements in the order they were received.

## Modules
With that flow defined, we now have to implement. The language I am developing has modular support. A simple way to add a new module [is shown in this pull request to support threads](https://github.com/vgsantoniazzi/tiny-lang/pull/10/files).

We created a new type of *Statement*, child of the Statement class, in the *SpawnStatement* case. We need to implement both methods: Read and Execute. Read is responsible for obtaining all the information it needs to execute and Execute executes.

The way to obtain information whether it is this module to execute or not, is the task of the Statement itself. Crazy.

The Statement should be able to read the first Token and work as a task distribution channel. According to the first Token read, it is able to select which statement module to execute the code.

## First Control Structure Version
*IfStatement*, in this way, is dumb enough not to support nesting, but smart enough to execute or not the next Statement. Dumb because it loads the Statement if the condition is true or false. Maybe this is so smart that a thread changes the value of some variable, and our interpreter doesn’t see it. Language feature, sometimes called characteristic 😂.

Well, every day I face functional problems like this, and I always have to decide which way to go (or not).

I really hope that this mini-micro-minimalist-series has helped you get a little more insight into how things work in a simplistic way inside an interpreter. ;

## High Level Programming Languages
Currently, programming languages have more features, smarter algorithms. We have languages that are interpreted and compiled, curly, and thus, things get more interesting.

## Take A Look
A lot of new programming languages are built on top o [LLVM](https://llvm.org/). Next time, I'll build a version of tiny-lang on top of LLVM with Just In Time compiler.
