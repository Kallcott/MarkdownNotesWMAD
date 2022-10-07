# Class 6 - Uploading Files
Created: 2022-09-20 10:38
[[Serv - Sept 20#References]]

- How to use a model from a view:
	- @model IEnumerable <Project.Models.MyControllerName
	- Configure our project to connnect to a database: create database. table, and populate.  Automatically 
-Controllers need action methods to work: ie index

## PP Image Upload Pt 1
Physical vs Logical architecture
- Physical
	- How many physical PCs being used
- Logical
	- how many different deployements, irrespective of physical resources. ex: server and Client on the same PC

Client and Server
- Connections
	- Query - Model (Properties: File -> Size, Ext, Locatoin, Name)
	- Responce - Controller - Storage (Path)

### Files
File Uploads and using the file system
- We must ensure they are safe: Ensure correct file type, Max Size, 

#### File System
HttpPostedFileBase file;
	- file.Content.Length  // size in bytes
System.IO.File
	- File.Move(string sourceFile, string destinationFile) // moves a file
	- File.inputStream // gets a stream object that pointsto an uploaded file. Read contents
	- File.SaveAS(string path) // saves contents
System.IO.Path
	- Path.Combine()  // combines two strings into a path
	- Path.GetFileName(string path) // retruns the filename and extension of specified path strings
### Server
Server.MapPath(string path) // returns physical file path to specified virtual path
### Directory
Directory.Exists(string path) // determines 
Directory.GetFiles(string path)
## System.drawing.image
System.Drawing.Image.FromStreams(Stream stream) // creates an image from the specified data stream
System.Drawing.Imagin.ImageFormat //specifies fromat of an image
	- ImageFormat.Jpeg
	- ImageFormat.Gif
	- ImageFormat.Png
	- ImageFormat.Tiff
	- ImageFormat.Bmp
	- Lots More
Image.RawFormat // gets the file format of the System.Drawing.Image

## Code
Controller actions are configured for specific types of requests
- default is GET
- Action result is a abstract class that includes ViewResult. 


## References
!