so we need to make it so that a user can make a node, if there are no nodes nearby...

So an AddNode method.

the user needs to be able to select a tile, somehow... I could let the user select a location. - 20, 3 - for example....

since the user is in the center of the screen, we could have the player go into a 'select' mode to select locations near them. gets weird with screen sizes.

Ah. I determined that when the user desires to place a node, they add the coordinates from their current coordinates. I'll have to fetch the local nodes, to make sure that we're not too close to others.

Maybe when the user selects the location, we can fetch nearby terrains, for each terrain type nearby, we can allow custom node types, instead of visually showing the terrain, at least for the prototype.

^^^ This ended up being a sort of breakthrough in my mentality of how I want this to work.

We will use OSM, a super powerful API written with C++, to fetch info about nearby terrain. So when we add a node, we must do these steps.

Take user's long/lat

Check if there are other nodes nearby, if yes, cancel action

Check nearby terrains within a mile or so. If water & land, water is river or lake, then you can do a water node. If forest nearby, forest node, and you get to choose what kind of node it is. So if there's a lake in the forest, you get to choose if it's a forest or water node. 

There's going to be a limited number of nodes initially, let's keep it simple with forest, water, and mine... 

Another question... Should there be 'default' mine types? Such as, no matter the terrains, you CAN place quarry & farm nodes? I could see that. And only if you're near forest / mountain / water can you place the other node types...

So for now, we can continue with just the default node, and begin adding functionality after that.

- [ ] need to test the queries in node.go file!