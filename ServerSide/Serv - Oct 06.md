# Serv - Oct 06
Created: 2022-10-06 10:31
[[Serv - Oct 06#References]]

- Create new project - Library Store demo
		- MVC, no authentication
		- By default shows the boiler plate login page
		- Check nugget package manger to check what is installed
				- Tools -> Nugget -> Manage
				- See tabs: browse and serch
					- We need entity framework // could also use packageM console with 'install-package' command
					- We need 
		- Also must need to enable migrations
				- add a context model
					- add class: Library Context
					- Inside Class:  public class LibraryContext: DbContext (needs "using System.Data.Entity" Ctrl+. )
				- Add Connection string in  Web config
					-  "\<add name="SobeysConnection" connectionString="Data Source=localhost;Initial Catalog=mvc2022SobeysDemo;Integrated Security=True" providerName="System.Data.SqlClient"/>""
					- The name in the connection string must match the DbContext
						- We can use base class to override "public ProductManagerContext() : base("SobeysConnection")"
					- We must make sure this name is unique amung our databses (check using SSMS)
				- Now we can use command "enable-migrations" in the packageM console
					- If we created a migration at this point it would be empty. (no Models)

Having issues with migration is hard to fix once the database is updated. Make sure you mirgation are good to go before you use the command: Update Database.

## PP Working Around Conventions PT1
-- will also cover  PP Read Only Properteis
Review
	The name it looks for by default in the connection string matches the context in Library string
	- Model can have validation in them
	- Model must find a \[Key] by default this is ID. This can be datatype INT or String

Default convention: Primary keys in SQL almost always use Idendity
	- We have worked with one to many relationships so far.  

### CODE
Create clas LibarryModels:
	- This wiill contain multiple models

We will stop using an ID, and instead use ISBN as a string key
	- "\[StringLength(13, MinimumLength = 10)]"
	- If we use \[Key] we don't need \[Required], but we left it there because it won't effect anything

- BEFORE WE ADD MIGRATION
		- We must add our library class to our Context
			- "public DbSet\<Book> Books { get; set; }"
		- If we screw up and want to overwrite our last migration use the command:
			- "add-migration initialDb -Force" 
			- Alternatively you can delete the migratoin within file explorer
		- **If we screw up our connection string/context and our didn't go to SQL server it will embed into our project inside the App_Data folder, as a hidden file (usually based off of the Initial Catalog name, but can be random numbers** ON QUIZ
	>Primitive types do not support null: we would have to add a "?" to the type. 
	>		- this includes Datetime, & int
	>If we want to rollback to before initial DB we have to revert using an index of 0.

## PP Actually inside the PP
Primary Key conventings:
	- By default our PK is INT, because indentity uses ID
	- We can also use a string, this means DatabaseGeneratedOption is set to None
		- This disables the Identity on the PK
		- We can set this for INT as well. 
			- This is usefull when we want the user to input a value, instead of the database creating one (our ISBN)
		In both cases it is best practice to use: (it is automatic if we use string type)
		"\[DatabaseGenerated(DatabaseGeneratedOption.None)]" on our Key in our model (like \[Required])
- There is a third option for DatabaseGenerated Option: **Computed**
		- This lets us do stuff we'll learn at a later date.

## CODE
- we added "	"\[DatabaseGenerated(DatabaseGeneratedOption.None)]" to our ISBN
Once we add our first table we actually have two tables: myTable & \_MigrationHistory

## PP
No Pludal Table names
- What do we do if our plural has no S like for Moose or Mouse vs. Mice
		- We must add an overide method:
```
	protected override void OnModelCreating(DbModelBuilder modelBuilder)
	{
		base.OnModelCreating(modelBuilder);
	
		modelBuilder.Conventions.Remove<PluralizingTableNameConvention>();
	}
		
``` 
- It will auto create a lot of this as we type, but we must add the "modelBuilder.Conventions.Remove<..."

 If we want to do this on an existing database:
 - Go nuclear and delete the whole database: This is bad if we have any data we want ot keep. 
 OR
-- **ON QUIZ UP and Down: Down is the code to revert changes, up is the code to get new chanegs**
	- use command "update-database -targetmigratoin:0" to revert every change
	- Alt: "update-database -targetmigration:InitialDatabase" this is a bit confusoin because it is different to InitialDb we use

YAY now our table is Book instead of Books!
- BEWARE IF we try to change a migration that we've already applied to the database. Make sure to revert. 

## CODE
We added author class
New toic we specifed the Id prop for author with:
```
        [Key]
        [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
```
Remember to add Author to the Context (DbSet\<author>) mode
	- add-migration addedAuthor -Force  -- if we don't use force it will show our previous attempt. If we didn't spell migratoin name it will yell at us, because only one migratoin can be pending. 

We cannot add another migration if we haven't run update database. 


**ADDING FOREIGN KEY** new way -- ICollection<>
	- anything with I in front of them is an interface. 

In Author
```
        public virtual ICollection<Book> Books { get; set; }
```

In Books (contain FK)
```
        public virtual int AuthorID { get; set; }
        public virtual Author Author { get; set; }
```
- This actually works even theough AuthorID doesn't match author's FK:"AuthorID" - PK:"Id"
		- but this is garantees so make sure to double check migratoins, or use exact names FK:"AuthorId" -  PK:"AuthorId"

Stepping into controllers
- Only generate controllers after the models have been created
		- That way we can use the models as a template
		- It is easier to delete the entire controller and regerate them
	- Our Publication didn't display a date picker because we didn't display data type in the model ( \[]  )
	- We will crash our program atm if try to type a duplicate PK. 




## References
!