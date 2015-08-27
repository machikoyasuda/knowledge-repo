1. Normalization: Store data in one place. But often you have to use that data in several places. 

In mySQL: break up into relational tables
and create associations

In noSQL: keep copies of data

2. Back up your database.

3. Have a GUID that is not used for anyone else. (Or serialized integer)

4. Index everything you will query and search with. Indexes take up a lot of space. 

5. Don't put anything that can be calculated from something else. It should be a canonical reference. Everything else is subordinate. 

## Joins

Inner v. Outer join: