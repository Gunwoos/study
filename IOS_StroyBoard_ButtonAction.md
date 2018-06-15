
### ViewController

```
//
//  ViewController.swift
//  practice_ButtonAction
//
//  Created by 임건우 on 2018. 6. 15..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    var num = 1
    
    override func viewDidLoad() {
        super.viewDidLoad()

    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()

    }

    @IBAction func AddNumOne(_ sender: UIButton) {
        num += 1
        self.SetLabel.text = String(num)
    }
    
    @IBOutlet weak var SetLabel: UILabel!
}


```
