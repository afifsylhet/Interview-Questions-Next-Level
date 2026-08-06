# JavaScript Fundamentals – 25 Interview Questions & Answers

*Simple, beginner-friendly answers for full stack developer interview prep.*

---

## Part 1: Your Mentor's Questions (Q1–Q15)

### Q1. What is the difference between var, let, and const in JavaScript?

- **var**: Old way. Function-scoped. Can be re-declared and updated. Gets "hoisted" (moved to top) with a default value of `undefined`.
- **let**: Block-scoped (`{ }`). Can be updated but not re-declared in the same scope.
- **const**: Block-scoped. Cannot be updated or re-declared. Must be given a value when created.

```javascript
var a = 1;   // function scoped
let b = 2;   // block scoped
const c = 3; // block scoped, cannot change
```

---

### Q2. Explain the concept of hoisting in JavaScript.

Hoisting means JavaScript moves variable and function **declarations** to the top of the file (or function) before running the code.

- `var` variables are hoisted and set to `undefined`.
- `let` and `const` are hoisted too, but they stay in a "temporal dead zone" until the line where they are defined (you cannot use them before that line).
- Function declarations are fully hoisted, so you can call them before they appear in the code.

```javascript
console.log(x); // undefined (not an error)
var x = 5;
```

---

### Q3. What are the primitive data types in JavaScript?

Primitive types store simple values, not objects. There are 7:

1. `String` – text, e.g. `"hello"`
2. `Number` – numbers, e.g. `42`
3. `Boolean` – `true` or `false`
4. `Undefined` – a variable declared but not assigned
5. `Null` – an empty/no value
6. `Symbol` – a unique value (used rarely)
7. `BigInt` – for very large numbers

---

### Q4. What is the difference between == and === in JavaScript?

- `==` (loose equality): Compares values **after** converting types if needed.
- `===` (strict equality): Compares both **value and type**, no conversion.

```javascript
5 == "5";   // true  (converts string to number)
5 === "5";  // false (different types)
```

**Tip:** Always prefer `===` to avoid unexpected bugs.

---

### Q5. Explain how closures work in JavaScript with an example.

A closure is when an inner function "remembers" the variables from its outer function, even after the outer function has finished running.

```javascript
function outer() {
  let count = 0;
  function inner() {
    count++;
    return count;
  }
  return inner;
}

const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

Here, `inner()` still has access to `count` because of closure.

---

### Q6. What is the difference between null and undefined?

- **undefined**: A variable has been declared but has no value yet. JavaScript sets this automatically.
- **null**: An "empty" value that a developer sets on purpose to say "no value here."

```javascript
let a;         // undefined
let b = null;  // null (set on purpose)
```

---



### Q7. What are arrow functions and how do they differ from regular functions?

Arrow functions are a shorter way to write functions using `=>`.

```javascript
// Regular function
function add(a, b) {
  return a + b;
}

// Arrow function
const add2 = (a, b) => a + b;
```

Key differences:
- Arrow functions do **not** have their own `this` — they use `this` from the surrounding code.
- Arrow functions cannot be used as constructors (no `new`).
- Shorter syntax, good for small functions like callbacks.

---

### Q8. What is the scope chain in JavaScript?

When JavaScript looks for a variable, it first checks the current scope. If not found, it checks the outer scope, then the next outer scope, and so on until it reaches the global scope. This chain of scopes is called the **scope chain**.

```javascript
let a = "global";
function outer() {
  let b = "outer";
  function inner() {
    console.log(a, b); // finds both through scope chain
  }
  inner();
}
outer();
```

---

### Q9. Explain the concept of the temporal dead zone.

The Temporal Dead Zone (TDZ) is the time between entering a block and the point where a `let` or `const` variable is actually declared. During this time, the variable exists but cannot be accessed.

```javascript
console.log(x); // ReferenceError
let x = 10;
```

`x` is in the TDZ from the start of the block until `let x = 10` runs.

---

### Q10. What is a pure function? Give an example.

A pure function:
1. Always gives the same output for the same input.
2. Does not change (mutate) anything outside itself (no side effects).

```javascript
// Pure function
function add(a, b) {
  return a + b;
}

// Impure function (changes outside variable)
let total = 0;
function addToTotal(x) {
  total += x;
}
```

---



### Q11. What is the difference between function declaration and function expression?

- **Function Declaration**: Defined with the `function` keyword and a name. It is hoisted, so it can be called before it's defined.
- **Function Expression**: A function assigned to a variable. It is NOT hoisted the same way — you must define it before using it.

```javascript
// Declaration
function greet() {
  console.log("Hi");
}

// Expression
const greet2 = function () {
  console.log("Hello");
};
```

---

### Q12. What are default parameters in JavaScript?

Default parameters let you set a default value for a function parameter if no value (or `undefined`) is passed.

```javascript
function greet(name = "Guest") {
  console.log("Hello " + name);
}

greet();        // Hello Guest
greet("Sara");  // Hello Sara
```

---

### Q13. What is the typeof operator and what are its possible return values?

`typeof` tells you the data type of a value. Possible return values:

- `"string"`
- `"number"`
- `"boolean"`
- `"undefined"`
- `"object"` (also returned for `null` — this is a known JS quirk)
- `"function"`
- `"symbol"`
- `"bigint"`

```javascript
typeof "hi";     // "string"
typeof 5;        // "number"
typeof null;     // "object" (quirk!)
typeof undefined;// "undefined"
```

---

### Q14. Explain type coercion in JavaScript with examples.

Type coercion is when JavaScript automatically converts a value from one type to another.

```javascript
"5" + 1;    // "51" (number becomes string)
"5" - 1;    // 4   (string becomes number)
true + 1;   // 2   (true becomes 1)
"5" == 5;   // true (string compared with number)
```

This happens because JavaScript is a "loosely typed" language.

---


### Q15. What is an immediately invoked function expression (IIFE)?

An IIFE is a function that runs immediately after it is defined. It is often used to create a private scope so variables don't leak into the global scope.

```javascript
(function () {
  console.log("I run immediately!");
})();
```

---

## Part 2: Additional 10 Questions (Q16–Q25)

### Q16. What is the "this" keyword in JavaScript?

`this` refers to the object that is currently "calling" or "owning" the function. Its value depends on **how** a function is called, not where it's written.

```javascript
const person = {
  name: "Ana",
  greet() {
    console.log(this.name); // "this" = person
  }
};
person.greet(); // Ana
```

In a regular function, `this` depends on how it's called. In an arrow function, `this` comes from the surrounding (outer) code.

---


### Q17. What is prototypal inheritance?

In JavaScript, objects can inherit properties and methods from other objects through a hidden link called the **prototype**. This is how JavaScript shares behavior between objects without using classes (though classes are also available as easier syntax).

```javascript
const animal = {
  eat() {
    console.log("eating...");
  }
};

const dog = Object.create(animal);
dog.eat(); // "eating..." (inherited from animal)
```

---

### Q18. What is the event loop in JavaScript?

JavaScript runs code in a single thread, one thing at a time. The **event loop** is the mechanism that lets JavaScript handle tasks like timers, promises, and events without blocking the main thread. It constantly checks: "Is the main code finished? If yes, run tasks waiting in the queue (like `setTimeout` callbacks)."

```javascript
console.log("1");
setTimeout(() => console.log("2"), 0);
console.log("3");

// Output: 1, 3, 2
// "2" waits because setTimeout goes to the queue
```

---

