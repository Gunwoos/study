# Button and Action
---
- 버튼 2개를 만들어 하나의 버튼을 클릭시 다른 버튼에 클릭 횟수를 +1 증가시키기
```
//
//  ViewController.swift
//  Class0528_1
//
//  Created by 임건우 on 2018. 5. 28..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

var checkColor = 1
var clickedNum = 0

class ViewController: UIViewController {

//    @IBOutlet weak var button: UIButton!
//    @IBAction func buttonDipTap(_ sender: UIButton) {
//        print("button Dip Tap")
//        button.backgroundColor = .red
//    }
    var newButton = UIButton(frame: CGRect(x: 100, y: 100, width: 200, height: 200))
    
    var numButton2 = UIButton(frame: CGRect(x: 100, y: 400, width: 200, height: 200))
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
//        button.backgroundColor = .black
//        button.setTitleColor(UIColor.cyan, for: .normal)
        
        // 버튼 1 생성
        newButton.backgroundColor = UIColor.black
        newButton.setTitle("Click", for: .normal)
        newButton.setTitleColor(UIColor.cyan, for: .normal)
        newButton.addTarget(self, action: #selector(buttonClicked ), for: .touchUpInside)
        view.addSubview(newButton)
        
        //버튼 2 생성
        numButton2.backgroundColor = UIColor.green
        numButton2.setTitle("clicked : \(clickedNum)", for: .normal)
        numButton2.setTitleColor(.blue, for: .normal)
        numButton2.addTarget(self, action: #selector(clickedNumReset), for: .touchUpInside)
        view.addSubview(numButton2)
        
    }
    
//    @objc func setButton(buttonName : String, backgroundColor : UIColor, title : String, titleColor : UIColor ){
//        self.buttonName.backgroundColor = backgroundColor
//
//    }
    
    @objc func buttonClicked(){ // 첫번째 버튼 클릭 시 생기는 액션
        
        print("button clicked")
        // 첫번째 버튼을 클릭 시 첫번째 버튼 배경색, 글자색 변경 코드
        if checkColor == 1 {
            checkColor = 0
            self.newButton.backgroundColor = .cyan
            self.newButton.setTitleColor(UIColor.black, for: .normal)
        }
        else{
            checkColor = 1
            self.newButton.backgroundColor = .black
            self.newButton.setTitleColor((UIColor.cyan), for: .normal)
        }
        // 클릭된 횟수 +1 후 버튼2의 텍스트 초기화
        clickedNum += 1
        numButton2.setTitle("clicked : \(clickedNum)", for: .normal)
    }
    
    @objc func clickedNumReset(){ // 두번째 버튼의 클릭된 횟수 변수 초기화
        clickedNum = 0
        numButton2.setTitle("clicked : \(clickedNum)", for: .normal)
    }
    
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
}
```
