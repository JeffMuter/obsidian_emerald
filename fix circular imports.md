Before this point, I had considered the tasks package, as just a file for any funcs related to tasks

I hadn't realized, complex functions like: setWorkerToNewTask(worker workers.Worker) error {} would be so problematic. What's effectively happening, is that im importing worker, and location packages for this function.

In locations package. I have another func: updateLocationQuantities, which gets ongoing tasks, 

                      tasks
	            //            ^
	        //                    \\
	    //                             \\
	\/                                      \\
	workers =============================>  locations

As this poorly made diagram shows, as they depend on one another, it creates a loop. this isn't allowed in go. I don't fully know why, but it doesn't matter for this. It's a rule I have to always. follow. So if functions depend deeply on one another, then now, these packages become CRUD packages, meant to handle db operations related to their type.

When I make utility functions, using these types, that needs its own package. But thinking of the right package to make for these is interesting. I don't want to make a 10000 line file called services.go for all the different main game logic code. do i?
