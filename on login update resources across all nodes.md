this is an important functionality. we need tasks, resources, and tasks being assigned to worker to all be working to an MVP level for this to get done.

At some point, an API call must be made to every node, to update their quantities of resources. We can make a little function to do this, since we'll do it every few minutes when the user's logged in, and do it at core points. so this can be broken up into several sub tasks. but in general, we need:
1. a function that gets all of the nodes this user has, if those nodes have workers, who are working.
2. get all of the ongoing tasks those workers have.
3. run calc on how many resources should be added from the time of the last update.
4. update the quantities of all locations_resources that need updating.