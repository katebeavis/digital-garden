# 100DaysOfCode Log - Round 1

## Day 3

### 06/01/20

## Only allows authenticated users to access signed in pages [react-graphql-store](https://github.com/katebeavis/react-graphql-shop/pull/28)

### Create an authenticated wrapper

- Create an simple authenticated wrapper which checks if a user is signed in or not using the `useAuth` hook and renders either the sign in components or the children it is passed.

### useAuth hook

As not much coding happened today (first day back at work) I will go over the `useAuth` custom hook.

> A custom Hook is a JavaScript function whose name starts with ”use” and that may call other Hooks.

The `useAuth` hook is relatively simple as far as hooks go - it calls another hook, in this case Apollo's `useQuery` and then returns an array of `loading` and `error` states and `data`.

```
import { useQuery } from 'react-apollo';

import { CURRENT_USER_QUERY } from '../queries/queries';

const useAuth = () => {
  const { loading, error, data } = useQuery(CURRENT_USER_QUERY);
  return [loading, error, data];
};

export default useAuth;
```

These can then be destructured in the component that is using the `useAuth` hook.

```
const [loading, error, data] = useAuth();
```

### Notes

Ideally refactor to use authenticated routes as wrapping every single signed in component in the authentication wrapper will start to get tedious if the application grows.

## Day 2

### 05/01/20

## Sending email with nodemailer [react-graphql-store](https://github.com/katebeavis/react-graphql-shop/pull/24)

### Set up mailtrap

- Set up [mailtrap](https://mailtrap.io) to receive emails and set `host`, `post`, `username` and `password` as env variables

### Set up nodemailer

- Create a Nodemailer transporter using SMTP
- Set up email template

```
# mail.js
const nodemailer = require('nodemailer');

export const transporter = nodemailer.createTransport({
  host: process.env.MAIL_HOST,
  port: process.env.MAIL_PORT,
  auth: {
    user: process.env.MAIL_USER,
    pass: process.env.MAIL_PASS
  }
});

export const emailTemplate = text =>
  `<div>
    <p>${text}</p>
  </div>`;
```

### Send email

- Send email using the `sendMail` method of the transporter

```
import { transporter, emailTemplate } from './mail';

server.post('/send-mail', (req, res) => {
    try {
        await transport.sendMail({
            from: 'anEmail@email.com',
            to: 'anotherEmail@email.com',
            subject: 'An email',
            html: emailTemplate(
            'Here is some text'
            )
        });
        res.send(200);
    } catch (error) {
        throw new Error(`An email occurred ${error}`);
    }
});
```

### Notes

Use [mjml](https://mjml.io) for sophisticated templates.

## Day 1

### 04/01/20

## Resetting password with JWT in Node.js [react-graphql-store](https://github.com/katebeavis/react-graphql-shop/pull/22)

### Generate reset token

- Create a reset token using `randomBytes` from Node.js `crypto` module and set expiry (an hour)

```
const resetToken = await randomBytes(20).toString('hex');
const resetTokenExpiry = Date.now() + 3600000;
```

- Save these to `resetToken` and `resetTokenExpiry` column respectively in `user` table in db

### Email is sent to user with token

- User is sent email which contains a url yoursite.com/resetPasswordPage?resetToken=resetToken
- User is redirected to a page where they submit a new password

### Reset password

- Find user who has that reset token and throw an error if a user is not found or the token is expired
- Hash the new password
- Save the password to the db and set the `resetToken` and `resetTokenExpiry` to null

### Notes

Need to check the security of this method. An alternative method is to use a JWT token.

- User enters email into password reset form and the backend finds that user and creates a JWT token with that user's id in it
- An email is sent to that user with a url containing the JWT token
- User submits new password as above and token is decoded to get the user and password is hashed
- Need to consider expiry date of JWT token
