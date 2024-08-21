i noticed the resources haven't updated much. I may have been wrong that this is working correctly.

found the issue, we're never getting the base_rate for each resource. not sure the best way to add that in yet.

solved. I wrote a function for this, but forgot to use it.

Still an issue where CalculateEarnings is returning a nil slice.

wasn't adding the resource to the new slice after adjusting the quantity.

Now it appears this setup is working correctly.