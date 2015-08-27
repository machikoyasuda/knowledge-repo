# Cannot connect

 1. Quit Postgres.app
 2. Open Activity Monitor, see if any processes name postgres are running. If so, kill them.
 3. Delete the Folder ~/Library/Application Support/Postgres
 4. Open Postgres.app again
 5. Wait a few moments before clicking "Open psql", initialising the database might take a few seconds

# FATAL: Role does not exist
- Create db
psql
CREATE USER superb SUPERUSER;
ALTER ROLE superb WITH CREATEDB:
- rake db:setup
- rake db:create:all
- rake db:migrate