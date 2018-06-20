```
//
//  ViewController.swift
//  Class0620_practice
//
//  Created by 임건우 on 2018. 6. 20..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
    
        let scrollView = UIScrollView()

        scrollView.frame = CGRect(x: 0, y: 0, width: view.frame.width, height: view.frame.height)
        scrollView.contentSize = CGSize(width: view.bounds.width*4, height: view.bounds.height)
        scrollView.isPagingEnabled = true

        let firstView = UIView(frame: CGRect(x: scrollView.bounds.minX+view.bounds.width*2, y: scrollView.bounds.minY, width: view.bounds.width, height: view.bounds.height))
        let secondView = UIView(frame: CGRect(x: scrollView.bounds.minX+view.bounds.width, y: scrollView.bounds.minY, width: view.bounds.width, height: view.bounds.height))
        firstView.backgroundColor = .cyan
        secondView.backgroundColor = .green


        view.addSubview(scrollView)

        scrollView.addSubview(firstView)
        scrollView.addSubview(secondView)
        
        let kermit = UIImageView()
        kermit.image = #imageLiteral(resourceName: "The-Muppets-Kermit")
        kermit.frame = CGRect(x: 0, y: 0, width: view.frame.width, height: view.frame.height)
        kermit.contentMode = .scaleToFill
        
        scrollView.addSubview(kermit)
        
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()

    }


}

```
