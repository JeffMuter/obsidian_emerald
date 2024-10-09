issue I need to troubleshoot about more and more files needing an extra prompt when opening. 

this is routine with $MYVIMRC... Need to figure out how this interraction works.

when I need to use wsl --shutdown , there's a chance that a file will go into recovery mode for neovim. If I have to recover more than once, then the file isn't deleting itself, it's better to yank the file contents, delete the copies version by pressing 'D' on opening the file, paste in the changes you see.