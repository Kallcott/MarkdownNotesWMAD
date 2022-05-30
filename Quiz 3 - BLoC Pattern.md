# Quiz 3 - BLoC Pattern
Created: 2022-05-30 17:05
[[Quiz 3 - BLoC Pattern#References]]

SetState is not the best apporach for interactivity with any complexity, or scale. 

Benefits of Bloc?
- to seperate logic and layout
- to make reusable code
- to stop duplicating data when you update your app. 


## Listening to the stream
Made of 
- Streams: has an entrace and an exit. Data only flows one way
- StreamControllers: controls the stream
	- .sink property is the data-entrance.
	- .stream property is the data-exit.
- Syncs - like async requests and async reponsses //my own reminder

StreamSubscription object: is listened to.                           
- errors - dataflows out 
- gets notified when an event related to the stream is triggered.
DataTransformer object:                                              
- modify data - filter data
- transformes adta inside the stream

## About Blocs: Business Logic Components
supported by Google
introduced in dart conference in January 2018
- states you should move business logic out of UI and into Blocs.
- BLoC should be platform and environment independant for reusability. 
	- For Dart apps && Web with Dart Angular

Example: 
- sinks take events from a widget.
- streams output result to other widgets. 
- Inside of the Bloc is independent from the UI. 

![[Pasted image 20220530173224.png]]


## References
!
