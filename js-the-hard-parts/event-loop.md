# Event loop

The event loop is responsible for executing code, collecting and processing events and executing queued sub-tasks (callback/message queue)

The event loop runs continuously, checking if the call stack has anything to execute. If not, it checks the message queue. If there is a message, then it pops it off and pushes it onto the call stack
