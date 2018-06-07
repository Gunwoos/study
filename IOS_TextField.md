### ViewController

```
//
//  ViewController.swift
//  Class0606
//
//  Created by 임건우 on 2018. 6. 6..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    lazy var textLabel = UILabel(frame: makeFrame(view.frame.minX+15, view.frame.minY+100, view.frame.width-30, 30))
    lazy var textField = UITextField(frame: makeFrame(view.frame.minX+15, view.frame.minY + 200, view.frame.width-30, 30))
    
    class singleText{
        static let shared = singleText()
        var getText : String = ""
    }
    
    let newSingleText = singleText.shared
    
    var userDefaultText = ""
    let userDefault = UserDefaults.standard
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        
        
        textLabel.backgroundColor = .white
        textLabel.textAlignment = .center
        textLabel.text = "여기에 입력 됩니다"
        textLabel.textColor = .red
        
        view.addSubview(textLabel)
        
        textField.backgroundColor = .cyan
        textField.textAlignment = .center
        textField.placeholder = "입력하시오"
        textField.addTarget(self, action: #selector(blueText), for: UIControlEvents.editingDidBegin)
        textField.addTarget(self, action: #selector(setText), for: UIControlEvents.editingChanged)
        textField.addTarget(self, action: #selector(redText), for: UIControlEvents.editingDidEnd)
        textField.addTarget(self, action: #selector(exitTextField), for: UIControlEvents.editingDidEndOnExit)
        
        view.addSubview(textField)
        
        let saveButton = UIButton(frame: makeFrame(view.frame.width/2 - 50, view.frame.minY + 300, 100, 30))
        saveButton.backgroundColor = .white
        saveButton.setTitleColor(.blue, for: .normal)
        saveButton.setTitle("Save", for: .normal)
        saveButton.setTitleColor(.red, for: .highlighted)
        saveButton.addTarget(self, action: #selector(nextView), for: .touchUpInside)
        
        view.addSubview(saveButton)
        
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    @objc func nextView(){
        let nextView = NextViewController()
        
        present(nextView, animated: true){
            nextView.textLabel2.text = self.textLabel.text // 직접 설정 해주기
            
            nextView.changeText() // singleTon
            
            nextView.textLabel4.text = "\(self.userDefaultText)" // userDefaults
        }
        
    }
    
    @objc func makeFrame(_ num1 : CGFloat ,_ num2 : CGFloat ,_ num3 : CGFloat,_ num4 : CGFloat) -> CGRect{
        return CGRect(x: num1, y: num2, width: num3, height: num4)
    }
    
    @objc func blueText(){
        self.textLabel.textColor = .blue
    }
    
    @objc func redText(){
        self.textLabel.textColor = .red
    }
    
    @objc func exitTextField(){
    }
    
    @objc func setText(){
        self.textLabel.text = self.textField.text
        
        newSingleText.getText = self.textLabel.text!
        
        self.userDefaultText = self.textLabel.text!
        userDefault.set(userDefaultText, forKey: "TextKey")
    }



}

```

### NextViewController
```
//
//  NextViewController.swift
//  Class0606
//
//  Created by 임건우 on 2018. 6. 6..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class NextViewController: UIViewController {
    
    lazy var textLabel2 = UILabel(frame: makeFrame(view.frame.minX+15, view.frame.minY+200, view.frame.width-30, 30))
    
    lazy var textLabel3 = UILabel(frame: makeFrame(view.frame.minX+15, view.frame.minY+300, view.frame.width-30, 30))
    
    lazy var textLabel4 = UILabel(frame: makeFrame(view.frame.minX+15, view.frame.minY+400, view.frame.width-30, 30))

    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.modalTransitionStyle = .crossDissolve
        view.backgroundColor = .white
    
        let textLabel = UILabel(frame: makeFrame(view.frame.minX+15, view.frame.minY+100, view.frame.width-30, 30))
        textLabel.backgroundColor = .orange
        textLabel.textAlignment = .center
        textLabel.text = "New View"
        
        view.addSubview(textLabel)
        
        
        textLabel2.backgroundColor = .cyan
        textLabel2.textAlignment = .center
        textLabel2.text = ""
        
        view.addSubview(textLabel2)
        
        textLabel3.backgroundColor = .cyan
        textLabel3.textAlignment = .center
        textLabel3.text = ""
        
        view.addSubview(textLabel3)
        
        textLabel4.backgroundColor = .cyan
        textLabel4.textAlignment = .center
        textLabel4.text = ""
        
        view.addSubview(textLabel4)
        
        let backButton = UIButton(frame: makeFrame(view.frame.width/2 - 50, view.frame.minY + 500, 100, 30))
        backButton.backgroundColor = .white
        backButton.setTitleColor(.blue, for: .normal)
        backButton.setTitleColor(.red, for: .highlighted)
        backButton.setTitle("Back", for: .normal)
        backButton.addTarget(self, action: #selector(disMissThisView), for: .touchUpInside)
        
        view.addSubview(backButton)
    
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    @objc func disMissThisView(){
        dismiss(animated: true)
    }
    
    @objc func makeFrame(_ num1 : CGFloat ,_ num2 : CGFloat ,_ num3 : CGFloat,_ num4 : CGFloat) -> CGRect{
        return CGRect(x: num1, y: num2, width: num3, height: num4)
    }

    @objc func changeText(){
        guard let preViewController = presentingViewController as? ViewController else{ return }
        textLabel3.text = preViewController.newSingleText.getText
        
        
    }
    

}
```
