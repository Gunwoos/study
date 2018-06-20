

### ViewController
```
//
//  ViewController.swift
//  Class0620_practice_2
//
//  Created by 임건우 on 2018. 6. 20..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

final class ViewController: UIViewController {
    
    // MARK: Properties
    private let margin : CGFloat = 20
    private let pageControl = UIPageControl()
    private let scrollView = UIScrollView()
    
    
    // MARK: LifeCycle
    
    override func viewDidLoad() {
        super.viewDidLoad()
       
        setUp()
    }
    
    private func setUp(){
        scrollView.frame = CGRect(x: 0, y: margin, width: view.frame.width, height: view.frame.height-margin*4)
        scrollView.backgroundColor = .black
        scrollView.isPagingEnabled = true
        scrollView.delegate = self
        
        view.addSubview(scrollView)
        
        let myColor : [UIColor] = [ .cyan , .green , .yellow]
        
        for i in myColor.startIndex...myColor.endIndex-1{
            makeView(myColor: myColor[i],myNum: CGFloat(i))
        }
        
        pageControl.frame = CGRect(x: view.frame.midX-margin, y: view.frame.maxY-margin, width: margin*2, height: margin)
        pageControl.layer.borderWidth = 1
        pageControl.layer.borderColor = UIColor.black.cgColor
        pageControl.backgroundColor = .black
        
        view.addSubview(pageControl)
    }
    
    private func makeView(myColor : UIColor, myNum : CGFloat){
        print("\(scrollView.frame.maxX) \(view.frame.width)")
        let getFrame = CGRect(x: scrollView.frame.maxX*myNum, y: 0, width: scrollView.frame.width, height: scrollView.frame.height)
        
        let newView = UIView(frame: getFrame)
        newView.backgroundColor = myColor
        
        scrollView.contentSize.width += newView.frame.width
        pageControl.numberOfPages += 1
        
        scrollView.addSubview(newView)
        
    }
}
extension ViewController : UIScrollViewDelegate{
    func scrollViewDidEndDecelerating(_ scrollView: UIScrollView) {
        let page = Int(scrollView.contentOffset.x / scrollView.frame.width)
        pageControl.currentPage = page
    }
}



```
