### ViewController.swift

```
//
//  ViewController.swift
//  Class0626_01
//
//  Created by 임건우 on 2018. 6. 26..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    @IBOutlet weak var goodByeKermit: UIImageView!
    var lastTouchPoint = CGPoint.zero
    
    override func viewDidLoad() {
        super.viewDidLoad()
        goodByeKermit.layer.cornerRadius = goodByeKermit.frame.width/2
        goodByeKermit.layer.masksToBounds = true
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        super.touchesBegan(touches, with: event)
        guard let touch = touches.first else { return }
        let touchPoint = touch.location(in: touch.view)
        
        lastTouchPoint = touchPoint
        if goodByeKermit.frame.contains(touchPoint){
            goodByeKermit.image = UIImage(named: "Kermit_Sick")
        }
    }
    
    override func touchesEnded(_ touches: Set<UITouch>, with event: UIEvent?) {
        super.touchesEnded(touches, with: event)
        goodByeKermit.image = UIImage(named: "Kermit_Goodbye")
    }

    override func touchesCancelled(_ touches: Set<UITouch>, with event: UIEvent?) {
        super.touchesCancelled(touches, with: event)
        goodByeKermit.image = UIImage(named: "Kermit_Sick")
    }
    override func touchesMoved(_ touches: Set<UITouch>, with event: UIEvent?) {
        super.touchesMoved(touches, with: event)
        guard let touch = touches.first else { return }
        let touchPoint = touch.location(in: touch.view)
        
        if goodByeKermit.frame.contains(touchPoint){
//            goodByeKermit.center = touchPoint
            goodByeKermit.frame.origin = CGPoint(
                x: touchPoint.x - goodByeKermit.frame.width/2,
                y: touchPoint.y - goodByeKermit.frame.height/2
            )
            lastTouchPoint = touchPoint
            
        }
    }
}


```

###  GuestureViewController.swift

```
//
//  GuestureViewController.swift
//  Class0626_01
//
//  Created by 임건우 on 2018. 6. 26..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class GuestureViewController: UIViewController {

    @IBOutlet weak var sickKermit: UIImageView!
    var imageMax = true
    
    override func viewDidLoad() {
        super.viewDidLoad()
        

        sickKermit.layer.cornerRadius = sickKermit.frame.width/2 // 비율이 1:1 인 경우
        sickKermit.layer.masksToBounds = true
    }

 
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
 
    }
    @IBAction func RotationGesture(_ sender: UIRotationGestureRecognizer) {
        let rotation = sender.rotation
        sickKermit.transform = sickKermit.transform.rotated(by: rotation)
        print("rotation : \(rotation)")
        if rotation > 0 {
            sickKermit.image = UIImage(named: "Kermit_Sick")
        }
        else{
            sickKermit.image = UIImage(named: "Kermit_Goodbye")
        }
        

//        print("velocity : \(velocity)")
//        sickKermit.transform = sickKermit.transform.scaledBy(x: velocity, y: velocity)
        
        sender.rotation = 0
    }
    
    @IBAction func PanGesture(_ sender: UIPanGestureRecognizer) {
        let touchPoint = sender.location(in: sender.view)
        
        sickKermit.center = touchPoint
    }
    
    @IBAction func PinchGesture(_ sender: UIPinchGestureRecognizer) {
        let scale = sender.scale
        print("scale : \(scale)")
        if scale > 0.5 , scale < 2.0 {
            sickKermit.transform = sickKermit.transform.scaledBy(x: scale, y: scale)
        }
        
    }
    
    @IBAction func tapGesture(_ sender: UITapGestureRecognizer) {
        if imageMax {
            sickKermit.transform = sickKermit.transform.scaledBy(x: 2.0, y: 2.0)
        }
        else{
            sickKermit.transform = CGAffineTransform.identity
        }
        imageMax = !imageMax
    }
}

```
