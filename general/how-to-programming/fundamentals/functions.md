# Functions

## [Previous (variables)](./variables.md)

## Purpose

If a program is just a bunch of procedures acting on data, we'd better have a way to act on that data. A function is just a piece of code that accepts some data, processes it, and produces output (or doesn't, as we'll see). If variables are nouns, functions are our verbs.

To define a function, we must **declare** a function. To use a function, we must **call** or **invoke** the function.

## Arguments

A function's argument is simply whatever you feed into the function. There is no limit to how many arguments a function can take.

## Types

Like variables, writing a proper function involves types, whether they're visible to the progrmamer or not (recall dynamically vs statically typed languages). Under the hood, every function has a **return type**, and all of a function's arguments are also typed. A function's arguments are typed in the same sense a variable is typed; it specifies what data the function can take in. A return type on the other hand is what type of data the function will **return**, or output. The output of a function can then be used in an assignment, for instance.

## Syntax

Here's how you declare and call a function.

### Python

```python
def fn(a, b):          # declaration
    return a + b

output = fn(4, 7)      # function call
print(output)
```

To declare a function in Python, the general syntax is `def <function name>(<arguments>):` followed by a newline, tab, and the rest of the function. Notice that in Python, whitespace matters. You need that tab below the line `def fn(a):`.

### JavaScript

```javascript
function fn(a, b) {        // declaration
    return a + b;
}

let output = fn(4, 7);     // call
console.log(output);
```

To declare a function in JavaScript, use the scheme `function <function name>(<arguments>)` followed by curly braces with the function body inside. Notice that in JavaScript, instead of whitespace, we have curly braces. You need those curly braces after each function declaration.

### Dart

```dart
int fn(int a, int b) {             // declaration
    return a + b;
}

void main() {
    int output = fn(4, 7);     // call
    print(output);
}
```

Declaring functions is more tricky in Dart. Since functions must have a type, the return type of the function must be declared before the name of the function and its argument list. Additionally, each argument must be typed.

## Scope

**Scope** describes the variables and data that a function or code block is allowed to manipulate. Functions have their own separate scope from all other code blocks, functions, and programs. This means variables defined in the argument list of a function and in a function body are totally independent of the variables used anywhere else. Using JavaScript as an example,

```js
function multiply(a, b) {
    const c = a * b;
    return c;
}

const a = 3;
const b = 4;
const c = a * b;

const multiplyOutput = multiply(18, 3);

console.log(multiplyOutput);
console.log(c);
```

`multiplyOutput` is 54, but `c` is 12. This is because the variables `a, b, c` in `multiply` are in a different scope from the rest of the program. Keep this in mind.

## [Next (loops)](./loops.md)

---

1. [Anatomy of a program](./fundamentals/anatomy-of-a-program.md)
2. [Variables](./fundamentals/variables.md)
3. [Functions](./fundamentals/functions.md)
4. [Loops](./fundamentals/loops.md)
5. [Control flow](./fundamentals/control-flow.md)
6. [Essential data structures](./fundamentals/ds.md)
7. [Sharing code](./fundamentals/sharing-code.md)
8. [Classes](./fundamentals/classes.md)
9. [More functions](./fundamentals/more-functions.md)