---
title: Syntax
---

# Syntax

*Making with Code* is a static site built with [Hugo](https://gohugo.io/). You
will need to understand the basics of the Hugo framework to contribute. 
Content is written in markdown, which you can probably pick up just by looking at 
some of the existing content.

## Custom Shortcodes

### include_module

Includes the full content of a module (from the same unit) in a lesson.

```
{{</* include_module "lab_terminal_adventure" */>}}
```

### ref_module

Creates a link to a module (from the same unit) in a lesson.

```
{{</* ref_module "lab_terminal_adventure" */>}}
```

### ref_practice

Creates a link to a practice description. May be used on any content page. 

```
{{</* ref_practice "activity/help_queue" */>}}
```


### devnote

Use for notes and TODO items. Content within `devnote` is highlighted and only
shown in the `dev` environment. 

```
{{</* devnote */>}}
This lesson went horribly. Need to revise.
{{</* /devnote */>}}
```
