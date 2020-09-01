---
title: 5. Modules
type: labs
draft: true
---

# Modules Lab

{{< devnote >}}
Replace the ISF Academy repo links
{{< /devnote >}}


We are going to write a lot of code this year, so we need to keep it organized. The most obvious way to do this is to store code in different files. But what if you want to re-use a function you wrote in a different file? Copy it over?  It feels like there should be a better way. Today we are going to learn how to import code from one module into another. But first, let's get some vocabulary straight:

- All python code lives in `files` that end in `.py`. They're just plain text files that you can edit using Atom (or Microsoft Word if you really want. Don't though. You'll regret it.)
- Like all files, python files live in directories somewhere on your file system. For example, all your homework lives in `/Users/you/Desktop/cs9/unit_00`.
- Python thinks of each file as a `module`. Each module is its own little bubble world.
- Python thinks of each directory containing `.py` files as a `package`. A package is a bundle of modules. So your `unit_00` directory is also a package.

## A. Importing
When you want to use something from another module, you need to `import` it. We have actually already been doing this--every one of our programs so far has started with `from turtle import *`. But what is this `turtle`? Where did it come from? Let's use the python shell to find out:

```shell
    TEA-JWOLF:~ jwolf$ cd Destop/cs9/unit_00
    TEA-JWOLF:unit_00 jwolf$ python
    >>> import turtle
    >>> turtle
    <module 'turtle' from '.../turtle.py'>
```

See? It's a module! And it lives in a file called `turtle.py` that some people wrote for you.

```shell
    >>> turtle.forward
    <function forward at 0x102f90d08>
```

There's our old friend `forward`, the function which makes the turtle walk forward. You can use
it just like normal:

```shell
    >>> turtle.forward(100)
```

There are actually three different ways to get `forward`. You can import `turtle`:

```python
    import turtle
    turtle.forward(100)
```

Or you can import `forward` from `turtle`:

```python
    from turtle import forward
    forward(100)
```

Or You can do it the way you are used to doing it:

```python
    from turtle import *
    forward(100)
```

This third way means "go into the turtle module and import everything!" It's quick and easy, but it's kind of sloppy and it's not always a very good idea. Imagine this scenario:

```python
    from bodily_functions import eat
    from refrigerator import *
    from trash_can import *

    eat(chicken_sandwich)
```

You can see that the `eat` function came from `bodily_functions`, but where did that `chicken_sandwich` come from? The `refrigerator`? Or the `trash_can`? By importing just what we need from other modules, we can make it clear where everything came from, and we can make sure we don't import stuff we don't want. (What else did we import from the `trash_can`? Do we want that in our program?)

**STOP! Before you go on, figure out how to open `turtle.py`. Have a look inside and show it to your teacher.**

## B. Finding modules
There are three places you can import modules from:

- Some modules, like `turtle`, come pre-installed with python. When you import them, python knows where to find them.
- Some modules were published online by other software developers. If you install them, you can use them too.
  Like the built-in modules, python knows where to find these when you import them.
- Finally, any modules that are in the same directory as your python file can be imported.

Now let's try importing some of the code you wrote in previous lessons. Let's use a tool called `tree` to see what we're dealing with. `tree` doesn't come built-in, so let's install it now:

** Don't forget to exit the Python shell before entering this command! Check to make sure you see the command line prompt!**

```shell
    TEA-JWOLF:unit_00 jwolf$ brew install tree
```

Now, let's have a look at all your work in this class so far. We're going to show a tree of `.`, which means "here" (whatever directory you're currently in).

```shell
    TEA-JWOLF:unit_00 jwolf$ tree .
    .
    ├── homework_01.py
    ├── homework_02
    │   └── zoo
    │       ├── elephant_house
    │       │   └── meet_the_elephants.txt
    │       ├── entrance.txt
    │       └── snake_house
    │           └── meet_the_snakes.txt
    ├── homework_03.py
    ├── homework_04.py
    ├── lab_00_terminal_adventure
    │   ├── adventure
    │   │   ├── seafloor
    │   │   │   ├── coral_reef
    │   │   │   │   ├── chest.py
    │   │   │   │   ├── reef.txt
    │   │   │   │   └── treasure.png
    │   │   │   ├── seafloor.txt
    │   │   │   └── sunken_ship
    │   │   │       ├── galley
    │   │   │       │   └── ghost.py
    │   │   │       ├── ship.txt
    │   │   │       └── stateroom
    │   │   │           └── desk.py
    │   │   └── sinking.txt
    │   └── end.py
    ├── lab_02.py
    └── lab_03.py
```

From the `unit_00` folder, we can import any of these `.py` files as modules. If they're in the same directory (like `homework_01.py`), we can just write `import homework_01`. Try it now:

```shell
    TEA-JWOLF:unit_00 jwolf$ python
    >>> import homework_01
```

Fond memories. You should have seen your homework 1 run again. This is because when you import a module, all the code in that module runs. What about subdirectories that contain `.py` files? Python thinks of these as packages. Remember that treasure chest from the {{< ref_module "lab_terminal_adventure" >}}? It's buried a few layers deep in packages, but we can get it.

```shell
    >>> import lab_00_terminal_adventure.adventure.seafloor.coral_reef.chest
```

Usually we use packages to group together code that belongs together.

Now we are going to download a package full of fancy drawing functions to turbocharge your turtle. Make sure you are in`unit_00` and then download it using git:

```shell
    TEA-JWOLF:unit_00 jwolf$ git clone https://github.com/the-isf-academy/drawing.git
```

You just downloaded a package called `drawing`. Let's learn about what's included. Run `tree drawing` to see what's inside.

**STOP! Once you have downloaded the `drawing` package and are confident that everyone in your group understands modules and packages, check in with a teacher.**

## C. Fancy drawings

Then read the [package documentation](https://github.com/the-isf-academy/drawing), which describes all the functions.

Create a file called `lab_04.py` in `unit_00`. Work with your group to try out the examples from the `drawing` documentation, and see what else you can figure out. You will turn this file in at the end of class. (You may look at each others' code and write code together during labs. But remember, you may never look at someone else's homework code or show someone yours.)

You might also be interested in reading the documentation for `turtle` to see what other drawing functions are available.

## Deliverables

- By the end of class, each student should upload a file called `lab_04.py`.
- This file should make a drawing using functions from the `drawing` package.