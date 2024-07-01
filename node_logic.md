so we need to make it so that a user can make a node, if there are no nodes nearby...

So an AddNode method.

the user needs to be able to select a tile, somehow... I could let the user select a location. - 20, 3 - for example.

since the user is in the center of the screen, we could have the player go into a 'select' mode to select locations near them. gets weird with screen sizes.

Ah. I determined that when the user desires to place a node, they add the coordinates from their current coordinates. I'll have to fetch the local nodes, to make sure that we're not too close to others.

Maybe when the user selects the location, we can fetch nearby terrains, for each terrain type nearby, we can allow custom node types, instead of visually showing the terrain, at least for the prototype.

