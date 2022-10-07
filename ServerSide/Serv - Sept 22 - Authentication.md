# Class Sept 22
Created: 2022-09-22 10:38
[[Serv - Sept 22 - Authentication#References]]

## PP ASP.NET Identity
- creat new project, use MVC template 
	- Authenticatoin = individual accounts

Limitations
- Cannot add authentication after project creation.  
	- Cannot change from None -> Individual Accounts, -> Microsoft Network -> Windows
- If it has to be done, you must take a new project and copy code over. 
- This limitation isn't the case in .NET Core (.NET 6)

Identity
Domain -> API/Server ( User, Role, SignIn)
Persistentce

Models-
	- Classes for data models
	- Context classes
	Need to run commands with connection string to trigger migration. 

By default VS 2022, saves account in a hidden database file inside App_Data within the project. uses SSDT - Sequel Server Data Tools
- using it's default connection string in the root WebConfig file. 
- We can change the connection to connect to our SQL server by changing 
	- Data Source =(Local) instead of Data Source=(LocalDb)\MSSQLLocalDB;
	- remove: AttachDbFilename=|DataDirectory|\aspnet-mvc2022AuthenticationDemo-20220922105400.mdf;

Don't Upgrade Bootstrap to 5.x from 3.x. The syntax has changed and it will break the defaults. 

MVC template
- creates the first migration already. 
New Migration create a new class with two methods: Up & Down
	- Up
	- Down
- Sometimes it is empty and we can get rid of it. 

Identities model File contains more than one class. 
	- It contains the IdentityDbContext Class for our Migration
	- Here store the name of the connection string for the Database.
		- Example of a constructor that is calling it's base class constructor
			"public ApplicationDbContext()
				: base("DefaultConnection", throwIfV1Schema: false)"

Migration are first step, they have to applied with NuGet command: Update-Database
- if migration files are deleted the database will be broken.
- each migratoin is a collection of changes that built to the present day database. 

## References
!