### ViewController

```
//
//  ViewController.swift
//  Class0618
//
//  Created by 임건우 on 2018. 6. 18..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    let cyanView = UIView()
    let greenView = UIView()
    let cyanViewMargin : CGFloat = 50
    let greenViewMargin : CGFloat = 50

    override func viewDidLoad() {
        super.viewDidLoad()
        
        cyanView.backgroundColor = .cyan
        greenView.backgroundColor = .green
        
        view.addSubview(cyanView)
        cyanView.addSubview(greenView)
        
//        NSLayout()
        autoLayout()
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()

    }
    
    private func NSLayout(){
        cyanView.translatesAutoresizingMaskIntoConstraints = false
        greenView.translatesAutoresizingMaskIntoConstraints = false
        
        NSLayoutConstraint(item: self.cyanView, attribute: .top, relatedBy: .equal, toItem: view, attribute: .top, multiplier: 1, constant: cyanViewMargin).isActive = true
        NSLayoutConstraint(item: self.cyanView, attribute: .leading, relatedBy: .equal, toItem: view, attribute: .leading, multiplier: 1, constant: cyanViewMargin).isActive = true
        NSLayoutConstraint(item: view, attribute: .trailing , relatedBy: .equal, toItem: self.cyanView, attribute: .trailing, multiplier: 1, constant: cyanViewMargin).isActive = true
        NSLayoutConstraint(item: view, attribute: .bottom, relatedBy: .equal, toItem: self.cyanView, attribute: .bottom, multiplier: 1, constant: cyanViewMargin).isActive = true
        
        
        NSLayoutConstraint(item: self.greenView, attribute: .top, relatedBy: .equal, toItem: self.cyanView, attribute: .top, multiplier: 1, constant: greenViewMargin).isActive = true
        NSLayoutConstraint(item: self.greenView, attribute: .leading, relatedBy: .equal, toItem: self.cyanView, attribute: .leading, multiplier: 1, constant: greenViewMargin).isActive = true
        NSLayoutConstraint(item: self.cyanView, attribute: .trailing, relatedBy: .equal, toItem: self.greenView, attribute: .trailing, multiplier: 1, constant: greenViewMargin).isActive = true
        NSLayoutConstraint(item: self.cyanView, attribute: .bottom, relatedBy: .equal, toItem: self.greenView, attribute: .bottom, multiplier: 1, constant: greenViewMargin).isActive = true

    }
    
    private func autoLayout(){
        cyanView.translatesAutoresizingMaskIntoConstraints = false
        greenView.translatesAutoresizingMaskIntoConstraints = false
        
        cyanView.topAnchor.constraint(equalTo: view.topAnchor, constant: cyanViewMargin).isActive = true
        cyanView.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: cyanViewMargin).isActive = true
        cyanView.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -cyanViewMargin).isActive = true
        cyanView.bottomAnchor.constraint(equalTo: view.bottomAnchor, constant: -cyanViewMargin).isActive = true
        
        greenView.topAnchor.constraint(equalTo: cyanView.topAnchor, constant: greenViewMargin).isActive = true
        greenView.leadingAnchor.constraint(equalTo: cyanView.leadingAnchor, constant: greenViewMargin).isActive = true
        greenView.trailingAnchor.constraint(equalTo: cyanView.trailingAnchor, constant: -greenViewMargin).isActive = true
        greenView.bottomAnchor.constraint(equalTo: cyanView.bottomAnchor, constant: -greenViewMargin).isActive = true
        
    }
}
```
