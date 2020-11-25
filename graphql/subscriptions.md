# Subscriptions

In addition to queries and mutations, GraphQL supports a third operation type: subscriptions.

Like queries, subscriptions enable you to fetch data. Unlike queries, subscriptions maintain an active connection to your GraphQL server (most commonly via WebSocket). This enables your server to push updates to the subscription's result over time.

Subscriptions are useful for notifying your client in real time about changes to back-end data, such as the creation of a new object or updates to an important field.

## When to use subscriptions

Usually polling or refetching will do the job but there are some cases for using them:

- Small, incremental changes to large objects. Repeatedly polling for a large object is expensive, especially when most of the object's fields rarely change. Instead, you can fetch the object's initial state with a query, and your server can proactively push updates to individual fields as they occur.

- Low-latency, real-time updates. For example, a chat application's client wants to receive new messages as soon as they're available.

A real world example is liking of posts in Facebook. This is an example of a small, incremental change. Adding a subscription allows the client to get pushed data anytime someone likes or unlikes a post

"Subscriptions are a way to push data from the server to the clients that choose to listen to real-time messages from the server. Subscriptions are similar to queries in that they specify a set of fields to be delivered to the client, but instead of immediately returning a single answer, a result is sent every time a particular event happens on the server without the client needing to resend that request."
