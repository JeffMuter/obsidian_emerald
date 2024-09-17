theres a race condition at the end of mainMenu func. Need to learn how to stop that.

ive restructured main menu in a bad way. What it really needs is for main menu to return a value that we then do a handleRoomConnect or some function outside of main menu, in my opinion. Just need more isolation of concerns. 
Don't forget to add concurrent behavior and handle race cond.

