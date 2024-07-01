we want to use the current location of the user to add a location to the database.
in pseudocode
func AddNode(user user.User) err {
	userLat := user.Latitude
	userLong := user.Longitude
	// get other nearby nodes
	if nodes nearby {
		return error
	} else {
		db := database.OpenDatabase()
		defer db.Close()

		query := 
		// execute query
		return id, nil
	}



}

