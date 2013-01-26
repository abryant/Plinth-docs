Introduction
============

The Plinth programming language is designed to allow you to write fast, safe, object oriented code, with minimal verbosity.

Notable Features
----------------

* Rich type system

  Plinth has more than just the basic set of primitive, array, and class types. It also supports functions, value types, and tuples.

* Compiles to native code

  Plinth uses LLVM to compile to machine code for whichever OS/processor you want to target. It can also compile to a platform-independant bitcode format.

* Not-null types

  By default, all types in Plinth are not-null, meaning that the language can check that a value is not null at compile time instead of run time.

  Another benefit of this is that all types can be made nullable, for example ``?int`` is a nullable ``int``.

* Immutability

  Types can be marked as immutable, to denote that data they contain cannot be modified. Similarly, methods can be marked as immutable to denote that they do not modify anything.

* Binary compatibility

  Maintaining a library in Plinth is much easier than in C++, because it allows you to change much more while remaining binary compatible. Adding new (virtual) methods doesn't break binary compatibility, and version-specific overrides are possible for static methods.

