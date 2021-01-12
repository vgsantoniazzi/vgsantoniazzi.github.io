---
layout: post
title: How to teach programming through Repl.it
categories: [programming language]
---

I posted a month ago, a blog post about [Repl.it Lang Jam](https://repl.it/site/jam), and we created a team there https://repl.it/@tinylang.

In Tiny lang, we accept that other developers edit basic info from the language, like the regex to match `if` statements.

Right now, we have three versions of the language

- [English](https://repl.it/@tinylang/tiny-lang-english)
- [Portuguese](https://repl.it/@tinylang/tiny-lang-portugues)
- [Russian](https://repl.it/@tinylang/tiny-lang-russkii)

We are accepting pull requests to support new spoken languages. You can submit on [GitHub](https://github.com/vgsantoniazzi/tiny-lang), and I will build it to run in Repl.it.

## How to teach using repl.it

In the past, I taught programming to Brazilian children in Portuguese. At the time, I had to compile the lang in several computers and make sure that everything is okay before starting the class. It was five years ago, and we did not have Repl.it. Now it is much more accessible, with few clicks, anyone in the world without computer science knowledge can start writing the first lines of code in the primary language. This is what we are doing — enabling that people that do not know English learn how to do the first steps with programming.

## Writing the first lines in PT-BR.

Create an account on Repl.it.
Fork https://repl.it/@tinylang/tiny-lang-portugues
Click on `Run`
Edit `main.tl` to become your program
Edit `tokens/portugues.yml` to improve the language

You can copy and paste the following inside the `main.tl` to build your first control flow

```
imprimir "Qual a raiz quadrada de 16? ";

lerLinha associar numero resposta;

caso(resposta == 4)
  imprimir "Certa Resposta";
fim

imprimir "O programa chegou ao fim";
```

It's your turn. Have fun.
