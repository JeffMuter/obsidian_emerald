

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

If we can't store info needed within the cookie, how can we create server-side information about the user?

Context: Single-request information

Once we have an http.Request, we can apply a 'context' from go's context package to that request. Then, as the request navigates through the server, the context has specialized information. As we may not want to begin passing a bunch of new values as required parameters, requiring us to create an ever-growing list of required information just to render a page. The context package has a lot more to offer, please look into it but other features have little to do with this problem. However, some information, such as what 'type' of user we have, is important. Is their subscription active, for example. Keep in mind, when it comes to an active subscription, this requires a read from the database. We should keep in mind whether this is tolerable. On a large system with tens of thousands of requests / minute, this may not scale. So there's a final solution for this.


Session: Server-side reserved space to track data of active users.

For My own purposes, I could store this information in one of two main ways, depending on the number of users I expect to be active... Storing rows of users in a table, fields being information that could be relevant. Problem here is that may be a lot of information to check for at any given time. I also am not a huge fan of querying a database, or at least limiting it as much as possible. Since we always check the db on each request, I'd prefer the second option I'll describe next. 

Storing Sessions as In-Memory Data:

In Go, we can make a neat little struct called a Session. A session is stored in a map, using user cookies as their key. If the user doesn't have a value cookie value in their request, then something has gone wrong in their authentication, and it's a very quick rejection even if they have an invalid cookie as part of a map. It's a quick 1:1 validation.

In the Session struct, add whatever fields you need, store them in local memory. Of course, for each you may have many irrelevant, uninitiated values, but as long as you have enough memory, or not enough users, this shouldn't be a problem. For my purposes, I'm not desperately worried about maxing out my RAM on these session structs. However, if it ever did become a problem, I may require the database option, and only keep recent users in this struct, recycling old ones.

### Conclusion:

HTTP servers are hard. I had been so used to only worrying about the front end, and application development, that I hadn't continued to have time to get painfully deep into the weeds on constructing the foundation of an http server project with a db. So these lessons are incredibly powerful, and just being conceptually competent on these concepts feels like implementing solutions becomes a lot easier. Before, I had always tried to solve problems with cookies, middleware, and the database. But my solutions were probably overly convoluted because I tried to conform my solutions to a limited understanding of the best tools available. It's a good lesson, once again, on the importance of being willing to open google and go deep onto hard topics.

Hopefully anyone can benefit from my mistakes, and from my pain, learn to be a tiny bit better and save yourself some pain.






