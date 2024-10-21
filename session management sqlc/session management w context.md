session

so, our current solution looks as follows

user queries api.

Api sends almost all req to middleware.

middleware checks users cookies

if cookie for 'bearer' exists, check to see if jwt is valid

if it is, query this user on the db.

if this user is a member, apply 'member' to context of this single req.

else, apply 'registered' to context.

if not a registered user, apply 'guest' to context, and send them to login page.