# Call stack

A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc

- When a script calls a function, the interpreter adds it to the call stack and then runs that function

- Any functions that are called by that function are added to the call stack further up, and run where their calls are reached

- When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing

- If the stack takes up more space than it had assigned to it, it results in a "stack overflow" error

The items in a call stack are run on a LIFO (last in, first out) basis
