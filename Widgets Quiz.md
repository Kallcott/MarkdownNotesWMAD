# Widgets Quiz
Created: 2022-05-12 07:52
[[Widgets Quiz#References]]

## Maybe on Quiz? -- General Flutter stuff
HummingBird: runs flutter on the web
SKIA: for renders - same as Chrom Os & browser

Ahead of time (AoT) - Compilation
Hot Reload: apply changes to a running application

Cupertino class:   for iOS
Material class:      for andriod

Main.dart : main file for our app. 
- F5 for debugging

## Widgets

All flutter's UI is made of Widgets. Everything is widgets.
- written in Dart
- describe the look of their view.
- On a state change, widgets rebuild. -- therefore Widgets are immutable declarations
- There are no layout files in flutter, just layout widgets. 
- entry is through the void main() {runApp(const MyApp())}

Widgets can be stateful or stateless
- statefull - accepts changes, is dynamic. 
- stateless - only hold configuration, is static. 

Custom widgets are created using smaller widget -- instead of extending them. 

### Widget categories
Layout widgets:  arrange other widgets
- Single child: Align, Aspect Ration, Baseline
- Multi child: Column, Row, GridView, LayoutBuilder
- Sliver widgets: SliverAppBar, CustomScrollView, SliverChildBuilderDelegate
	- Sliver means it is scrollable inside it's container. 

Commonly used Widgets
- Text: display strings
- Row & Column: horizontal / vertical layout.
- Stack: place widgets atop each other in a z index. --Like css Absolute position. 
- Container: html div. background, border, shadow with BoxDecoration widget. 


### Widgets in detail:
Material App:
 import 'package:flutter/material.dart';
 Lets us use AppBar, Scaffold, Listview, StatelessWidget, StatefullWidget
 Properties:  
- themes (+subs): points to color setting that sets our default and accent colors. 
- shortcuits & action: defines hotkeys
- title: defines our app name
- home: holder the body of the app. 
- a number of navigator functions. 

Scaffold:
 Properties:
- appBar: horizontal top bar
- body: content inside the scaffold
- floatingActionButton: Logo/icon fixed in the right hand corner
- drawer: side panel at the side of scaffold. Callapses down. 
- bottomNavigationBar: menu at the bottom. Min two items. 

### Visible and invbisible widgets
Visible widgets: drawn on the screen
- Elavated button
- Text
- Card
- TextField +
Invisible widgets: give structure without being displayed
- Row & Column
- ListView
- Stack
Conatiner is by default invisible, but with styling becomes visbible. 

## Notes from Demos
To create an app:
- flutter create {folderName}  // Must be lowercase with underscores. 

### Hello World App:
Element properties are formated like so:
`textDirection: TextDirection.ltr`  // ltr = left to right

### Image Demo App
Any asset is only availble in app after rebuild:
- flutter pub get

We declare variables and functions betwween Class and @overide Widget builder
```
class _BulbAppState extends State<BulbApp> {
  int bulbNum = 1;

  void toggleBulb() {
    if (bulbNum == 1) {
      bulbNum = 2;
    } else {
      bulbNum = 1;
    }
    setState(() {}); // this could wrap around everything of be set seperate.
    print("Bulb$bulbNum is selected");
  }

  @override
  Widget build(BuildContext context)
```

#### Metadata
SplashScreen
	1. drop image in drawables folder
	2. Goto: andoird/app/src/main/res/drawable --> launch_background.xml
		- in item withing the layer-list tag
		```
		<item>
		        <bitmap
		            android:gravity="center"
		            android:src="@drawable/piranesi_prisonniers" />
		    </item>
		```    
App Label
	1. Goto android/app/src/main --> AndroidManifest.xml
	2. change manifest->application android:lable="myAppName"
App Icon
	1. Generate image with https://appicon.co/  This creates a bunch of mipmap folders
	2. Replace mipmap folders in android/app/src/main/res

#### Image
1.  Declare image
	- Image( image: NetworkImage ( {link} ) )
	- For Asset images:
		- Image( image: AssetImage( {path} ) )
		- Image.asset( {path} , height: 200,)
The benefit of using 
2.  Adding asset image to project
	- add images folder
	- save myimage.jpeg to images folder
	- add to pubspec
```
flutter:
  uses-material-design: true
  assets:
    - images/
```
- images/                            //will allow us to add an entire folder
- images/myImage.jpeg    // will add the specific image

### Fonts
1. a. Install package, inside project terminal type: 
````
flutter pub add google_fon
````
1. b.  Adding asset image to project
	- add folder called fonts. 
	- save myfont.ttf to the fonts folder
```
// after images
  fonts:
    - family: WaterBrush
      fonts:
        - asset: fonts/WaterBrush-Regular.ttf
```
2. a. asset -- text style
```
const Text(
  'Downloaded font family',
  style: TextStyle(
	fontFamily: 'WaterBrush',
	fontSize: 48,
  ),
```
2. b. package -- declare text style
```
Text('Light Bulb App',
	style: GoogleFonts.nunito(
	  fontWeight: FontWeight.w700,
	)),
```




## References
[[Class 2022-04-29]]
