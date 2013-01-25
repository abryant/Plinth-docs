Introduction
============

The Plinth programming language is designed to allow you to write fast, safe, object oriented code, with minimal verbosity.

Notable Features
----------------

* Not-null types

  By default, all types in Plinth are not-null, meaning that the language can check that a value is not null at compile time instead of run time.

* Immutability

  Types can be marked as immutable, to denote that data they contain cannot be modified.

* Compiles to native code

  Plinth uses LLVM to compile to machine code for whichever OS/processor you want to target. It can also compile to a platform-independant bitcode format.

