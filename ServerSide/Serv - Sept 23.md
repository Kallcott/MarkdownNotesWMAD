# Class - Sept 23
Created: 2022-09-23 08:38
[[Serv - Sept 23#References]]

## Revew
- Migrations
	- Note how migration removes PK before removing the tables
	- To add a new model, we must also add it in the context (IdentityModels)
	- To add new changes we must create a new migration, then update database
		- Don't modify the migration files
		- We also need to delete the Controller and it's views & regernerate it from the EF model
	- DateTime can't be null, so it will automatically make this required
		- It can be made optional be add a "?" nullable = DateTime? DateOfBirth
		- Records without a DOB, will be given a default DOB of 1/1/00, because databases can't store null dates. 
	- We can use the "-verbose" flag in NugetTerminal to get more details on the commands


## PP: Authentication.
- disallows anonyumous access on a controller
		- Use square brackets on specifc actions \[AllowAnonymous] or \[Authorize]
			- Can be attacked to the whole controller class, or individual actionResults
				- If a whole class has \[Authorize], exception with the action can be allowed with \[AllowAnonymous]
		- Can be performed Globally
- Can be done by roles & use login 
		- -- CASE SENSITIVE
		- if(User.Identity.IsAuthenticaed) { // do something}
		- if(User.IsInRole("Admin")) { // do something}
		- Roles use the Database's Name column to match in VS2022 logic
- Best practice to change admin via SQL
		- Add Role -- INSERT INTO AspNetRoles (ID, [Name]) VALUES ('ADMIN' , 'Administrative (POWER) User');
		- Add UserRole -- INSERT INTO AspNetUserRoles (UserId, RoleId) VALUES ('e01ee861-d230-4b27-b487-7ba4c1f21d6f' , 'ADMIN');




## References
!