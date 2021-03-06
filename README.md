# H-Cat

Hierarchical file concatenation

Motivation
----------

Many config files or source files are too big to be in just one file. Splitting them up
makes them more readable and modular. However the language specifications do not
necessarily account for this. Utilities like 'cat' can combine files sequentially,
but sometimes it is preferable to have a hierarchical approach.

Idea
----

A simple combiner utility that pre-processes input files by reading them, and whenever it
encounters a '#include', it includes the indicated file at that point and recursively scans
that file. The result is a single stream of content that can be passed to the regular
processor.

Synopsis
--------

```
hcat <file> [<include-tag>]
```

file: The name of the topmost file.  
include-tag: An alternative include indicator, if '#include' is unsuitable.

Output is to the stdout.

Example
-------

file1.txt contains

    hello
      #include file2.txt
    world

file2.txt contains

    to all
    in the

output would be

    hello
      to all
      in the
    world

Notice that indentation is inherited.

License
-------

All original code is distributed under the Boost License
(see LICENSE.txt).
