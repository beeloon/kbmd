```bash
# connect to PostgreSQL database with <username>
psql -U <username>

# connect to <database_name> database with <username> and <password>
# -W option => force psql to prompt for a password before connecting to a database
psql -d <database_name> -U  <username> -W

# connect to <database_name> database on certain <host> with <username> and <password>
psql -h <host> -d <database_name> -U <username> -W

# list available databases
\l

# command that help you switch connection to a new database, with user which is optional
\c <database_name> [<username>]

# list available tables
\dt

# describe a table
\d <table_name>

# list available schema
\dn

# list available functions
\df

# list available functions
\dv

# list users and their roles
\du

# show postgres version
SELECT version();

# to execute previous command use
\g

# list command history
# if you want to save command history to <filename>, put name of the file as a argument of \s command
\s [<filename>]

# execute psql commands from a file
\i <filename>

# get help on psql commands
\?

# To get help on specific PostgreSQL statement, you use the \h command.
\h ALTER TABLE


# if you want to quit from psql use following command
\q
```