---
layout: post
title: Building your own programming language
categories: [compilers, interpreters, programming-languages, c, c++]
---

When I started in software development, I gathered a huge amount of links, books, and articles to study, but I was never able to succeed.

I adopted a form of study where I separated all material about programming languages that I have, just for research.

Who never wanted to be a hacker one day? It was with this research that I arrived on some websites about assembly and machine language. I went through almost all the content it has, I really wanted to know how programming languages work. If you are a developer, you probably have a kind of yearning to understand how things work.

This study of assembly, registers, and processors got me thinking about the most modern programming languages, like C ++, Ruby, and Python.

I ended up dropping the hacker side and studying more about how a computer really works.

This area of compilers and interpreters is very complex. I wrote a compiler, after an interpreter, but it is nowhere near a good and intelligent interpreter. Let’s go through all the points that we need to know to write a simple interpreter. Just like I did with tiny-lang.

> We will pass through how an interpreter works. If you want read the code before, just check the [tiny-lang repository on Github](http://github.com/vgsantoniazzi/tiny-lang).

## Main Points

Before starting, I wrote a summary with the main points to be addressed:

1 — Introduction

2 — Flow and tokenizer

3 — Mathematical Expressions

4 — Control Modules and Structures

We will go through these modules in different posts.


## How output file looks like
A compiler is developed to translate, in a humanized way, a machine language. In other words, generate assembly.

To see it in action, create a file called `example.cpp` with the following code:

```cpp
int main(int argc, char *argv[]){ return 0; }
```

And now, compile like the following way.

```bash
g++ example.cpp -S
```

The `-S` argument generates the assembly without executing, open the `example.s` file and you will see the generated assembly code.

## Compiled programming languages
A compiled language has to know which environment it is running with. Processor, operating system, 32 or 64 bits, all matters! Currently, the great advantage of writing a compiler is: “you need to write embedded software to run on a Marvel PX A310 processor”.

You need to create a programming language that generates the assembly to run on this type of processor. Or build a `C` compiler to run on it.

## Interpreted programming languages
The interpreted languages ​​run in any environment (if supported), just install. Ruby has several interpreters (some them are compilers), you may have heard of them: MRI, JRuby, RubyMotion, and so on. Official interpreter is [ruby/ruby](https://github.com/ruby/ruby).

They all use Ruby syntax and run in different environments. The code is interpreted (or compiled) for the desired platform.

## C written in C
And that story of a good compiler/interpreter must be written in the language itself? It’s awesome! A language is interpreted first and then compiled. Take C for example, before it was an interpreter, and using this interpreter, the compiler was written.

Currently one of the best sources of research on compilers is the [Dragon Book](https://www.amazon.com/Compilers-Principles-Techniques-Tools-2nd/dp/0321486811). I will also leave a bibliography of links that I have that can help you develop your compiler/interpreter.

## Features Overview
A programming language must know how to solve mathematical expressions.

It is not just a sum, it is all operations and in order of priority. I can assure you that it is not an easy task. It is the minimum we need to start. Then we have assignments, control structures, and so on.

In the following posts, we will write an interpreter. Perform mathematical operations, we will have some control structures, we will implement analysis on the code to be executed, and leave it modular so that in the future we can write more structures, methods and improve the analysis. Exactly like tiny-lang is.

**Set a starting point for your language.** I like ruby-like (optional parentheses) and explicit expressions (1 + 2 + 3 + 4). If you prefer a lisp style, you can use a polish notation. Think about the details, describe examples of operations you want to perform.

If you want to get your hands dirty now, I suggest studying the tiny-lang source code and translating it into another language for non-English learners — Mandarim, maybe!?

Helping those who are just starting to program and don’t have the minimum knowledge in English would be a great idea.

Find the location of the lexemes for tokens and change the tokens that match: `if`, `print`, `end`, and so on.

## Let's built it

In the next post, we will build flow management and writing a simple tokenizer. For now, you can learn a little bit more about how assembly works and try to execute the [Kompilator project](https://github.com/vgsantoniazzi/kompilator). *Kompilator* stands for compiler in Polish. Since is a polish notation compiler, I just find the name funny.




