# The App Life Cycle
---
#### The Structure of an App
```
Model
 ↑↓
Controller
 ↑↓
View
```
#### The main run Loop
```
event -> Os -> Potr -> Event quere -> Main run loop -> Application object -> Core objects -> Os -> event
```
#### State changes in an ios app
```
Not running
	↓
Inactive  	
	↑↓			
Active		
	↑↓			
Background <-> Inactive 
	↑↓			
Suspended <-> Not running
```
- Not running
	- 실행되지 않았거나, 종료된 상태
- Inactive
	- 실행 중이지만 이벤트를 받고 있지 않은 상태
	- ex) 특정 앱 실행 후 문자를 받아 알림이 온 경우 특정 앱의 상태
- Background
	- view 없이 백그라운드 상태에서 동작함 
	- ex) 음악 재생
- Suspended 
	- 백그라운드 상태에서 활동을 멈춘 상태, 빠른 재실행을 위해 메모리에 적재되어 있지만 동작하지 않고 있다.
	- 메모리가 부족할 때 시스템이 강제종료됨

#### Launch Time
```
App start
	↓
main()
	↓
UIApplicationMain()
	↓
Load main UI file
	↓
First Initialization ->	application:willFinishLaunchingWithOptions:
	↓
Restore UI state <-> Various methods
	↓
Final initialization -> application:didFInishLaunchingWithOptions:
```
#### Into the foreground
```
	↓
Activate the app -> applicationDidBecomeActive:
	↓
event loop <-> Handle events
	↓
switch to a different app
```

#### Into the Background
```
Enter Background <-> applicationDidEnterBackground:
	↓
Allowed to run?  (no)-> app sleeps
	↓(yes)
monitor events <-> Handle events
	↑↓
app sleeps
```
#### Handling alert-based interruptions
```
event loop
	↓
a phone call arrives or an alert-based interruption occurs <-> applicationWillResignActive:
	↓
ignore? (yes)-> applicationDidBecomeActive: -> event loops
	↓(no)
switch to a different app
```
#### background to the foreground
```
switch to this app
	↓
wake up app <-> applicationWillEnterForeground
	↓
Acitvate the app <-> applicationDidBecomeActive:
	↓
Event Loop <-> Handle events
```
#### The Background Transition Cycle
```
User switches to a different app
	↓
Deactivate this app <-> applicationWillResignActive:
	↓
Enter Background <-> applicationDidEnterBackground:
	↓
Allowed to run? (no) -> app sleeps
	↓(yes)
monitor events <-> Handle events
	↑↓
app sleeps -> 	Terminate app
	↓
switch to this app 
```

Question
- 새 프로젝트 만들고 실행
- 코드가 어떤 순서로 호출되어 동작하는지
```
//app start
application()
viewDidLoad()
applicationDidBecomeActive()
//home button
applicationWillResignActive()
applicationWillResignActive()
//enter app
applicationWillEnterForeground()
applicationDidBecomeActive()
//home button
applicationWillResignActive()
applicationWillResignActive()
// app off
Message from debugger: Terminated due to signal 9
```
- 실행되지 않는 코드가 있다면 why?
	- 어떤 event 에 대하여 코드가 호출되기 때문에 발생한 event 에 대한 코드만 호출됨  
