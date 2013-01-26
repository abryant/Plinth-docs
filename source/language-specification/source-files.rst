.. highlight:: java

Source Files
============

Plinth source files can contain any of the following three things:

* A package specifier (optional).
* Any number of imports.
* Any number of type definitions.

Packages
--------

Packages are a hierarchical structure which contain type definitions. A package specifier must be at the beginning of a source file, and declares a list of sub-packages from the root of the package tree. For example::

    package foo.bar;

Any type definitions in this source file would now be in the package ``foo.bar``.

Packages are used in name resolution, to say which type to resolve more explicitly. For example, if there was a class called "Hello" inside the package ``foo.bar``, we can almost always refer to it using ``foo.bar.Hello``.

When resolving a named type (such as ``foo.bar.Hello``), we try to look up the first part of its name (``foo``) in the following places (in order):

* The type definitions in the same source file (i.e. look for a class called ``foo``).
* The imported type definitions (i.e. see if any of the imports are for ``foo``).
* The sub-packages and type definitions of this package (i.e. if we are in ``test``, see if there is a ``test.foo``).
* The sub-packages and type definitions of the root package (i.e. check for a top-level package or type called ``foo``).

Imports
-------

Imports are a way of resolving type definitions more easily. Instead of always writing ``foo.bar.Hello``, we can import it as follows::

    import foo.bar.Hello;

This imports ``Hello`` into the source file's scope, so that it can be referred to as ``Hello`` instead of ``foo.bar.Hello``.

When resolving an import, we always start in the root package.

There are also wildcard imports, which specify that everything in a given package should be imported. For example, to import everything in ``foo.bar`` we can do::

    import foo.bar.*;

Type Definitions
----------------

There are several different sorts of type definitions, and their semantics are defined in the next section:

.. toctree::
   :maxdepth: 2

   type-definitions

There are no restrictions on the names of type definitions in a given source file.

