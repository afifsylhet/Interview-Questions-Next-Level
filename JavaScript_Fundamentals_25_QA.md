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



