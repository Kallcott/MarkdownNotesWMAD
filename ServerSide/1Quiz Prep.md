
## MVC Intro
Model View Controller - NOT from microsoft, a design pattern
- sepration of concerns

Models - for data & validation layer      
View - for user interface layer (input logic)                -- visual represents model
Controller - for business logic layer        -- incoming requests

Steps
	1.  Create project
	2.  ASP.NET Wb Application (.NET framework) c#, not VB
	3. Empty or MVC +Optional Authentication, HTTP, MVC box checked
Folder for Controllers, Models, Views
	- Controllers are special classes
	- Models are just classes w/ props & validation in \[]
	- Views are made by left clicking in controller. 

Controllers
Controller always end with "Controller"
Default starting controller is in App_Start -> RouteConfig
	- routes.MapRoute - default parameter
	- Crashes without a Home, or reassign -- "Server Error in '/' Application"
Each controller holds many Action Results (index)
	- can add many more. 

Views: 
	- Shared layout in Views -> Shared -> \_Layout
	- Pass Information between controller and View using ViewBag.
	- @RenderBody is where view will be rendered


## PP Razor
 razor files:  extension:  ".cshtml"
@{do work}
\<p>@myvar\</p>
\[HTTP GET]]
\<!-- HTML comments-->
\@* Razor Comments \*@
isPost property to see whether a request is a GET or a POST for a page. 

Razor syntax: requires string to be enclosed in double quotes: "

Action Link: 
<li> @Html.ActionLink(  
 "Bonus Calculator", //linkText  
 "BonusCalc", //actionName  
 "Home", //controllerName  
 new { @amount = 1000 }, //routeValues ... in this case querystring values  
 null //htmlAttributes  
 )</li>

## PP BMI Model
HTTPGET - reading data (can send via queryString ?mVar=1&myVar2=2)
HTTPPOST - sending data via HTTP header

We use \[] to denote HTTPGET or HTTPOST before action links
	- by default its GET

## PP Model
Normal classes & Contructor:

public class BmiResponse  
{  
	public double Weight { get; set; }  
	public double Height { get; set; }  
}

ET or Entity Framework: 
	- works with many RDBMS

Different appraoches
	- Database First Approach / Schema First Approach             -- Generates class from a DB schema
	- Model First Approach      -- Generate DB & Code from a conceptual model
	- Code First Approach    -- Generate DB from Code

Validation 
	- \[Requires(ErrorMessage="TextText")]
	- \[Range (80, 500, ErrorMessage = "TextTextText")]
Match your ranges with intended DB ranges
	- \[Display()]
	- \[Min/MaxLength] - These are two seperate
	- \[DataType(DataType.Current)] - doesn't actually validate
	- \[DisplayFormat(DataFormatString = "{0:yyyy-MM-dd}", ApplyFormatInEditMode = true)]
	- \[RegularExpression(@"^[A-Z]{2}$", ErrorMessage = "Country code can only be two alphabetic characters in CAPITALS")]

Helpers in Views
	- HTML.ActionLink() - create a link to a controller's action
			- Can also also pass in parameters like so:
			@Html.ActionLink("Edit Record", "Edit", new {Id=3})
Form Helpers
	- Html.TextBoxFor()  
	◦ Html.TextAreaFor()  
	◦ Html.DropDownListFor()  
	◦ Html.CheckboxFor()  
	◦ Html.RadioButtonFor()  
	◦ Html.ListBoxFor()  
	◦ Html.PasswordFor()  
	◦ Html.HiddenFor()  
	◦ Html.LabelFor()  
	◦ Html.EditorFor()
More
	- HTML.BeginForm() - writes a form tag ->& submit
	- HTML.ValidationSummary() - prints validation from model error messages
	- HTML.TextBoxFor() - Links Textbox to data for validation


## Partials
Are HTML Templates.
	- Naming conventions have a "\_" as first character ex: "\_AddEdit"
	- placed in the Shared folder
To use them instead of using HTML.Action, we use HTML.Partial
	- invoking outside a model, use HTML.Action as normal