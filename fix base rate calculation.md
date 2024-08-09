2 issues here. in the app, the base rate is always 0. Which cannot continue.

when creating a new locations_resources, we fill in the 0 manually. We need some way to calculate this that makes sense.

When making a location, we set a type of location. Each location has tasks, and those tasks yield different resources. We need to have a task_resource have the rate, I think

Now task_types_resources contains a col for base_rate.

we need to retrieve the base rate from the db when we calculate the