# Quiz 2 - Packages, Class Constructors, Named Arguments
Created: 2022-05-24 11:13
[[Quiz 2 - Packages, Class Constructors, Named Arguments#References]]

## Packages
Packages: tools for a language developed by externally. 
- importable libraries
	- Add within the pubsepc.yaml
	 - Use flutter pub add MyPackage
- speed up development
- pub.dev/flutter/packages
- Judge based on likes and popularity, and PUB points
- Pub points represent a standard
	- Dart file conventions
	- Documentations
	- platform support
	- pass static analysis
	- up to date dependencies
	- null safety

Localizations: langues for dates, currency, etc
- by default flutter provides only US English, other are installed via packages. The main package is below:
	- import 'package:flutter_localizations/flutter_localizations.dart';

Installing Localizations:
- In pubsepc
```
dependencies:
	flutter:
		sdk: flutter
	flutter_localizations:
		sdk: flutter
	intl: ^0.17.0 # Add this line

```
```
flutter:
  generate: true # Add this line

```


## Class Constructors & Named Arguments
We use classes to group data
```
class Person {  
	String name = 'Bob';  
	int age = 30;  
}
```

Class constructors allow us to build classes as we need to:
```
class Person {  
	String name;  
	int age;  
		//Note that unlike other languages we dont need to specify the keyword "constructor"
	Person(String name, int age){  
		this.name = name;  
		this.age = age;  
	}  
}

// In code
void main() {  
	var p1 = Person('Bob', 30);  
	print(p1.name + ' '+p1.age.toString()); //Bob 30  
}

```

Notice how the argumenst below are wrapped in curly braces, these are named arguments
-  ***These are optional*** Beware, crashes could happen if an optional argument is left out and code requires it to execute. 
```
Person({String name, int age}){  
	this.name = name;  
	this.age = age;  
}
```
Benefits:
- use only what you need `var p1 = Person( name: 'Bob');`
- use them in any order `Person(age: 30, name: 'Bob');`
- Default Values 
```
Person({String name, int age = 30}){  
	this.name = name;  
	this.age = age;  
}  

var p1 = Person( name: 'Bob');//Note age is not passed in here  
print(p1.name + ' '+p1.age.toString()); //Bob 30
```
- use @Required to make something not optional. -unique to flutter, doesn't work in dart. 
```
Person({@required String name, int age}){  
	this.name = name;  
	this.age = age;  
}
```

We can also remove the constructor's body and use shorthand:
```
Person({this.name, this.age});  
}
```

## References
!
