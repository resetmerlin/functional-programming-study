## Declarative vs Imperative Programming Paradigms

One example of these paradigms I talked about at the beginning is object-orientated programming. Another is functional programming.

So what exactly is functional programming?

Functional programming is a sub-paradigm of the Declarative programming paradigm, with its own rules to follow when writing code.

### What is the declarative programming paradigm?

If you're coding in a language that follows the declarative paradigm, you write code that specifies what you want to do, without saying how.

A super simple example of this is either SQL or HTML:

```sql
SELECT * FROM customers
```

```html
<div></div>
```
In the above code examples, you aren't implementing the SELECT or how to render a div. You are just telling the computer what to do, without the how.

From this paradigm, there are sub-paradigms such as Functional programming. More on that below.

### What is the imperative programming paradigm?

If you're coding in a language that follows the imperative/procedural paradigm, you write code that tells how to do something.

For example, if you do something like below:

```javascript
for (let i = 0; i < arr.length; i++) {
     increment += arr[i];
}
```
You are telling the computer exactly what to do. Iterate through the array called arr, and then increment each of the items in the array.

### Declarative vs Imperative programming

You can write JavaScript in the Declarative paradigm or the Imperative paradigm. This is what people mean when they say it's a multi-paradigm language. It's just that functional code follows the Declarative paradigm.

If it helps you remember, an example of a declarative command would be to ask the computer to make you a cup of tea (I don't care how you do it, just bring me some tea).

Whilst imperatively, you would have to say:

- Go to the kitchen.
- If there is a kettle in the room, and it has enough water for a cup of tea, turn on the kettle.
- If there is a kettle in the room, and it doesn't have enough water for a cup of tea, fill the kettle with enough water for a cup of tea, then turn on the kettle.
- And so on


### So what is Functional Programming So what does this mean for functional code?

Because it's a sub-paradigm from the Declarative paradigm, this affects the way you write functional code. It generally leads to less code, because JavaScript already has a lot of the in-built functions you commonly need. This is one reason people like functional code.

It also allows you to abstract away a lot (you don't have to understand in depth how something gets done), you just call a function that does it for you.

And what are the rules that lead to functional code?

Functional programming can be simply explained by following these 2 laws in your code:

1. You architect your software out of pure, isolated functions
2. You avoid mutability and side-effects

## Meaning of Functional Programming?

Functional programming is a paradigm of building computer programs using expressions and functions without mutating state and data.

By respecting these restrictions, functional programming aims to write code that is clearer to understand and more bug resistant. This is achieved by avoiding using flow-control statements (for, while, break, continue, goto) which make the code harder to follow. Also, functional programming requires us to write pure, deterministic functions which are less likely to be buggy.

In this article, we will talk about doing functional programming using JavaScript. We will also explore various JavaScript methods and features that make it possible. In the end, we will explore different concepts associated with functional programming and see why they are so powerful.

Before getting into functional programming, though, one needs to understand the difference between pure and impure functions.

## Pure vs. Impure Functions

Pure functions take some input and give a **fixed output**. Also, they cause no side effects in the outside world.

```javascript
const add = (a, b) => a + b;
```

Here, add is a pure function. This is because, for a fixed value of a and b, the output will always be the same.

```javascript
const SECRET = 42;
const getId = (a) => SECRET * a;
```

getId is not a pure function. The reason being that it uses the global variable SECRET for computing the output. If SECRET were to change, the getId function will return a different value for the same input. Thus, it is not a pure function.

```javascript
let id_count = 0;
const getId = () => ++id_count;
```

![](https://assets.toptal.io/images?url=https%3A%2F%2Fbs-uploads.toptal.io%2Fblackfish-uploads%2Fuploaded_file%2Ffile%2F55111%2Fimage-1569846449711-b437d21679e123bdb3d092ebc64937c4.png)

This is also an impure function, and that too for a couple of reasons—(1) it uses a non-local variable for computing its output, and (2) it creates a side effect in the outside world by modifying a variable in that world.

This can be troublesome if we had to debug this code.

What’s the current value of id_count? Which other functions are modifying id_count? Are there other functions relying on id_count?

Because of these reasons, we only use pure functions in functional programming.

Another benefit of pure functions is that they can be parallelized and memoized. Have a look at the previous two functions. It’s impossible to parallelize or memoize them. This helps in creating performant code.

This can be troublesome if we had to debug this code.

What’s the current value of id_count? Which other functions are modifying id_count? Are there other functions relying on id_count?

Because of these reasons, we only use pure functions in functional programming.

Another benefit of pure functions is that they can be parallelized and memoized. Have a look at the previous two functions. It’s impossible to parallelize or memoize them. This helps in creating performant code.

So far, we have learned that functional programming is dependent on a few rules. They are as follows.

1. Don’t mutate data
2. Use pure functions: fixed output for fixed inputs, and no side effects
3. Use expressions and declarations

When we satisfy these conditions, we can say our code is functional.

## Functional Programming in JavaScript

JavaScript already has some functions that enable functional programming. Example: String.prototype.slice, Array.protoype.filter, Array.prototype.join.

On the other hand, Array.prototype.forEach, Array.prototype.push are impure functions.

One can argue that Array.prototype.forEach is not an impure function by design but think about it—it’s not possible to do anything with it except mutating non-local data or doing side effects. Thus, it’s okay to put it in the category of impure functions.

Also, JavaScript has a const declaration, which is perfect for functional programming since we won’t be mutating any data.

## Pure Functions in JavaScript

Let’s look at some of the pure functions (methods) given by JavaScript.

### Filter

As the name suggests, this filters the array.

```javascript
array.filter(condition);
```

The condition here is a function that gets each item of the array, and it should decide whether to keep the item or not and return the truthy boolean value for that.

```javascript
const filterEven = (x) => x % 2 === 0;
[1, 2, 3].filter(filterEven);
// [2]
```

Notice that filterEven is a pure function. If it had been impure, then it would have made the entire filter call impure.

### Map

map maps each item of array to a function and creates a new array based on the return values of the function calls.

```javascript
array.map(mapper);
```

mapper is a function that takes an item of an array as input and returns the output.

```javascript
const double = (x) => 2 * x;
[1, 2, 3].map(double);
// [2, 4, 6]
```

### Reduce

reduce reduces the array to a single value.

```javascript
array.reduce(reducer);
```

reducer is a function that takes the accumulated value and the next item in the array and returns the new value. It is called like this for all values in the array, one after another.

```javascript
const sum = (accumulatedSum, arrayItem) =>
  accumulatedSum + arrayItem[(1, 2, 3)].reduce(sum);
// 6
```

![](https://assets.toptal.io/images?url=https%3A%2F%2Fbs-uploads.toptal.io%2Fblackfish-uploads%2Fuploaded_file%2Ffile%2F55112%2Fimage-1569846477173-d38787256500eeb7e2464c036280c6e0.png&width=768)

### Concat

concat adds new items to an existing array to create a new array. It’s different from push() in the sense that push() mutates data, which makes it impure.

```javascript
[1, 2].concat([3, 4]);
// [1, 2, 3, 4]
```

You can also do the same using the spread operator.

```javascript
[1, 2, ...[3, 4]];
```

### Object.assign

Object.assign copies values from the provided object to a new object. Since functional programming is predicated on immutable data, we use it to make new objects based on existing objects.

```javascript
const obj = { a: 2 };
const newObj = Object.assign({}, obj);
newObj.a = 3;
obj.a;
```

With the advent of ES6, this can also be done using the spread operator.

```javascript
const newObj = { ...obj };
```

## Creating Your Own Pure Function

We can create our pure function as well. Let’s do one for duplicating a string n number of times.

```javascript
const duplicate = (str, n) => (n < 1 ? "" : str + duplicate(str, n - 1));
```

This function duplicates a string n times and returns a new string.

```javascript
duplicate("hooray!", 3);
// hooray!hooray!hooray!
```

## Higher-order Functions

Higher-order functions are functions that accept a function as an argument and return a function. Often, they are used to add to the functionality of a function.

```javascript
const withLog = (fn) => {
  return (...args) => {
    console.log(`calling ${fn.name}`);
    return fn(...args);
  };
};
```

In the above example, we create a withLog higher-order function that takes a function and returns a function that logs a message before the wrapped function runs.

```javascript
const add = (a, b) => a + b;
const addWithLogging = withLog(add);
addWithLogging(3, 4);
// calling add
// 7
```

withLog HOF can be used with other functions as well and it works without any conflicts or writing extra code. This is the beauty of a HOF.

```javascript
const addWithLogging = withLog(add);
const hype = (s) => s + "!!!";
const hypeWithLogging = withLog(hype);
hypeWithLogging("Sale");
// calling hype
// Sale!!!
```

One can also call it without defining a combining function.

```javascript
withLog(hype)("Sale");
// calling hype
// Sale!!!
```

## Currying

Currying means breaking down a function that takes multiple arguments into one or multiple levels of higher-order functions.

Let’s take the add function.

```javascript
const add = (a, b) => a + b;
```

When we are to curry it, we rewrite it distributing arguments into multiple levels as follows.

```javascript
const add = (a) => {
  return (b) => {
    return a + b;
  };
};
add(3)(4);
// 7
```

The benefit of currying is memoization. We can now memoize certain arguments in a function call so that they can be reused later without duplication and re-computation.

```javascript
// assume getOffsetNumer() call is expensive
const addOffset = add(getOffsetNumber());
addOffset(4);
// 4 + getOffsetNumber()
addOffset(6);
```

This is certainly better than using both arguments everywhere.

```javascript
// (X) DON"T DO THIS
add(4, getOffsetNumber());
add(6, getOffsetNumber());
add(10, getOffsetNumber());
```

We can also reformat our curried function to look succinct. This is because each level of the currying function call is a single line return statement. Therefore, we can use arrow functions in ES6 to refactor it as follows.

```javascript
const add = (a) => (b) => a + b;
```

## Composition

In mathematics, composition is defined as passing the output of one function into input of another so as to create a combined output. The same is possible in functional programming since we are using pure functions.

To show an example, let’s create some functions.

The first function is range, which takes a starting number a and an ending number b and creates an array consisting of numbers from a to b.

```javascript
const range = (a, b) => (a > b ? [] : [a, ...range(a + 1, b)]);
```

Then we have a function multiply that takes an array and multiplies all the numbers in it.

```javascript
const multiply = (arr) => arr.reduce((p, a) => p * a);
```

We will use these functions together to calculate factorial.

```javascript
const factorial = (n) => multiply(range(1, n));
factorial(5);
// 120
factorial(6);
// 720
```

The above function for calculating factorial is similar to f(x) = g(h(x)), thus demonstrating the composition property.


#### Source
- https://www.freecodecamp.org/news/functional-programming-in-javascript/
- https://www.toptal.com/javascript/functional-programming-javascript