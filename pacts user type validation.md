This is a log of the issue where we needed to know the user type (guest || registered || member), and we had a hell of a time with it.

In retrospect, and summary, the issue was rooted in a lack of understanding of how to use a few concepts proficiently at a high level. They were all fairly fuzzy in my mind, which led to a dependency on AI chatbots guiding me through the problem. Leading to more junk code, problems across the whole application.

The concepts were:

- cookies
- context package
- session management
- jwt

### Problem Abstract:

Users may be in one of three types: 
- not signed in
- signed in & inactive membership
- signed in & active membership

In this program, each type of user needs a different type of navbar. Simple, right?

#### Try via Cookies & Middleware
My instinct was to store this in cookies. If they have a valid jwt, we know they're one of the signed-in types, so we could jump into the middleware, check their cookie, and store a cookie, check their account type (member or not), either or, send that as a cookie?

Nope. Can't do that. The user can manipulate the cookie. The only reason this works for JWT is that the token is time-restricted and randomized.

I was also very hung up on that unprotected routes wouldn't do this check, and the user may keep their navbar!

Well, this is taken care of by the middleware now. If the user's jwt is wrong or expired, we'll perform a full page reload to the login page. However, this also wasn't a big deal. Even if the user tries to perform some kind of route, as long as the middleware doesn't allow it to occur, we won't have an issue.



