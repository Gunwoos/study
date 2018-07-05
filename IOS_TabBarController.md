# NotificationCenter
---

-   인스턴스 간의 데이터를 주고받는 방식
-   **발송자(Notification Center)**: 특정 이벤트가 발생 하였음을 불특정 다수의 객체에게 알리기 위해 사용하는 클래스
-   **수신자(Observer)**: 어떤 객체라도 특정 이벤트가 발생했다는 알림을 받을 것이라고 관찰자(Observer)로 등록을 해두면 노티피케이션 센터가 모든 관찰자 객체에게 알림을 준다.
-   UserDefaults처럼 모든 app이 하나씩 가지고 있다.
- **Notification** 이란 단위로 알림을 하나의 객체에 등록하여 변동사항을 다른 여러 객체들에게 전달하고 싶을 때
- __단__ Notification 생성 후 제거하지 않으면 __메모리 누수__ 가 발생 

### Notification 생성
- 생성은 알림을 받고자 하는 viewController 에서 해줌
```
let myNoti = Notification.Name.init("myNoti") // 전역변수로 생성하기 때문에 좋은 방법은 아님

extension Notification.Name{ // 확장하여 사용하기에 아래 방법을 권장
    static let myNoti2 = Notification.Name.init("myNoti2")
}
```
### Notification data 전달
```
//1
NotificationCenter.default.post(<#T##notification: Notification##Notification#>)

//2
NotificationCenter.default.post(
    name: <#T##NSNotification.Name#>, 
    object: <#T##Any?#> // 전달할 data를 object에 담아 any type 으로 전달 
    )
    
//3
NotificationCenter.default.post(
    name: <#T##NSNotification.Name#>, 
    object: <#T##Any?#>, 
    userInfo: <#T##[AnyHashable : Any]?#>  // 전달할 data를 userInfo 로 dictionary type 으로 전달
    )

```

### NotificationCenter & TabBarController Example

#### TabBarController Storyboard Image

<img width="889" alt="main storyboard 2018-07-05 17-21-18" src="https://user-images.githubusercontent.com/39073993/42311102-038a2ca4-8078-11e8-8895-de8fec50422d.png">

1. ViewController 7개를 관리하는 TabBarController 만들기
2. Item2ViewController 에서 RGB 값을 Item3ViewController 에 전달하여 Item3ViewController 의 myView 배경색 바꾸기 

#### Item1ViewController

```
//
//  Item1ViewController.swift
//  0705_TabBar
//
//  Created by 임건우 on 2018. 7. 5..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class Item1ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        print("Item 1 viewDidLoad")
        // Do any additional setup after loading the view.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    override func viewWillAppear(_ animated: Bool) { // view 가 곧 생길 때 호출
        super.viewWillAppear(animated)
        
        print("Item 1 viewWillAppear")
    }
    
    override func viewWillDisappear(_ animated: Bool) { // view 곧 사라질 때 호출
        super.viewWillDisappear(animated)
        
        print("Item 1 viewWillDisappear")
    }
    
    override func viewDidAppear(_ animated: Bool) { // view 가 나타나면 호출
        super.viewDidAppear(animated)
        
        print("Item 1 viewDidAppear")
    }
    
    override func viewDidDisappear(_ animated: Bool) {  // view 가 사라지면 호출
        super.viewDidDisappear(animated)
        
        print("Item 1 viewDidDisappear")
    }

    deinit {
        print("Item 1 deinit") // view 가 소멸 되면 호출
    }
}

```

#### Item2ViewController
```
//
//  Item2ViewController.swift
//  0705_TabBar
//
//  Created by 임건우 on 2018. 7. 5..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class Item2ViewController: UIViewController {

    @IBOutlet weak var RedRGB: UISlider!
    @IBOutlet weak var GreenRGB: UISlider!
    @IBOutlet weak var BlueRGB: UISlider!
    
    override func viewDidLoad() {
        super.viewDidLoad()

        print("Item 2 viewDidLoad")
        // Do any additional setup after loading the view.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        
        print("Item 2 viewWillAppear")
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        
        print("Item 2 viewWillDisappear")
    }
    
    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        
        print("Item 2 viewDidAppear")
    }
    
    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        
        print("Item 2 viewDidDisappear")
    }
    
    @IBAction func SetColor(_ sender: Any) {
        print("Send Color")
        print(RedRGB.value)
        print(GreenRGB.value)
        print(BlueRGB.value)
        
        let myUserInfo = ["Red":[CGFloat(RedRGB.value), CGFloat(GreenRGB.value), CGFloat(BlueRGB.value)]]
        
        NotificationCenter.default.post(name: Item3Noti, object: nil, userInfo: myUserInfo)
        // NotificationCenter 의 Item3Noti 에 userInfo 를 통해 데이터를 전달

    }
    
    deinit {
        print("Item 2 deinit")
    }

}

```

#### Item3ViewController
```
//
//  Item3ViewController.swift
//  0705_TabBar
//
//  Created by 임건우 on 2018. 7. 5..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

let Item3Noti = Notification.Name("Item3Noti") // 전역 변수로 사용 하는 것은 좋지 않음

/* 아래의 방법을 추천
extension Notification.Name{
    static let myNotification = Notification.Name.init("myNotification")
}
*/

class Item3ViewController: UIViewController {
    @IBOutlet weak var myView: UIView!
    
    override func viewDidLoad() {
        super.viewDidLoad()

        
        NotificationCenter.default.addObserver(
            self,
            selector: #selector(changeColor(_:)),
            name: Item3Noti,
            object: nil
        )
        
        print("Item 3 viewDidLoad")
        // Do any additional setup after loading the view.
    }
    
    @objc func changeColor(_ noti: Notification){
        print("change color")
        
        let myColor = noti.userInfo!["Red"]! as! Array<CGFloat>
        myView.backgroundColor = UIColor(red: myColor[0], green: myColor[1], blue: myColor[2], alpha: 1)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        
        print("Item 3 viewWillAppear")
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        
        print("Item 3 viewWillDisappear")
    }
    
    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        
        print("Item 3 viewDidAppear")
    }
    
    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        
        print("Item 3 viewDidDisappear")
    }
    
    deinit {
        print("Item 3 deinit")
    }

}

```
