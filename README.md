# S-expression Primer

A primer for Lisp-style S-expressions, for those already familiar with C-family languages.  S-expressions are at the core of all Lisp-family languages (Lisp, [Clojure](http://clojure.org), [Scheme](http://www.scheme-reports.org))

## Thinking in S-expressions

In C-family languages we think of data structures (`Numbers`, `Strings`, `Arrays`, `Objects`), operators (`+`, `-`, `*`, `÷`, `++`, `==`), and control structures (`if/else`, `while`, `for`) as separate concerns.  In Lisp-family languages we think of all these things as S-expressions.

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

```Lisp
(== (substr "Hello World" 1) "ello World")
```

### No More Order of Operations

While writing code using S-expressions there is no need to consider Operator precedence, because it simply doesn't need to exist.

```js
1 + 3 + 5 * 7 % 8
```

Can be rewritten without precedence using Lisp-style expressions.

```lisp
(+ 1 3 (% (* 5 7) 8)
```

### Mapping and Recursion Instead of Looping

If you've modeled any problem in C-family languages, you've probably come into some sort of looping procedure.  This type of control logic doesn't always map directly to a Lisp-family equivalent, but there is usually a function to do a similar manipulation.

This is a fundamental difference. In Lisp languages all code _is_ data, where in C languages data and control structures are separated.

Let's say we have an array of people and we want to create a new array with only doctors included.

```js
const people = ["Mr. Hanky", "Towlie", "Dr. Alphonse Mephesto"]
let doctors = []
for (let i = 0; i < people.length; i++) {
  if (people[i].indexOf('Dr.') !== -1) {
    doctors.push(people[i])
  }
}
// doctors == ["Dr. Alphonse Mephesto"]
```

Every time we pushed a person into the doctors array above would be considered a side-effect in functional parlance.  In Lisp-style languages reduce type functions are used instead.

```clojure
(def people ["Mr. Hanky", "Towlie", "Dr. Alphonse Mephesto"])
(def doctors
  (filter
    (fn [person] (string/includes? person "Dr."))
    people))
```
