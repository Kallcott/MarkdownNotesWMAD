# Serv - Oct 04
Created: 2022-10-04 10:36
[[Serv - Oct 04#References]]

- Install "EntityFramework" by microsoft version 6.4.4
	- This isn't installed by default when we do not have Authentication. 
	- This is seperate from the CORE version. 

Models
- Use validation annotation to validate our properties. 

Before validation can be enabled, we need a valid connection inside webConfig
- Each model needs a database context
		- Add a new class "ProductManager Context"
			- The class must inherit from  DBContext
				- "public class ProductManagerContext : DBContext"
			- Define a collection that contains our models in our context
				- "public DbSet\<Product> Products { get; set; }"

To get rid of a migration you have to delete the migration file. 
Run update database to apply our migrations to our database. 

Mistakes in your webconfig will make a hidden file
- Hidden bin folder
So make sure the name of your connection string matching the name of your Context Class
	- \<connectionStrings>\<add name="ProductManagerContext" ...

Steps to create a new model
1. Create a class
2. add a property for the primary key: "ModelID" or using \[Key]
3. add your properties
4. Add valitaion to properties such as \[Required] and \[StringLength(100, MinimumLength =1)]
5. In Context Class, add property using DBSet\<MyModel> MyModel
6. In Package manager console use command: "add-migration" or "add-migration -Force" (IF overwriting last migration)
7. In Package manager console use command: "update-database"

## PP Implementing Relationships
Ovveriding Default connection string name. 
For the Web.config we can change the name of the connection string using Base/SuperClass
```
        public ProductManagerContext() : base("AlternativeContextName")
        {

        }

```

Primary keys identify unique records
Foreign keys always point to primary keys of other tables. 

For EF we use Navigation Properties
	- properties
		- Choose one way navigation
		- Property looks like:
			- In the single side 
				- "public int CategoryID { get; set; }"
				- "public virtual Category Category { get; set; }"
			- In the Many side "public virtual List\<Product> Products { get; set; }"
		- Points of failure:
			- Foreign keys must have the same type as the primary key they represent.
			- Foreign keys must use the format "ModelID" and never "ID"
				- Beware not matching "ID" ir "Id", keep caps the same between PK & FK

Untangling migration changes
- "Pending migrations"
	- We can comment out all the changes we did since the migration, 
	- Update Database
	- After Update dabase has run, we should be able to add & update the database properly. 
- Usefull Package CLI command: get-migrations


Adding a Controler using a model
1. Add controller
2. MVC5 using Entity Framework
3. Add Controller form:
	1. Choose model class
	2. Choose Data Context class
	3. Leave default checkboxes (Views, References, Layout Page)
	4. Add the controller
4. Add action links in your Views/Shared/\_Layout
	1. "\<li>@Html.ActionLink("Categories", "Index", "Categories")\</li>"
- It is safer to delete a controller and remake it, instead of trying to rename things. 



## References
!