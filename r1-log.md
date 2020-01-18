# 100DaysOfCode Log - Round 1

## Day 5

### 18/01/20

## Learn how to learn course

### The importance of sleep

> You might be surprised to learn that just plain being awake creates toxic products in your brain. How does the brain get rid of these poisons? Turns out that when you sleep, your brain cells shrink. This causes an increase in the space between your brain cells. It's like unblocking a stream. Fluid can flow past these cells and wash the toxins out. So, sleep which can sometimes seem like such a waste of time is actually your brain's way of keeping itself clean and healthy.

> It seems that during sleep, your brain tidies up ideas and concepts you're thinking about and learning. It erases the less important parts of memories and simultaneously strengthens areas that you need or want to remember.

Sleep is a very important part of memory and learning.

By getting a good nights sleep, you enhance your chances of solidifing concepts you have been studying.

### Introduction to memory

> Working memory is the part of memory that has to do with what you're immediately and consciously processing in your mind.

> Researchers used to think that our working memory could hold around seven items or chunks, but now it's widely believed that the working memory holds only about four chunks of information.

> You often need to keep repeating what you're trying to work with so it stays in your working memory. For example, you'll sometimes repeat a phone number to yourself until you have a chance to write it down. Repetitions needed so that your metabolic vampires that is natural dissipating processes don't suck those memories away.

> The other form of memory, long term memory is wide a storage warehouse, and just like a warehouse, it's distributed over a big area. Different kinds of long-term memories are stored in different regions of the brain. Research has shown that when you first try to put an item of information in long-term memory, you need to revisit it at least a few times to increase the chances that you'll be able to find it later when you might need it.

> So it can be difficult for you to find the information you need unless you practice and repeat at least a few times.

> Long-term memory is important because it's where you store fundamental concepts and techniques that are often involved in whatever you're learning about. When you encounter something new, you often use your working memory to handle it. If you want to move that information into your long-term memory, it often takes time and practice.

> To help with this process, use a technique called spaced repetition. This technique involves repeating what you're trying to retain, but what you want to do is a space this repetition out.

> Extending your practice over several days does make a difference. Research has shown that if you try to glue things into your memory by repeating something 20 times in one evening for example, it won't stick nearly as well as if you practice it the same number of times over several days. This is like building the brick wall we saw earlier, if you don't leave time for the mortar to dry, that is time for the synoptic connections to form and strengthen, you won't have a very good structure.

There are two types of memory - working & long term.

Working memory can hold only about four chunks of information & can be compared to an inefficient blackboard. You need to keep on repeating what you're trying to remember. This explains why it is easy to get 'lost' when following code through multiple files - your chunks are full.

Long term memory is where you store fundamental concepts & techniques. Moving something to long term memory often takes time and practice. You need to revisit the memory at least a few times to be able to easily recall it. Repetition helps with this but it's best to space it out.

It's best to space the repetition out rather than cramming it into one day. Practice it the same number of times over several days.

### Practice makes perfect

> In the greater scheme of all the different careers and disciplines that people can pursue, why are those involving math and science, sometimes, a bit more challenging? We think it may be related, at least in part, to the abstract nature of the ideas.

> This means it's important to practice with ideas and concepts your learning in math and science, just like anything else you're learning. to help enhance and strengthen the neural connection your making during the learning process. You can see on your left here the symbolic representation of a thought pattern. Neurons become linked together through repeated use. The more abstract something is, the more important it is to practice in order to bring those ideas into reality for you. Even if the ideas you're dealing with are abstract, the neural thought patterns you are creating are real and concrete. At least they are if you build and strengthen them through practice.

> When you first begin to understand something, for example, how to solve a problem, the neural pattern from is there, but very weak. Kind of like the faint pattern at the top of our paintball machine analogy here. When you solve the problem again fresh from the start, without looking at the solution. You, if you begin deepening that neuron pattern, kind of like the darker pattern you see here in the middle.

> Practice makes permanent.

> When you're learning, what you want to do is study something. Study it hard by focusing intently. Then take a break or at least change your focus to something different for awhile. During this time of seeming relaxation, your brain's diffuse mode has a chance to work away in the background and help you out with your conceptual understanding. Your, your neural mortar in some sense has a chance to dry.

Practice makes perfect. When you first learn something you create a neural pattern but it's very weak. The more you solve the problem again from the start, the more deep the neural pattern becomes. This is why when learning to code, we are told to delete the code and start over again.

A good way to learn is to study it hard by focusing intently and then take a break. Your brain's diffuse mode has a chance to help you understand with conceptual understanding. A good way of doing this is by using the Pomodoro technique.

## Day 4

### 16/01/20

## Learn how to learn course

### Focused and Diffuse Modes

> Researchers have found that we have two fundamentally different modes of thinking. Here, I'll call them the Focused and the Diffuse modes.

> We're familiar with focusing. It's when you concentrate intently on something you're trying to learn or to understand. But we're not so familiar with diffuse thinking. Turns out that this more relaxed thinking style is related to a set of neural resting states.

> To get to this new thought pattern, you need a different way of thinking. And that's represented here, by the diffuse mode.

> In this diffuse mode of thinking, you can look at things broadly from a very different, big-picture perspective. You can make new neural connections traveling along new pathways. You can't focus in as tightly as you often need to, to finalize any kind of problem solving. Or understand the finest aspects of a concept. But you can at least get to the initial place you need to be in to home in on a solution.

> Usually, diffuse thinking happens as you do other things. That’s why taking a shower or going for a run to take a break from studying can actually lead to an important breakthrough. While your conscious mind is relaxed, your brain is able to form a creative solution to a problem or finally link ideas that had been eluding you.

https://www.brainscape.com/blog/2016/08/better-learning-focused-vs-diffuse-thinking/

Focused thinking is when all your attention is on the matter at hand and there are no distractions. Diffuse thinking is when you are not 100% focused and let your mind wander - an explanation for the 'shower epiphany'.

## Day 3

### 06/01/20

## Only allow authenticated users to access signed in pages [react-graphql-store](https://github.com/katebeavis/react-graphql-shop/pull/28)

### Create an authenticated wrapper

- Create a simple authenticated wrapper which checks if a user is signed in or not using the `useAuth` hook and render either the sign in component or the children it is passed.

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
