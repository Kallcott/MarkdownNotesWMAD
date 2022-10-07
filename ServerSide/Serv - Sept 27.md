# Ntie - Sept 27
Created: 2022-09-27 10:32
[[Serv - Sept 27#References]]

- Do activity on

WHERE is Default Connection targetter
	- Defined inside WEB.config
	- For the MVC template's Context -Under the IdentityModels dropdown is: "ApplicationDbContext"
		- There we can edit public ApplicationDbContext
		- If it fails it fallback to creating a local db: its in App_Data -> DefaultConnection.mdf

IDK What we're doing I fell behind.

## PP Migrations
Review of 
	- Classes DBContext
	- and classe DBSet

## Code
Add a model to be tracked
	- Create a class inside Models
		- add all your properties to store data.
	- Alter file IdentityModels.cs
		- Add a property under the class: ApplicationDbContext : IdentityDbContext\<ApplicationUser>
			- public DbSet\<Book> {get; set;}
	- in package console: 
		- add-migration myMigrationName
		- update-database

## PP Cont.
Data access in MVC

Changing Migration
	- all use the Parameter "Target"
		- update-database -target test
			- This will only update in SSMS, it will not change your source code. 
	- TargetMigratrion:0
		- update-database -TargetMigration:0
			- Because we specify index of the migrations we can select 0, or unmodified table. This is even before initialDb. No Tables. 

Modifying migration
	1. Revert to previous migration 
		- update-database -target initialDb
	2. Update your Model
		- changed code in BookStoreModel.cs
	3. Delete that migration
		- solution explorer - delete added book model
	4. Add migration
		- add-migration addedBookModel
	ORR
	For the very last migration
	1. Update your Model
	2. Add migration force
		- add-migration updatedBookAddedAuthorModel -force

## References
!