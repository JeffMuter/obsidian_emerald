schema is old, I thought we reloaded, but need to try that again.

in terminal, in database/ dir, run 

sqlite3 database.db   // opens db in sqlite3 cli tooling mode
.read schema.sql        // tells sqlite to read the current schema.sql
.quit                           // exits sqlite3 mode
