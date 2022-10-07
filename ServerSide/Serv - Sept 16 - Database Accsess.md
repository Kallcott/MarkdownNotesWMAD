# Class 5 - Database Accsess
Created: 2022-09-16 08:33
[[Serv - Sept 16 - Database Accsess#References]]

ActionResult or ViewResult?
- conrtollers return actionResult to return viewResults
	- ViewResult is one of the subtypes of action result

ViewModel
- a models don't work with databases, and instead passes data between classes

ORM, object-ra.atoinal mapping - is the generic term for the entity relation framework. 
- ET is specialized for a code-first apprach

Having more than one SQL Express service can mess with VSCommunity's instance of SQL

Databse Connection
- need a connection string in web.config
- need to install EF from NuGet
- Create a context class for your Models
- Enable Nuget
	- command: enable-migrations
			- error: connection string is incorrect
			- How: there is a pairity between name of your ContactContext.cs & name inside connection string
			- finished: creates a Migration folder w/ a configuration.cs
	- command: add-migration initialDb
			- uses ContactContext
			- finished: in Migration folder creates a file with date/time stamp.
				- this file is the database in a POCO format (plain old CLR object)
				- Identity will be chose based on the model's property with "ID" at the end of it
			- name of every first migration is initialDb
	- command: Update-database
		- this adds the db to server
			- the connection string's initial Catalog will be the name of the database
				- have unique database names
		- Contains a migration history table. 
	- Migrations can be reverted
	- After database is created we can make a controller based off of our database.
		- use drop down to select in controller creation
	- 




## References
!