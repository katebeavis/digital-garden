# JS principles

## Thread of execution

When Javascript code runs, it goes through the code line-by-line and runs/executes each line. This is know as the thread of execution.

It saves data like strings and arrays so we can use that data later in **memory**.

The identifer (name of the variable) is saved in memory along with what data it points to.

There is only one thread of execution happening at a time.

## Execution context

An abstract concept of an environment where JS code is evaluated and executed.

### Global execution context

The overall program that is running. Any code that is not inside any function is in the global execution context.

It does two things: it creates a global object which is a window object and sets the value of `this` to the global object. There can only be one global execution context in a program.

### Functional execution context

Everytime a function is invoked, a brand new execution context is created for that function. Each function has its own execution context, but it's created when the function is invoked or called.

It has two parts: the local memory (local as it's only avaialble in the scope of the function) and the thread of execution.

## Call stack

The call stack keeps track of what is running.

When you run a function, it is added to the call stack.

When the function has finished running, it is removed from the call stack.

Whatever is on top of the call stack is what is currently running.

The global execution context is always at the bottom of the call stack.
