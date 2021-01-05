---
layout: post
title: Welcome to Oxidize
categories: [operating system, open source]
---

I decided to create a new operating system to learn Rust. I'd built one operating system before, if I remember correctly, it was in 2014, after reading [Operating Systems: Design and Implementation Second Edition from Tanenbaum](https://www.amazon.com/Operating-Systems-Design-Implementation-Second/dp/0136386776).


De facto, I'd done something similar, but I want to do with a new programming language on top of LLVM, so I chose Rust.

## Repository

I started the repository at [`vgsantoniazzi/oxidize`](https://github.com/vgsantoniazzi/oxidize) and I'll keep the updates there.

The structure will follow the following pattern

```bash
.
├── Cargo.lock   # Cargo's locked configs
├── Cargo.toml   # Cargo's package manager configs
├── LICENSE      # MIT License
├── Makefile     # Easy to understand and use configuration files
├── README.md    # General README. With usage and how-to documentation.
├── src          # Rust language files
│   └── main.rs  # Main file
└── target       # Compiled sources.
```


## Naming

[Alex wrote about software naming](https://alexoliveira.cc/software-naming.html) in the past. I recommend you to read it. I chose oxidize because it happens because of rust, and eventually I'll stop maintaining, so it will oxidize.

## Next steps

My idea is to finish a couple of predefined tasks, and keep the entire system modular. So I want to support a new filesystem, I just need to create — and append, a module to it. The same with high-level modules, such as commands and text editors.

What I have in mind for this repository

1. Booting
  - I want to be able to eventually write a flash drive and boot in a x86 machine.
2. Terminal
  - I want to be able to write commands and it will produce an output — similar to REPL, or open a new program, such as text editor.
3. Text editor
  - I want to write — or support, a small VI-like text editor.
4. Filesystem
 - I want to create a simple and usable filesystem, with commands such as `ls`, `cat`, and `touch`.

## Contributing

This is an open source project, you can help me to accomplish this. I would love to receive your input!

![Done]({{ site.baseurl }}/images/posts/2021-01-05-welcome-to-oxidize/os.png)