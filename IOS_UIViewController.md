# UI View Controller 

### Simple Example

##### ViewController
```
//
//  ViewController.swift
//  Class0604_1
//
//  Created by 임건우 on 2018. 6. 4..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    
    lazy var textLabel2 = UILabel(frame: CGRect(x: view.frame.maxX/2 - view.frame.maxX/4, y: view.frame.maxY/2, width: view.frame.maxX/2, height: 50))
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        
        let nextButton = UIButton(frame: CGRect(x: view.frame.maxX-100, y: view.frame.maxY-100, width: 100, height: 50))
        nextButton.backgroundColor = .black
        nextButton.setTitle("next", for: .normal)
        nextButton.setTitleColor(.white, for: .normal)
        nextButton.addTarget(self, action: #selector(showNextView), for: .touchUpInside)
        
        view.addSubview(nextButton)
        
        let textLabel = UILabel(frame: CGRect(x: view.frame.maxX/2 - view.frame.maxX/4, y: view.frame.maxY/2 - view.frame.maxY/4, width: view.frame.maxX/2, height: 50))
        textLabel.text = "First View"
        textLabel.textColor = .white
        textLabel.backgroundColor = .black
        textLabel.textAlignment = .center
        
        view.addSubview(textLabel)
        
        textLabel2.text = "0"
        textLabel2.textColor = .white
        textLabel2.backgroundColor = .black
        textLabel2.textAlignment = .center
        
        
        view.addSubview(textLabel2)
        
        
        // Do any additional setup after loading the view, typically from a nib.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    @objc func showNextView(){
        let secondViewController = SecondViewController()
        
        present(secondViewController, animated: true){
            print("next view load")
            secondViewController.textLabel2.text = "changed text"
        }
    }

    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        print("Did Appear")
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        print("Will Appear")
    }
    
    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        print("Did Disappear")
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        print("Will Disappear")
    }

}


```


##### SecondViewController
```
//
//  SecondViewController.swift
//  Class0604_1
//
//  Created by 임건우 on 2018. 6. 4..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class SecondViewController: UIViewController {
    
    lazy var textLabel2 = UILabel(frame: CGRect(x: view.frame.maxX/2 - view.frame.maxX/4, y: view.frame.maxY/2, width: view.frame.maxX/2, height: 50))
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .cyan
        
        let nextButton = UIButton(frame: CGRect(x: view.frame.maxX-100, y: view.frame.maxY-100, width: 100, height: 50))
        nextButton.backgroundColor = .black
        nextButton.setTitle("next", for: .normal)
        nextButton.setTitleColor(.white, for: .normal)
        nextButton.addTarget(self, action: #selector(showNextView), for: .touchUpInside)
        
        view.addSubview(nextButton)
        
        let dismissButton = UIButton(frame: CGRect(x: view.frame.minX, y: view.frame.minY+15, width: 100, height: 50))
        dismissButton.backgroundColor = .black
        dismissButton.setTitle("Back", for: .normal)
        dismissButton.setTitleColor(.white, for: .normal)
        dismissButton.addTarget(self, action: #selector(dismissView), for: .touchUpInside)
        
        view.addSubview(dismissButton)
        
        let textLabel = UILabel(frame: CGRect(x: view.frame.maxX/2 - view.frame.maxX/4, y: view.frame.maxY/2 - view.frame.maxY/4, width: view.frame.maxX/2, height: 50))
        textLabel.text = "Second View"
        textLabel.textColor = .white
        textLabel.backgroundColor = .black
        textLabel.textAlignment = .center
        
        
        view.addSubview(textLabel)
        

        textLabel2.text = "Second View"
        textLabel2.textColor = .white
        textLabel2.backgroundColor = .black
        textLabel2.textAlignment = .center
        
        
        view.addSubview(textLabel2)
        
        
        // Do any additional setup after loading the view.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    
    @objc func showNextView(){
        let thirdViewController = ThirdViewController()
        
        present(thirdViewController, animated: true){
            print("next view load")
        }
    }
    
    @objc func dismissView(){
        guard let viewController = presentingViewController as? ViewController,
            let text = viewController.textLabel2.text,
            let count = Int(text)
            else{ return }
        viewController.textLabel2.text = "\(count + 1)"
        
        dismiss(animated: true){
            print("Dismiss Second View Controller")
        }
    }
    
    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        print("Did Appear 2")
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        print("Will Appear 2")
    }
    
    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        print("Did Disappear 2")
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        print("Will Disappear 2")
    }
    
    deinit {
        print("2 view exit")
    }
    
}

```

##### ThirdViewController
```
//
//  ThirdViewController.swift
//  Class0604_1
//
//  Created by 임건우 on 2018. 6. 4..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ThirdViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        view.backgroundColor = .green
        
        let dismissButton = UIButton(frame: CGRect(x: view.frame.minX, y: view.frame.minY+15, width: 100, height: 50))
        dismissButton.backgroundColor = .black
        dismissButton.setTitle("Back", for: .normal)
        dismissButton.setTitleColor(.white, for: .normal)
        dismissButton.addTarget(self, action: #selector(dismissView), for: .touchUpInside)
        
        view.addSubview(dismissButton)
        
        let dismissButton2 = UIButton(frame: CGRect(x: view.frame.maxX-100, y: view.frame.minY+15, width: 100, height: 50))
        dismissButton2.backgroundColor = .black
        dismissButton2.setTitle("Go First", for: .normal)
        dismissButton2.setTitleColor(.white, for: .normal)
        dismissButton2.addTarget(self, action: #selector(dismissView2), for: .touchUpInside)
        
        view.addSubview(dismissButton2)
        
        let textLabel = UILabel(frame: CGRect(x: view.frame.maxX/2 - view.frame.maxX/4, y: view.frame.maxY/2 - view.frame.maxY/4, width: view.frame.maxX/2, height: 50))
        textLabel.text = "Third View"
        textLabel.textColor = .white
        textLabel.textAlignment = .center
        textLabel.backgroundColor = .black
        
        view.addSubview(textLabel)
        
        
        
        // Do any additional setup after loading the view.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    @objc func dismissView(){
        dismiss(animated: true){
            print("Dismiss Third View Controller")
        }
    }
    
    @objc func dismissView2(){
        presentingViewController?.presentingViewController?.dismiss(animated: true){
            print("ting ting dismiss")
        }
    }
    
    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        print("Did Appear 3")
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        print("Will Appear 3")
    }
    
    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        print("Did Disappear 3")
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        print("Will Disappear 3")
    }

    deinit {
        print("3 view exit")
    }

}

```
