bug where we're not getting all the locations to show the user where we can move the worker to...

getting locations, but while the worker is no longer at the old location, im not seeing them in the new location they were sent to...

Issue with a query that's notorious... it is returning null on a couple task_types, evne though they have values in the task type & worker task, it must be an issue with the joins.

appears this was finally solved by a different kind of join.