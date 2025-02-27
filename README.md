Pagila
======

Pagila is a port of the Sakila example database available for MySQL, which was  
originally developed by Mike Hillyer of the MySQL AB documentation team. It  
is intended to provide a standard schema that can be used for examples in 
books, tutorials, articles, samples, etc.

All the tables, data, views, and functions have been ported; some of the
changes made were:

* Changed char(1) true/false fields to true boolean fields
* The last_update columns were set with triggers to update them
* Added foreign keys
* Removed 'DEFAULT 0' on foreign keys since it's pointless with real FK's
* Used PostgreSQL built-in fulltext searching for fulltext index.
  Removed the need for the film_text table.
* The rewards_report function was ported to a simple SRF

The schema and data for the Sakila database were made available under the BSD
license which can be found at http://www.opensource.org/licenses/bsd-license.php.
The pagila database is made available under this license as well.  


FULLTEXT SEARCH
---------------

Fulltext functionality is built in PostgreSQL, so parts of the schema exist
in the main schema file. 

Example usage:

SELECT * FROM film WHERE fulltext @@ to_tsquery('fate&india');


PARTITIONED TABLES
------------------

The payment table is designed as a partitioned table with a 6 month timespan
for the date ranges. 
If you want to take full advantage of table partitioning, you need to make
sure constraint_exclusion is turned on in your database. You can do this by
setting "constraint_exclusion = on" in your postgresql.conf, or by issuing the
command "ALTER DATABASE pagila SET constraint_exclusion = on" (substitute
pagila for your database name if installing into a database with a different
name)


INSTALL NOTE
------------

The pagila-data.sql file and the pagila-insert-data.sql both contain the same
data, the former using COPY commands, the latter using INSERT commands, so you 
only need to install one of them. Both formats are provided for those who have
trouble using one version or another.

VERSION HISTORY
---------------

Version 2.0
* Update schema for newer PostgreSQL versions
* Remove RULE for partitioning, add trigger support.
* Update years in sample data. 
* Remove ARTICLES section from README, all links are dead.

Version 0.10.1
* Add pagila-data-insert.sql file, added articles section

Version 0.10
* Support for built-in fulltext. Add enum example 

Version 0.9
* Add table partitioning example 

Version 0.8 
* First release of pagila
# hello-world
# hello-world
