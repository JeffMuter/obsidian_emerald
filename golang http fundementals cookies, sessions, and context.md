

## Golang HTTP Fundementals: Cookies, Sessions, & Context

This all got started when I wanted to render a navbar based on the type of user. Guests are users who aren't signed in, perhaps have no account. Registered users, who are not active-paying members, and members.

Non-paying members & members are fairly easy to distinguish. Between those and guests? Oh, and how do we do this so we're not querying the database multiple times whenever a handler is called?

My first instinct was to use sessions, and store those sessions in the database. Then, however, I realized that meant reading from the database, even when the user is going to the homepage. That felt very wrong in my head.

Next, I tried managing this via cookies. Do we set these in every handler? Or every render function? I decided to do it where I handle all of my cookie management, in the middleware. Obviously this was a fairly dumb decision, in retrospect. Not every route is protected...

Well the one time I KNOW I'll need to know their user-type is when we render a full new page, so we'll shove it in the full-page renderer func, right?

Wrong. It requires reading from the database every time... Again.

What the hell? Why is this so nonsensically complex? This is one of my first, and certainly most complex Golang HTTP Web Servers I've written from scratch on my own. So this HAS to be a skill issue. Which means I can fix it by exploring some.

Finally, so progress. I was thinking about this problem as an OR solution. Sessions OR cookies. Cookies OR context. I needed to sit down and look at these three systems, cookies, sessions, and context. Knowing how each are intended to be used, what they're good at, what they're bad at, and then use them each for what they're good for.

Cookies: Storing randomized information you don't mind the user manipulating / seeing.

There's a difference here between random and unrandomized data. I don't mind a user seeing a randomized token, because a randomized token can't be abused over time. So if we assigned a randomized token, that expires in 24 hours, they can't re-use that token indefinitely. But you can't just write their user-status here, such as "member", or even a randomized key that represents a member, if it represents a member indefinitely, in a way that doesn't expire. So great, we can send the user a timed cookie with an expiration








