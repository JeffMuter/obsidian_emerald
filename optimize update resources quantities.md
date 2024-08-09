when we have multiple possible resources in the slice like [type1, type2, type3], we are updating the type1 row twice. Need to clean this up. There are half a dozen decently sized functions happening here as well, and they could seriously be split up, or more comments added to help me. Because this was rough.

my thought for the multi-resources is to use a slice.

There's also a map, that I basically change the definition of what the value means as I reassign it, from a # of minutes, to the # of the resource quantity. this is really unclear. should be redone.
