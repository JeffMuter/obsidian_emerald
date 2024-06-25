[[prism]]

one rough point of object painting to screen is that we completely repaint the entire obj art. maybe we won't care, however, we could simplify this process by sorting the obj slice in its current reverse, then add a condition for each char paint, that says don't paint if the space is occupied by game object char.