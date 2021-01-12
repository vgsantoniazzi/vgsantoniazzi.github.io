---
layout: post
title: "Building your own programming language: Flow and Tokenizer"
categories: [programming language, open source]
---


When dealing with the flow, compilers and interpreters are different. In the case of an interpreted language, operations are performed until the declarations (assignments, control structures, data output, etc.) are finished or some type of error is generated.

Interpreters analyzes the statement and then execute it. A compiler, on the other hand, transforms all the code into assembly and then executes it. Of course, not all languages are like that, we have some non-standard cases. Like JIT compilers.

> We will pass through how an interpreter works. If you want read the code before, just check the [tiny-lang repository on Github](https://github.com/vgsantoniazzi/tiny-lang).

## Interpreters

A [basic flow of an interpreter](https://github.com/vgsantoniazzi/tiny-lang/blob/master/src/Interpreter.cpp) is similar to the case below.

```cpp
int main(int argc, char *argv[])
{
  Tokenizer program(argv[1]);
  Statement *statement;
  while(program.Remaining())
  {
    statement = Statement::GetNext(program);
    statement->Execute();
  }
  return 0;
}
```

Let’s call the file we received as a program argument. This program has several statements. While there are statements available, we take the next one and execute it.

## Compilers
The case for a compiler is a little different. We will see.

```cpp
int main(int argc, char *argv[])
{
  Tokenizer program(argv[1]);
  Statement *statement;
  while(program.Remaining())
  {
    statement = Statement::GetNext(program);
    statement->GenerateCode();
  }
  program->Dump();
  return 0;
}
```

While we have declarations, we generate the assembly code, and in the end we execute the generated code.

From now on we will see only see structures and code for interpreters. If you want to read more about compilers, this is a very good book: [http://www.compilers.iecc.com/crenshaw/tutorfinal.pdf](http://www.compilers.iecc.com/crenshaw/tutorfinal.pdf)

## Lexical Analyzer
To start the implementation, we need to take the lexemes and turn them into interpretable tokens. We call it lexical analysis!

There are several ways to do this analysis, the most common is to read character by character and separate when we have space or some other special character other than the type previously read. Let’s look at two possible cases:

```
  value = 10;
  value=10;
```

If a lexical analyzer passes both code snippets, it will return the following lexemes:

```
  "value" -> VARIABLE
  "="     -> ASSIGNMENT
  "10"    -> INTEGER
  ";"     -> SEMICOLON
```

We analyzed the entire code snippet correctly. The Tokenizer of that link is a very simple example of how to do this.

## Variables
To finish the flow and be able to see something functional already in this post, we need to be able to have variables and update their values ​​(a variable always exists!! But if it hasn’t been set yet, it is null). We will be able to analyze a piece of code and save a variable.

We need a singleton class to store these variables. Let’s put its lifetime as the whole application. At the moment we will not have variables by scope. That way we have a complete flow, without worrying too much about details. We won’t worry about typing yet.
An C ++ implementation [would look something like this](https://github.com/vgsantoniazzi/tiny-lang/blob/master/src/variables/Variables.cpp).

## Next steps
Now that we have a sense of the complete process, we can continue to implement more features. We also need to: Analyze and execute mathematical expressions, create output structure, control structure and so on. We will go through these points in the next posts!
