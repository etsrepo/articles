FFI cookbook
============

This article describes how to handle different scenarios in order to write FFI bindings to interface a C library from Haskell. It was written primarily while creating the [couchbase-ffi][cb_hackage] package by me.



Low level bindings
------------------

In order to save you a lot of boilerplate (but not nearly enough), I recommend using the [bindings-dsl] package. It is a small collection of CPP macros to be included in your `.hsc` file that make your life a lot easier. I'll call the language using those macros *C-DSL*.



### Referring to types

Referring to other C types is done by putting them in angular braces, e.g. the C type `size_t` would be written `<size_t>`. Other types are Haskell types, e.g. `CInt` is the Haskell type to marshal C `int`s with.



### Structs

Structs are declared using multiple macros together. The correspondence between C and C-DSL are fairly straightforward, so an example will suffice.


```c
struct mystruct_t {
};
```

```c
//
#starttype TYPE
#field NAME , TYPE
#stoptype
```



### Functions



### Unions

Unions are a really poor version of sum types (e.g. `Either`). It basically means that a piece of memory can be read as different types, and the programmer has to know which one it is - the compiler has no idea (!).

#### Isolated unions



### Void pointers



[cb_hackage]: http://hackage.haskell.org/package/couchbase-ffi
[bindings-dsl]: http://hackage.haskell.org/package/bindings-DSL