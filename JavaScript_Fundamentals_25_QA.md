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

