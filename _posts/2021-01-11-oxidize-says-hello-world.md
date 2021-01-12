---
layout: post
title: Oxidize says Hello World!
categories: [operating system, open source]
---

Last week, I researched about boot, BIOS, UEFI, bootloader, compiler, and I was able to get my operating system to say something. In fact, are 230 lines of Rust to say "Welcome to Oxidize!!".

```bash
$ find . -name '*.rs' | xargs wc -l
 169 ./src/screen.rs
  12 ./src/screen/singleton.rs
  20 ./src/main.rs
  26 ./src/macros.rs
   3 ./target/bootimage/bootloader/x86_64-bootloader/release/build/bootloader-b884f8b2fd4061d3/out/bootloader_config.rs
 230 total
```

Look how beautiful it is. I can burn a CD-ROM to boot my operating system, and I'll!

The next step will be to create a driver for the keyboard since the driver to see things on the VGA port is done!

![Done]({{ site.url }}/images/posts/2021-01-11-oxidize-says-hello-world/os.png)

Follow [`vgsantoniazzi/oxidize`](https://github.com/vgsantoniazzi/oxidize) to be notified about the new changes.

See you!
