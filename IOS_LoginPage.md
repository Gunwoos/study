### ViewController
```
//
//  ViewController.swift
//  Class0607_1
//
//  Created by 임건우 on 2018. 6. 7..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    
    var memberList = ["abc123" : "abc123" , "asd123" : "asd123"]
    var newID = ""
    var newPassword = ""
    

    lazy var imageView = UIImageView(frame: getFrame(view.frame.minX + 20, view.frame.minY + 20, width: view.frame.width - 40, height: view.frame.width - 40))
    lazy var buttonView = UIView(frame: getFrame(imageView.frame.minX, imageView.frame.maxY + 5, width: imageView.frame.width, height: imageView.frame.width))
    lazy var idTextField = UITextField(frame: getFrame(view.frame.minX + 60, view.frame.minY + 10, width: 300, height: 30))
    lazy var passwordTextField = UITextField(frame: getFrame(view.frame.minX + 60, view.frame.minY + 50, width: 300, height: 30))
    func showLogin(){
        let myPageViewController = MyPageViewController()
        
        present(myPageViewController, animated: true)
    }
    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.modalTransitionStyle = .crossDissolve
        view.backgroundColor = .white
        
        
        imageView.image = #imageLiteral(resourceName: "FastCampus_Logo-2.png")
        imageView.contentMode = .scaleAspectFit
        
        view.addSubview(imageView)
        
        view.addSubview(buttonView)
        
        let idView = UIImageView(frame: getFrame(view.frame.minX + 20, view.frame.minY + 10, width: 30, height: 30))
        idView.image = #imageLiteral(resourceName: "userIcon.png")
        idView.contentMode = .scaleToFill
        
        buttonView.addSubview(idView)
        
        let passwordView = UIImageView(frame: getFrame(view.frame.minX + 20, view.frame.minY + 50, width: 30, height: 30))
        passwordView.image = #imageLiteral(resourceName: "passwordIcon.png")
        passwordView.contentMode = .scaleToFill
        
        buttonView.addSubview(passwordView)
        
    
        idTextField.placeholder = "ID 를 입력하시오"
        idTextField.textAlignment = .center
        idTextField.layer.cornerRadius = 5
        idTextField.backgroundColor = UIColor.lightGray
        idTextField.addTarget(self, action: #selector(getID), for: .editingChanged)
        idTextField.addTarget(self, action: #selector(doneID), for: .editingDidEndOnExit)
        
        buttonView.addSubview(idTextField)
        
    
        passwordTextField.backgroundColor = .lightGray
        passwordTextField.layer.cornerRadius = 5
        passwordTextField.placeholder = "password 를 입력하시오"
        passwordTextField.textAlignment = .center
        passwordTextField.isSecureTextEntry = true
        passwordTextField.addTarget(self, action: #selector(getPassword), for: .editingChanged)
        passwordTextField.addTarget(self, action: #selector(donePassword), for: .editingDidEndOnExit)
        
        buttonView.addSubview(passwordTextField)
        
        let loginButton = UIButton(frame: getFrame(view.frame.minX + 150, view.frame.minY + 100, width: 100, height: 30))
        loginButton.backgroundColor = .white
        loginButton.setTitleColor(.black, for: .normal)
        loginButton.setTitleColor(.blue, for: .highlighted)
        loginButton.setTitle("Login", for: .normal)
        loginButton.layer.borderWidth = 2
        loginButton.layer.cornerRadius = 5
        loginButton.layer.borderColor = UIColor.black.cgColor
        loginButton.addTarget(self, action: #selector(checkID), for: .touchUpInside)
        
        buttonView.addSubview(loginButton)
        
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

    @objc func getFrame(_ x: CGFloat, _ y : CGFloat, width : CGFloat, height : CGFloat) -> CGRect{
        return CGRect(x: x, y: y, width: width, height: height)
    }
    

    @objc func getID(){
        self.buttonView.frame = CGRect(x: imageView.frame.minX, y: imageView.frame.maxY - 15, width: imageView.frame.width, height: imageView.frame.width)
        self.newID = self.idTextField.text!
    }
    
    @objc func doneID(){
        self.buttonView.frame = CGRect(x: imageView.frame.minX, y: imageView.frame.maxY + 5, width: imageView.frame.width, height: imageView.frame.width)
    }
    

    @objc func getPassword(){
        self.buttonView.frame = CGRect(x: imageView.frame.minX, y: imageView.frame.maxY - 15, width: imageView.frame.width, height: imageView.frame.width)

        self.newPassword = self.passwordTextField.text!
    }
    
    @objc func donePassword(){
        self.buttonView.frame = CGRect(x: imageView.frame.minX, y: imageView.frame.maxY + 5, width: imageView.frame.width, height: imageView.frame.width)
    }
    
    @objc func checkID(){
        if memberList[newID] == newPassword{
            print(" Login ")
//            let loginOkAlert = UIAlertController(title: "", message: "Login", preferredStyle: .alert)
//            let loginOKAction = UIAlertAction(title: "확인", style: .default)
//            loginOkAlert.addAction(loginOKAction)
//
//            self.present(loginOkAlert, animated: true)
            
            self.showLogin()
        }
        else{
            print("ID or Password Miss")
            let loginFailAlert = UIAlertController(title: "", message: "ID or Password Miss", preferredStyle: .alert)
            let loginFailAction = UIAlertAction(title: "OK", style: .default)
            loginFailAlert.addAction(loginFailAction)
            
            self.present(loginFailAlert, animated: true)
            
            self.idTextField.text = ""
            self.passwordTextField.text = ""
        }
    }
}
```

### MyPageViewController
```
//
//  MyPageViewController.swift
//  Class0607_1
//
//  Created by 임건우 on 2018. 6. 7..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class MyPageViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.modalTransitionStyle = .crossDissolve
        
        view.backgroundColor = .white
        
        
        let logOutButton = UIButton(frame: CGRect(x: view.frame.width/2-50, y: view.frame.width/2-50, width: 100, height: 30))
        logOutButton.setTitle("logout", for: .normal)
        logOutButton.setTitleColor(.black, for: .normal)
        logOutButton.setTitleColor(.blue, for: .highlighted)
        logOutButton.addTarget(self, action: #selector(logOutPage), for: .touchUpInside)
        
        view.addSubview(logOutButton)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    @objc func logOutPage(){
        dismiss(animated: true)
    }

}
```
