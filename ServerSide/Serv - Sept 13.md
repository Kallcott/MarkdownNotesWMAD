# Class 3
Created: 2022-09-13 10:30
[[Serv - Sept 13#References]]

- Model: Data layer
- View: UI Layer
- Controller: Business layer

MVC project using ASP NET

Controllers always have the index method
Run the MVC project through a server & connect through a browser/terminal

Views are coded in RAZOR - which is HTML + C# 

USE ASP.NET Web Application (.NET Framework)
	- Choose "Empty"
	- Check "MVC core references"
	- Check "Configure for HTTPS"

Base Files
	-App_Data : nothing yet
	- App_Start : has RouteConfig. This controls the default controller
		- There is no controllers made by default, so a home controller shoud be made
	- Controllers : empty
	- Models : emptu
	- Views : has web.config

Adding Controller
	-Right click Controller folder, Add- Context-option "Controller..." -> "Add MVC 5 Controller - Empty" -> rename "HomeController"
		- required name follow "MyNameController"

Adding View
	- Each controlelr is linked with a view folder of the same name
	- View can be added from controller : right click in controller's index code "Add View" -> "MVC 5 View" -> "Add"
		- View Layout can be disabled by unchecking "Use a layout page"

Modifying View
	-ViewBag.Title: Modifier's tab name
	- html is content
	- Title, Footers, Head, etc is in Views/Shared/\_Layout.cshtml
	- Bootstrap is integrated into ASP.NET

Shared Layouts
	- @ViewBag.Title
	- ActionLinks
	- @RenderBody() : where views will be injected
	- 

Package manager for .NET is called nugget
	- Tools -> NuGet Package Manager

Navigating an ASP.NET project in Browser
	- localhost:44304
	- add /MyName (don't add Controller keyword)
	- add /MyAction (localhost:44304/Home/NumbersSum)
	- When Controllers are shanged the server must be stop and restarted
	-  Can Launch a specific view if you hit Play inside the view.cshtml

Errors
- If your ActionResult requires input, but receives a null we will get an error.
	- Null entry for parameter 'x' of non-nullable type
	- Fixed by providing defaults or being nullable
- If your ActionResult lacks a veiw
	- view 'MyAction' or it's master was not found
	- Right click in action -> Add View

ActionResults
	- Pass code into a view using the Viewbag : 
		- ViewBag.MyVariable = myVariable
	- For quick debugging use QueryStrings inside the URL. - not case sensitive
		- ?x=4&y=2

Gang of Four Design Patterns - PDF DO LOOKUP

### Powerpoint : Getting started with RAZOR
Views
		- HTML that can be embeded with c#

Benefits
		-Significantly less code, but more complicated
		- @ symbol to use C#
		- @{ } for single/multiline C#

Be wary of types
		- Array Lists take objects: in C# everything is an object, so must must validate

Comments: 
		-// or /\*\*/ only C# mode. 
		\<!-- --> only HTML 
		@\* \*@ alternate Razor universal comments

Wrting HTML Tag inside a C# block (@) will switch code
	- scope of these variables are throughout the view. 

### Other
ActionLinks components
	- Title
	- Action
	- Controller
	- Parameters (area by default) ex: , new {x=7, y=5}
		- When done correctly the parameters will show up in the HTML
	- CSS ()



## References
!