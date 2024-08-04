when the user is logged out, we dont automatically spend a ton of resources updating their resources all of the time.

we update the resources of their nodes at a crucucial time, like when looking at location details, or on login.

this card is for making these functions run whenever the user logs in.

each location needs to check for the most updated tasks, if those tasks are ongoing, and non resting / traveling, then we check each location's resources, and update them with the algorithm from the last time updated, to now.
