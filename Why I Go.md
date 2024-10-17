## Why I Go
###### A Bad Explanation of How I Fell in Love With Go


Go is simple: use the gopher as a symbolic explanation of Go's focus on simplicity

What does simplicity mean? Simple for the developer? Simple for the compiler?

What does simple code look like? 

---
#### comments are pseudocode for simplicity

Error type as a value that can be returned in functions:
```

package main

import ( // this loads into memory whatever packages (code) this file needs
	"projectname/database" // this will load our database, and allow for queries
	"fmt" // this is for formatting text...
)

func doSumthin(userId int) ([]int, error) {
	var friendsIds []int
	
	// query the database for a list of id's of this user's friends
	friendsIds, err := query.GetIdsOfFriendsByUserId
	
	if err != nil { // if this is true, we know something went wrong
		// let's return the error, so we know what it is 
		// in the function that calls it!
		return friendsIds, err
	} else {
		// if err is nil, then the query was successful, let's return the id's
		// and nil
		return friendsIds, nil
	}
}

func main() {
	// let's use the function to print the user the list of ids of their friends
	friendsIds, err := doSumthin(1)
	if err != nil {
		// fmt.Printf formats a print statement
		fmt.Printf("an error code appeared while fetching friends id's: %v" , err)
		return
	} else if len(friendsIds == 0) {
			fmt.Println("you have no friends... :( ")
	} else { // then let's print a list of friends! And make it look pretty.
		for i := range friendsIds {
			fmt.Printf("Friend %d: %d\n", i, friendsIds[i])
		}
	}
}

```


---
## Go Is Simple
![[0_YISbBYJg5hkJGcQd.png]]

---
### How The Gopher Came to Represent the Go Philosophy
![[modelsheet.jpg]]

---
## Great Content to Keep Up w/ Language Evolution
#### Cup O' Go

![[1674486898-artwork.jpg]]

---

## Other Great Podcasts:

![[go-time-original.webp]]

---

Learning Resources:
### Ardan Labs:

![[ardan-labs-go-tour-banner.png]]
---

![[bootdev-logo-full-small.webp]]

---

Learning Guide:
1: Tour of Go - https://go.dev/tour/welcome/1

2: Go By Example - https://gobyexample.com/

3: Gophercises - https://gophercises.com/

4: Use these as references to build an http server from scratch



![[png-clipart-go-programming-language-computer-programming-others-baltimore-web-application.png]]![[images.jpg]]
