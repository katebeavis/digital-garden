# Closures

Functions get a new local memory when they are run/executed

They are "functions with memories"

## Functions with memories

- When our functions get called, we create a live store of data (local memory/variable environment/state) for that function's execution context

- When the function finsihes executing, its local memory is deleted (except the returned value)

- But what if our functions could hold onto live data between executions?

- This would let our function definitions have an associated cache/persistent memory

- But it all starts with us **returning a function from another function**

```
 function createFunction() {
   function multiplyBy2(num) {
     return num * 2;
   }
   return multiplyBy2;
 }

 const generatedFunction = createFunction();
 const result = generatedFunction(3); // 6
```

`generatedFunction` is equivilent to `multiplyBy2`

`generatedFunction` no longer has **anything** to do with `createFunction`. `createFunction` is no longer in local memory

`generatedFunction` when called, immediately runs `multiplyBy2` as that is what is in local memory

## Nested function scope

Where you define your functions determines what data it has access to when you call it

```
function outer() {
  let counter = 0;
  function incrementCounter() {
    counter ++
  }
  return incrementCounter;
}

const myNewFunction = outer();
myNewFunction(); // 1
myNewFunction(); // 2
```

`incrementCounter` has access to the `counter` variable as it was defined in the same local memory as `incrementCounter`

When `incrementCounter` is returned as the result of calling `outer()` the function definition isn't the only thing that is returned. It also returns the local memory that it is run in which includes the `counter` variable

### The backpack

- We return `incrementCounter`'s code (function definition) out of outer into global and give it a new name - `mynewFunction`

- We **maintain the bond to outer's live local memory** - it gets 'returned out' attached on the back of `incrementCounter`'s function definition

- So outer's local memory is now stored attached to `myNewFunction` - even though outer's execution context is long gone

- When we run `myNewFunction` in global, it will first look in its own local memory first (as we'd expect), but then in `myNewFunction`'s 'backpack'

## Technical definition

## What can we call this 'backpack'

The local memory that is returned can be referred to as the variable environment. Closed over variable environment. Also known as closure

Lexical/static scoping - where I save my function determines for that rest of the life of that function, what data it will have access to when that function is run

The `backpack` (or 'closure') of live data is attached to `incrementCounter` (then to `myNewFunction`) through a hidden property known as `[[scope]]` which persists when the inner function is returned out

## Practical applications

**Closure gives our functions persistent memories and entirely new toolkit for writing professional code**

**Helper functions:** Everyday professional helper functions like `once` and `memoize`

**Iterators and generators:** Which use lexical scoping and closure to achieve the most contemporafy patterns for handling data in Javascript

**Module pattern:** Preserve state for the life of an application without polluting the global namespace

**Asynchronous Javascipt:** Callbacks and Promises rely on closure to persist state in an asynchronous environment
