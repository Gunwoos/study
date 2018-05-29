# UI Guide
---
#### Points and Pixels
##### point  좌표계는 각 디스플레이의 스크린이 가지는 scale factor 에 따라 rendered pixel 로 옮겨진다.
- Points
	```
	절대적인 값
	1인치를 72로 나눈 값 ( 1pt )
	```
- Pixel
	```
	상대적인 값
	해상도를 나타낼 때 사용, 화소
	이미지를 이루는 가장 작은 단위
	```
- point & pixel
	```
	non-retina x 1 → 1pt = 1px * 1px
	retina x 2 → 1pt = 2px * 2px
	retina HD x 3 → 1pt = 3px * 3px
	```
#### Window
```
//  AppDelegate.swift
//  Class0529_2
//
//  Created by 임건우 on 2018. 5. 29..
//  Copyright © 2018년 lims. All rights reserved.
//
import UIKit

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate { 
// app 이 시작되면 호출됨

	var window: UIWindow?

	func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
// Override point for customization after application launch.

	let window = UIWindow(frame: UIScreen.main.bounds)  
	// window 의 사이즈를 각 디바이스에서 가져옴
	
	window.rootViewController = ViewController() 
	// window 의 view 를 기본으로 관리할 함수를 지정
	
	window.backgroundColor = .white  
	// default 값이 없으므로 색상 white 지정
	
	window.makeKeyAndVisible() // app 이 실행되면 main window 와 key 를 만들기 위해 makeKeyAndVisible() 함수를 호출한다
	//convenience. most apps call this to show the main window and also make it key. otherwise use view hidden property
	
	self.window = window 
	// AppDelegate 의 main window 를 window를 지정
	
	return  true
	}
}
```
#### View

##### - View 만들기
```
let newView = UIView(Frame: CGRect(x: index, y:index, width:index, height:index)
newView.backgroundcolor = .white

view.addSubview(newView)
```  
##### - 디바이스의 width, height 값 가져오기
```
let newView = UIView(Frame: CGRect(x: Int(view.frame.minX), y: Int(view.frame.minY), width: Int(view.frame.width)/2, height: Int(view.frame.height)/2))
/*
view.frame.minX : x축의 최소값
view.frame.maxX : x축의 최대값, 즉 각 기기의 width 값과 같음
view.frame.minY : y축의 최소값
view.frame.maxY : y축의 최대값, 즉 각 기기의 height 값과 같음
view.frame.width : 기기의 width 값
view.frame.height : 기기의 height 값
*/
```
##### - UIScreen.main.bounds 와 view.frame.index 의 차이
- UIScreen.main.bounds
	- 해당 디바이스의 길이 값을 가져옴
	- view 를 생성 전에도 사용 가능
- view.frame.index
	- 해당 view 의 길이 값을 가져옴
	- view 생성하지 않으면 호출 불가

##### - frame 와 bounds 의 차이
- frame
	- superView, 즉 상위뷰의 좌표 체계 안에서 해당 view 의 위치와 크기를 나타낸다
	- 기준점이 해당 view의 superView
	- subView 는 superView 가 변경되면 영향을 받음
- bounds
	- View 의 위치와 크기를 자신만의 좌표 체계 안에서 나타낸다
	- 기준점이 View
	- subView 는 superView 의 좌표 체계가 변경 되어도 영향받지 않음

#### Button

##### - button 만들기
```
let newButton = UIButton(frame: CGRect:(x: index,y: index, width: index, height: index)
newButton.backgroundcolor = .blue
newButton.setTitle("Button", for: .normal)

view.addSubview(newButton)
```
##### - button action
```
//button 만들기 코드에 아래 코드 추가
//newButton.addTarget(_ target: Any?, action: Selector, for controlEvents: UIControlEvents)
newButton.addTarget(self, action: #selector(index), for: .touchUpInside)
// 여기서 index 는 작동할 함수를 viewDidLoad() 외부에 구현 후 넣어주어야 한다.
```

#### Label

##### - Label 만들기
```
var newLabel = UILabel(frame: CGRect(x: index, y: index, width: index, height: index))
newLabel.text = "입력할 내용"

view.addSubview(newLabel)
```
#### 응용
```
//  ViewController.swift
//  Class0529_2
//
//  Created by 임건우 on 2018. 5. 29..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
	var countNum = 0 {
		didSet{
			countLabel.textAlignment = .center
			countLabel.text = " countNum : \(countNum)"
		}
	}
	
	let countLabel = UILabel(frame: 		CGRect(x: 15, y: 15, width: Int(UIScreen.main.bounds.width)-30, height: 100) )

	override func viewDidLoad() {
		super.viewDidLoad()
		let newButtonFrame = setFrame(Int(countLabel.frame.minX), Int(countLabel.frame.maxY), 100,  100)
		let newButton = setButton(newButtonFrame, .cyan)
		newButton.setTitle("newButton", for: .normal)
		let plusButtonFrame = setFrame(Int(newButton.frame.maxX), Int(newButton.frame.minY), 100, 100)
		let plusButton = setButton(plusButtonFrame, .darkGray)
		plusButton.setTitle("+1", for: .normal)
		plusButton.addTarget(self, action: #selector(plusButtonAction), for: .touchUpInside)

		let resetButtonFrame = setFrame(Int(plusButton.frame.maxX), Int(plusButton.frame.minY), 100, 100)
		let resetButton = setButton(resetButtonFrame, .brown)
		resetButton.setTitle("Reset", for: .normal)
		resetButton.addTarget(self, action: #selector(resetButtonAction), for: .touchUpInside)

		let alertButtonFrame = setFrame(Int(resetButton.frame.maxX), Int(resetButton.frame.minY), 100, 100)
		let alertButton = setButton(alertButtonFrame, .gray)
		alertButton.setTitle("Alert", for: .normal)
		alertButton.addTarget(self, action: #selector(alertAction(_:)), for: .touchUpInside)

		let newViewFrame = setFrame(Int(newButton.frame.minX), Int(newButton.frame.maxY), Int(view.frame.width)-30, 100)
		let newView = setView(newViewFrame, .green)
		let newLabelFrame = setFrame(Int(newView.frame.minX), Int(newView.frame.maxY), Int(view.frame.width)-30, 100)

		let newLabel = setLabel(newLabelFrame, .black)
		newLabel.text = "newLabel"
		newLabel.textAlignment = .center
		newLabel.textColor = .white
		countLabel.textAlignment = .center
		countLabel.text = " countNum : \(countNum)"
 
		view.addSubview(countLabel)
		view.addSubview(newButton)
		view.addSubview(plusButton)
		view.addSubview(resetButton)
		view.addSubview(alertButton)
		view.addSubview(newView)
		view.addSubview(newLabel)
	}

	@objc func setView(_ CGRect : CGRect,_ backgroundColor : UIColor)->UIView{
		print("---setView()---")
		let view = UIView(frame: CGRect)
		view.backgroundColor = backgroundColor

		return view
	}
	
	@objc func setButton(_ CGRect : CGRect,_ backgroundColor : UIColor)->UIButton{
		let button = UIButton(frame: CGRect)
		button.backgroundColor = backgroundColor
		print("---setButton()---")

		return button
	}
	
	@objc func setLabel(_ CGRect : CGRect,_ backgroundColor : UIColor)->UILabel{
		let label = UILabel(frame: CGRect)
		label.backgroundColor = backgroundColor
		print("---setLabel()---")

		return label
	}
	
	@objc func setFrame(_ x: Int,_ y: Int,_ width: Int,_ height: Int)->CGRect{
		print("---setFrame()---")

		return CGRect(x: x, y: y, width: width, height: height)
	}

	@objc func plusButtonAction(){
		countNum += 1
	}

	@objc func resetButtonAction(){
		countNum = 0
	}

	@objc func alertAction(_ button : UIButton){
		let alertController = UIAlertController(title: "Count Clicked Number", message: "", preferredStyle: .alert)
		let plusButton = UIAlertAction(title: "+1", style: .default){_ in
			self.countNum += 1
		}
		let resetButton = UIAlertAction(title: "reset", style: .destructive){_ in
			self.countNum = 0
		}
		let cancleButton = UIAlertAction(title: "Cancle", style: .cancel){_ in
		}
		for action in [ plusButton, resetButton, cancleButton]{
			alertController.addAction(action)
		}
		present(alertController, animated: true)
	}
	
	override func didReceiveMemoryWarning() {
		super.didReceiveMemoryWarning()
	}
}
```
