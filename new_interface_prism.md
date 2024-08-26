[[blog_ideas]]

this is a blog about how I hadn't realized I was thinking without interfaces.

Earlier last week someone mentioned that if you were 6 months into learning Go, and hadn't actually implemented an interface, then it was worth a very stern talking to, as my grandfather would say (haha).

It is roughly 9-10 months since I started using Go, and I felt a little abashed to be confronted with the reality that I had honestly forgot about interfaces. Most of my projects have probably been too small to have a terribly great need for them. 

I did some Googling, some GPTing too, and felt like as my game grew, especially past the MVP phase, that interfaces would become more essential, but at the moment, there wasn't a great need for them.

However, I was proven wrong almost instantly. As I went back to my project, I was dabbling in a 'menu' system, that often involves printing rows of data about the user's inventory. Sometimes the detail is high, sometimes it's low. However, it insteantly caught my attention from my recent queries about interfaces. I realized I had the opportunity to develop a kind of interface to print out the details of each kind of type. Details on a location, details on a worker, inventory, you name it. So below I'll show you the before & after code.

// ReadNumericSelection() is a func that takes in a max num, like 3, and tha assumption is you've already printed a list of something, and you're passing in the max # the user could select. Here we read the input of the user, check, and convert that string to an int, so you can option[result] to find the user's selection.

util.go : used to store misc functions that don't have a great package for them yet.
'''
func ReadNumericSelection(options int) (int, error) {
	input, err := ReadCommandInput()
	if err != nil {
		return -1, err
	}
	// convert input to int
	intInput, err := strconv.ParseInt(input, 10, 64)
	if err != nil {
		return -1, err
	}

	// make sure input isn't out of bounds.
	if intInput < 0 || intInput >= int64(options) {
		return -1, fmt.Errorf("input was too low or too high")
	}

	return int(intInput), nil
}
'''

'''
type Printable interface {
	String() string
 }
'''