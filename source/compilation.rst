Compilation
===========

Compilation process
-------------------

The Plinth compiler compiles source files (``.pth``) into bitcode files (``.pbc``), and optionally links them together into a single bitcode file.

Suppose we have a file called ``Hello.pth``, which contains a single class called ``Hello``, which has a main method. We can run the compiler as follows::

  plinth -o Hello.pbc
         -l /path/to/plinth.pbc
         -l /path/to/core-x86_64-linux.pbc
         --main-type Hello
         Hello.pth

This will compile ``Hello.pth`` into ``Hello.pbc``.

Because we said that ``Hello`` was the main type, ``Hello.pbc`` contains code to call the main method: ``Hello.main([]string args)``.

.. note::

   | ``-l /path/to/plinth.pbc`` tells the compiler to link in the plinth standard library, which contains definitions for ``string``, ``stdout``, and other important types.
   | ``-l /path/to/core-x86_64-linux.pbc`` tells the compiler to link in the plinth core runtime for x86_64 Linux systems.

   There are plans to simplify these options by using environment variables to specify a default set of files to import and link in.

Now we have a file called ``Hello.pbc`` which contains all of the LLVM code required to run the program. To execute it, we can use LLVM's interpreter ``lli``, or compile it to native code using LLVM's compiler ``llc`` followed by ``gcc``.

To execute a plinth program, the bitcode files can either be run via the LLVM interpreter (``lli``), or compiled to native code via LLVM's compiler::

  > lli Hello.pbc
  Hello, World!

  > llc Hello.pbc -o Hello.s
  > gcc Hello.s -o Hello
  > ./Hello
  Hello, World!



Compiler options
----------------


