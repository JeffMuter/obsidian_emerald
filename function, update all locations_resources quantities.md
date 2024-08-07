this function updates all the user's locations' resource quantities.

1. find all user's locations
2. find all locations workers
3. find all workers tasks
4. get all locations_resources
5. if there's an ongoing task that generates resources:
6. run algo on how much of the quantity has changed since last update




Another issue is just updating one location. let's try to isolate things.

we have a location id to start with.

using that location, we need to update all resources it is going to have. to know that, we need to know the ongoing tasks, and the resources they can potentially update.

once we have the location_resources. let's say we have iron, 
