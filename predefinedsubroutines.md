---
layout: default
title: Chipset
---
# Predefined routines

Predefined routines are a new set of routines that simplify application development.

## Why not macros
Macros are usually the best way for libraries. They define a block of code which is never allocated in memory until you call them.
Macros can also have parameters which can modify behavior. These are the main reason for high usage in <code>c128lib</code>.

Cons of macros is that everytime you call them, a new block of code is allocated and this is againts [Dry software principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

## Subroutine carefully
In this term, subroutine is a better solution because it's defined only once and can be called a number of time without affecting memory allocation.
But, cons is that when defined, subroutine uses you memory space, even if don't use it.

So <code>chipset</code> uses a solution that provide subroutine support behind a guard. Every subroutine is allocated (and available) only if guard is defined in your code. Let's see an example.

In Vdc module there is a subroutine called <code>FillScreen</code>.
When you include vdc.asm, this subroutine is not available because its guard <code>FILLSCREEN</code> it's not defined (and you'll get an error).

If you define guard like this in your code:
```assembly
...
#define FILLSCREEN
...
```
you can use subroutine with this statement
```assembly
...
jsr c128lib.Vdc.FillScreen
...
```

Every subroutine defines guard needed for its code so you only have to define subroutine guard.

So it's up to you to define guard only for subroutines that you really use and need.
