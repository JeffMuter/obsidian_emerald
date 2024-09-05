for some reason, getting worker details isn't working for hozashi at position 0

hozashi is the only worker appearing bevause the qery only gets workers who are working. hes the only one in the db who's 'working' maybe we should just make a func to determine if working...

actually, this is caused because no other worker but hozashi has been assigned to do anything, until they are,

found the issue... cities have no task types because they were going to be a kind of crafting hub.