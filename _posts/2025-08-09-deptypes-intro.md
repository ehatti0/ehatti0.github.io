---
title: Dependent types for programmers
---

I'll use tagged unions to introduce dependent types. Here's a tagged union `int_or_char`.
```c
enum int_or_char_tag {
    INT_TAG,
    CHAR_TAG
}
union int_or_char_data {
    int int_data;
    char char_data
}
struct int_or_char {
    enum int_or_char_tag tag;
    struct int_or_char_data data;
}
```

An issue is that in order to be used safely, we must make sure to update the tag whenever we update the data. If we don't, we could mistakely treat an `int` like a `char` or vice versa. Key idea: The type system isn't preventing us from making mistakes.

Let's imagine we added dependent types to C. This is what a safer version of the type would look like.
```c
struct int_or_char {
    enum int_or_char_tag tag;
    (int_or_char_tag == INT_TAG : int ? char) data;
}
```
Dependent types allow types to be **computed** from data which may only be known at runtime. In this example the type of `data` is now an _expression_ which reads the `tag` field and returns either `int` or `char`. This new type would prevent us from making a mistake:
```c
struct int_or_char example;
example.tag = INT_TAG;
// Type error: expected an `int`, got a `char`
example.data = 'a'
```
```c
struct int_or_char example;
example.tag = INT_TAG;
// This typechecks
example.data = 33
```

Let me reiterate this: **Dependent types allow types to be computed from data which may only be known at runtime.** Because of this, typechecking in dependently-typed languages can be very complex. Allowing types to depend on runtime values means you essentially have to do **symbolic computation** during typechecking.

This isn't an explanation of dependent type<em>checking</em> though, so I'll leave it at that. Dependent types as a concept are pretty simple! It's implementing them that is hard.
