# Control flow

## [Previous (loops)](./loops.md)

## Purpose

We can store data, we can write functions, and we can execute code multiple times. But what if we want to execute different code depending on some condition? That's where control flow statements come in.

## If/else

The most common way for a language to let a programmer do different things based on some value is with the if/else construction.

Say we want to write a function that divides 2 numbers. However, as we all know, dividing anything by 0 is undefined <sup>[1](#myfootnote1)</sup>. While a good implementation of the division operator would stop any programmer from dividing by 0 by throwing an error, we'll just treat any division by 0 as 0 for the sake of lazin- I mean, the educational excuse to use if/else.

### Python

```python
def divide(a, b):
    if b == 0:
        return 0
    else:
        return a / b

print(divide(4, 4))
print(divide(4, 0))
```

### JavaScript

```js
function divide(a, b) {
    if (b === 0) {
        return 0;
    } else {
        return a / b;
    }
}
console.log(divide(4, 4));
console.log(divide(4, 0));
```

### Dart

```dart
double divide(int a, int b) {
    if (b == 0) {
        return 0;
    } else {
        return a / b;
    }
}
void main() {
    print(divide(4, 4));
    print(divide(4, 0));
}
```

The if/else construction is basically the same across all of these languages save for whitespace versus curly braces. The first condition checked is contained in the line containing `if`. In the above cases, we check for whether `b` is 0. If this condition is false, then we execute the code in the `else` block.

Notice that in JavaScript, we use the `===` operator instead of `==`. This is a JavaScript quirk where `===` checks for equality of references in memory, while `==` allows for [type coercion](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion). Check [this](https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons) post for a detailed explanation. In nearly every case, you'll want to use `===`.

## Else if

But what if we wanted to check multiple conditions? That is, after the initial condition in the `if` block fails, what if we want to check another condition?

Let's say a value `mystery` can either be 0, 1, or 2, and we want to do something different for each number. We can use an `else if` block in addition to the `if` and `else` blocks.

### Python

```python
mystery = ... # some code to get the mystery number
if mystery == 0:
    print('wow, 0')
elif mystery == 1:
    print('wow, 1')
else:
    print('wow, 2')
```

### JavaScript

```js
const mystery = ... // some code to get the mystery number
if (mystery === 0) {
    console.log('wow, 0');
} else if (mystery === 1) {
    console.log('wow, 1');
} else {
    console.log('wow, 2');
}
```

### Dart

```dart
void main() {
    int mystery = ... // some code to get the mystery number
    if (mystery == 0) {
        print('wow, 0');
    } else if (mystery == 1) {
        print('wow, 1');
    } else {
        print('wow, 2');
    }
}
```

`else if` is pretty straightforward. If the initial condition in the `if` block fails, the computer will check the condition in the following `else if` block. If that block fails, it will followingly check each successive `else if` condition afterwards. If none of the conditions are true, it executes the `else` block.

Strictly speaking, you don't need the `else if` nor the `else` blocks; leaving them out will not result in a syntax error. In fact, most of the time, you will not need `else`. In our division examples, notice that after we return from a function, we never reach the rest of the function's code. So, to use JavaScript as an example, we can simplify our code:

```js
function divide(a, b) {
    if (b === 0) {
        return 0;
    }
    return a / b;
}
```

The `else` was redundant, and now our code looks much prettier. Similarly, you don't technically need the `else` statements in the `mystery` examples.

## Ternary operators

Sometimes, it's cumbersome to write if and else and all that junk. When checking for short conditions, it's often pithier to use a **ternary operator**.

### Python

```python
four_is_bigger = 4 < 5
b = 1 if four_is_bigger else 0
```

Here, instead of breaking out an if/else block, we set the value of `b` in one line. Since `four_is_bigger` is `True`, then `b` takes on the value 1. If it were not, then `b` would be 0.

### JavaScript

```js
const four_is_bigger = 4 < 5;
const b = four_is_bigger ? 1 : 0;
```

JavaScript is different. The condition comes before the first value this time, but the logic is the same. `b` will be 1.

### Dart

```dart
void main() {
    bool four_is_bigger = 4 < 5;
    bool b = four_is_bigger ? 1 : 0;
}
```

The Dart implementation is basically the same as that of JS.

## Tips

Sometimes, you'll find yourself making a lot of nested checks. For example, in Python

```python
if check_A:
    if check_B:
        # do some stuff
        return True
    return True
else:
    return False
```

This can be simplified to

```python
if not check_A or not check_B:
    return False
# do some stuff
return True
```

Sometimes, it's much cleaner to check for fail/escape cases and then return from the function before carrying on with the rest of it. This keeps your code flat, reducing nesting, and makes it much easier to reason about (and read). These checks for fail cases are called [guard clauses](https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html).

Another tip is that the order of conditions in your `if` and `else if` statements matters, particularly when their conditions are not mutually exclusive. That is, be aware of how you order your conditions if multiple conditions can be true at the same time. You'll see why this is important in the exercises.

## Exercises

1. Solve [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/) (you can write it yourself or use Leetcode's boilerplate).
2. Write a program that determines whether integers `a`, `b` are [coprime](https://en.wikipedia.org/wiki/Coprime_integers). Be sure to use loops.

## [Next (essential data structures)](./ds.md)

<a name="myfootnote1">1</a>: However, there are [zero divisors](https://en.wikipedia.org/wiki/Zero_divisor#:~:text=In%20abstract%20algebra%2C%20an%20element,to%20ax%20is%20not%20injective.&text=An%20element%20that%20is%20a,simply%20called%20a%20zero%20divisor.) in certain [rings](https://en.wikipedia.org/wiki/Ring_(mathematics)). If you're interested in cryptography, it'd be useful to get to know some abstract algebra.
