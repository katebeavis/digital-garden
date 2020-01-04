# 100DaysOfCode Log - Round 1

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
