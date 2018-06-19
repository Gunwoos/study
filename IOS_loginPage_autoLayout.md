# ViewController
- [IPhone](https://user-images.githubusercontent.com/39073993/41592317-267015ae-73f7-11e8-8a43-60d1ae917e79.png)
```
//
//  ViewController.swift
//  Class0619_scrollview_3
//
//  Created by 임건우 on 2018. 6. 19..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    private let imageView = UIImageView()
    private let loginView = UIView()
    
    private let IdImage = UIImageView()
    private let PwImage = UIImageView()
    
    private let IdTextField = UITextField()
    private let PwTextField = UITextField()
    
    private let loginButton = UIButton()
    
    private let margin : CGFloat = 20
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        imageView.image = #imageLiteral(resourceName: "The-Muppets-Kermit")
        imageView.contentMode = .scaleToFill
        
        view.addSubview(imageView)
        
        loginView.backgroundColor = .green
        
        view.addSubview(loginView)
        
        IdImage.image = #imageLiteral(resourceName: "userIcon")
        IdImage.contentMode = .scaleToFill
        IdImage.backgroundColor = .white
        IdImage.layer.borderWidth = 1
        IdImage.layer.borderColor = UIColor.black.cgColor
        
        PwImage.image = #imageLiteral(resourceName: "passwordIcon")
        PwImage.contentMode = .scaleToFill
        PwImage.backgroundColor = .white
        PwImage.layer.borderWidth = 1
        PwImage.layer.borderColor = UIColor.black.cgColor
        
        IdTextField.placeholder = "ID 를 입력하시오"
        IdTextField.textAlignment = .center
        IdTextField.backgroundColor = .white
        IdTextField.layer.borderWidth = 1
        IdTextField.layer.borderColor = UIColor.black.cgColor
        
        PwTextField.placeholder = "Password 를 입력하시오"
        PwTextField.textAlignment = .center
        PwTextField.backgroundColor = .white
        PwTextField.layer.borderWidth = 1
        PwTextField.layer.borderColor = UIColor.black.cgColor
        
        loginButton.backgroundColor = .green
        loginButton.layer.borderWidth = 1
        loginButton.layer.borderColor = UIColor.black.cgColor
        loginButton.setTitle("login", for: .normal)
        loginButton.setTitleColor(.black, for: .normal)
        loginButton.setTitleColor(.blue, for: .highlighted)
        
        
        
        loginView.addSubview(IdImage)
        loginView.addSubview(PwImage)
        loginView.addSubview(IdTextField)
        loginView.addSubview(PwTextField)
        loginView.addSubview(loginButton)

    }
    
    override func viewWillLayoutSubviews() {
        super.viewWillLayoutSubviews()
        
        let safeLayoutInsets = view.safeAreaInsets
        let horizontalInset = safeLayoutInsets.left + safeLayoutInsets.right
        let verticalInset = safeLayoutInsets.top + safeLayoutInsets.bottom
        
        let yOffset = safeLayoutInsets.top + margin
        let viewHeight = (view.bounds.height - verticalInset - 3*margin)/2
        
        imageView.frame = CGRect(
            x: safeLayoutInsets.left + margin,
            y: yOffset,
            width: view.bounds.width - horizontalInset - (margin*2),
            height: viewHeight
        )
        
        loginView.frame = CGRect(
            origin: CGPoint(x: imageView.frame.minX, y: imageView.frame.maxY+margin),
            size: imageView.bounds.size
        )
        
        makeFrame()
    }
    
    func makeFrame(){
        IdImage.translatesAutoresizingMaskIntoConstraints = false
        PwImage.translatesAutoresizingMaskIntoConstraints = false
        IdTextField.translatesAutoresizingMaskIntoConstraints = false
        PwTextField.translatesAutoresizingMaskIntoConstraints = false
        loginButton.translatesAutoresizingMaskIntoConstraints = false
    
        IdImage.topAnchor.constraint(equalTo: loginView.topAnchor, constant: margin).isActive = true
        IdImage.leadingAnchor.constraint(equalTo: loginView.leadingAnchor, constant: margin).isActive = true
        IdImage.widthAnchor.constraint(equalToConstant: (loginView.bounds.maxY-(margin*4))/3).isActive = true
        IdImage.heightAnchor.constraint(equalToConstant: (loginView.bounds.maxY-(margin*4))/3).isActive = true
        
        IdTextField.topAnchor.constraint(equalTo: loginView.topAnchor, constant: margin).isActive = true
        IdTextField.trailingAnchor.constraint(equalTo: loginView.trailingAnchor, constant: -margin).isActive = true
        IdTextField.leadingAnchor.constraint(equalTo: IdImage.trailingAnchor, constant: margin).isActive = true
        IdTextField.heightAnchor.constraint(equalToConstant: (loginView.bounds.maxY-(margin*4))/3).isActive = true

        PwImage.topAnchor.constraint(equalTo: IdImage.bottomAnchor, constant: margin).isActive = true
        PwImage.leadingAnchor.constraint(equalTo: loginView.leadingAnchor, constant: margin).isActive = true
        PwImage.widthAnchor.constraint(equalToConstant: (loginView.bounds.maxY-(margin*4))/3).isActive = true
        PwImage.heightAnchor.constraint(equalToConstant: (loginView.bounds.maxY-(margin*4))/3).isActive = true
        
        PwTextField.topAnchor.constraint(equalTo: IdTextField.bottomAnchor, constant: margin).isActive = true
        PwTextField.leadingAnchor.constraint(equalTo: PwImage.trailingAnchor, constant: margin).isActive = true
        PwTextField.trailingAnchor.constraint(equalTo: loginView.trailingAnchor, constant: -margin).isActive = true
        PwTextField.heightAnchor.constraint(equalToConstant: (loginView.bounds.maxY-(margin*4))/3).isActive = true
        
        loginButton.topAnchor.constraint(equalTo: PwImage.bottomAnchor, constant: margin).isActive = true
        loginButton.bottomAnchor.constraint(equalTo: loginView.bottomAnchor, constant: -margin).isActive = true
        loginButton.leadingAnchor.constraint(equalTo: loginView.leadingAnchor, constant: margin*2).isActive = true
        loginButton.trailingAnchor.constraint(equalTo: loginView.trailingAnchor,constant: -margin*2).isActive = true
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()

    }


}


```

