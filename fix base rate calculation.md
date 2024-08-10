2 issues here. in the app, the base rate is always 0. Which cannot continue.

when creating a new locations_resources, we fill in the 0 manually. We need some way to calculate this that makes sense.

When making a location, we set a type of location. Each location has tasks, and those tasks yield different resources. We need to have a task_resource have the rate, I think

Now task_types_resources contains a col for base_rate.

we need to retrieve the base rate from the db when we calculate the...

this whole thing needs rethought.

k. So we got location id.

we need to get a list of ongoing Tasks, from them, we need a map of all possible resources, and their rates. don't think we need more yet. This list of tasks is

1:
in tasks, take a location id, and make a func that returns
map{resourceName}Rate for each given task
potentialResources = map{resouceName string}rate float64

2: 
get slice of []resource. We check locations_resources to get the existingResources
existingResources = []resource

3:
figure out which resources don't exist yet. so we can add them to db???
simply, cycle through the map of 