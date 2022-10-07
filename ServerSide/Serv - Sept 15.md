# Class 4
Created: 2022-09-15 10:40
[[Serv - Sept 15#References]]

- MVC
	- Model: Data & validation
	- View: Client & visuals
	- Controller: Business logic

We use razor to write files
- two file types: CShtml VBHtml (visual basic)

Create controllers:
- Class that contains methods

By default a view will be linked to the argument inside the View() call.

## Powerpoint Models with strongly typed views
The model:
	Representation of real world objects, processes, and rules that define the subject of interest (domain)
	- contains c# that makeup the application
	- Views & controllers expose the domain to our clients in a consistent manners
	- When working with the database you start with models as the focal point. Then add controllers and views. ex with UML

## Code
To add a model - add a class. 
- store informatoin as properties

## PP
Using the Entity Framework, or EF
- part of the .NET framework - allows database access with strongly type c# code
- No worries about Low-Level-Abstractoins when classes use ET
- No connections, sql commands, sql parameters, sqlresulttests, etc
	- instead use C# with LINQ
	- LINQ (Language INtegrated Query) is .NET framework component to add native data queries
We will be using ET and Code first approach to create MVC data-centric applications 

ET can be used with many Relational database managements systems
	- SQL Server
	- SQL Server Compact Edition
	- Oracle
	- DB2
	- & More

Can be used in 3 different ways:
	Database First Approch / Schema first approach
		- Open graphical designer in VS
		- Point to database & it imports the db schema & generates all the classes you need to query. Updates the DB
		- **Hardley ever used**
	Model First Approach
		- Using graphical designer to draw a conceptual model for the app
		- ET generates class definition and the DB scheme
		- **Hardley ever used**
	Code First Apprach
		- code doesn't need to know database abstraction details.
		- write your C# model classes first & the EF can generate a DB for us on the lfy.
			- based on those class definitions 
			- can map your classes to an existing DB using Conventions (naming conventions)
			- can manually provide an explicit mapping from a property on an object to a column that is in a DB table
		- **Most widely used & embraced**

## Validating Data
- using statement for System.ComponentModel.DataAnnotations
Example
```
	// Required values
	[Required(ErrorMessage="Weight is required.")]  

	// Ranges
	[Range(80, 500, ErrorMessage = "Sorry, you must enter a value between 80  
	 and 500 pounds.")]
```

View helper Methods
- many built in helper methods for HTML links, text inputs, checkboxes, selection menus, & custom controls
- HTML helpers render HTML. Most times it is a method that returns a string.
- Are not required, but increases speed

Action Link Helper
- HTML.ActionLink() easiest way to link. 
	- takes parameters depending on the overload
```
	@Html.ActionLink(“BMI Application”, “BmiResponse”)
```
- Can also pass route values from a HTML.ActionLink() to a controller action.
	- Like for the Id of a database record to edit:
```
	@Html.ActionLink("Edit Record", "Edit", new {Id=3})
	//The html rendered by this link looks like:
	<a href="/Home/Edit/3">Edit Record</a>
```

Other Helpers:
		◦ Html.TextBoxFor()  
		◦ Html.TextAreaFor()  
		◦ Html.DropDownListFor()  
		◦ Html.CheckboxFor()  
		◦ Html.RadioButtonFor()  
		◦ Html.ListBoxFor()  
		◦ Html.PasswordFor()  
		◦ Html.HiddenFor()  
		◦ Html.LabelFor()  
		◦ Html.EditorFor() // This one will render different html controls depending on the model  
		property’s datatype
	
## Code
to use a model in a view
- `@model mvc2022BMICalculator.Models.BMIResponce
start form with: 
```
	@using (Html.BeginForm()){
	
	}

```
Create user inputs with:
	`@Html.TextBoxFor(m => m.Weight)


## MR M Insights
First time HTML load we make a GET request
After that we make a POST request

By default our controller will only have a reaction to GET requests
We must make a create a responce for POST requests
- we use a HTTP verb annotation
```
        [HttpPost]
        public ActionResult Index(BMIResponce resp)
        {
            return View();
        }
```

In order to actually show validation to the user we must provide the following:
```
@using (Html.BeginForm())
{
    @Html.ValidationSummary()
    // ... HTML ...
```


## References
!
