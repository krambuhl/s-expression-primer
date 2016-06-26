# S-expression Primer

A primer for Lisp-style S-expressions, for those already familiar with C-family languages.  S-expressions are at the core of all Lisp-family languages (Lisp, [Clojure](http://clojure.org), [Scheme](http://www.scheme-reports.org))

## Thinking in S-expressions

In C-family languages we think of data structures (`Numbers`, `Strings`, `Arrays`, `Objects`), operators (`+`, `-`, `*`, `÷`, `++`, `==`), and control structures (`if/else`, `while`, `for`) as seperate concerns.  In Lisp-family languages we think of all these things as S-expressions.

### A Small Example

Let's take this expression using C-style that should feel familiar and convert it to Lisp style code.

```js
"Hello World".substr(1) == "ello World"
```

Let's first make one modification to help with a conceptual leap.  Instead of thinking of `==` as an operator, let's think of it as a method on the the `String` class.

```js
"Hello World".substr(1).equals("ello World")
```

Then we can rewrite this `object.method(...args)` format code into generic a `(function ...args)` format.

```lisp
(== (substr "Hello World" 1) "ello World")
```
