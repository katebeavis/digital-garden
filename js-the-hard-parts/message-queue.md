# Web api rules

## Callback/message queue

User initiated events, asynchronous code and events that are handled by the web browser api are added to the callback/message queue before being added to the call stack

The event loops gives priority to those items in the call stack. It processes everything in the call stack and in global and when there is no synchronous code left to be run, it moves onto the message queue

| Call stack   |
| ------------ |
|              |
|              |
|              |
| printHello() |

global()
