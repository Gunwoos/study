# 계산기 만들기
```
//
//  ViewController.swift
//  Class0601
//
//  Created by 임건우 on 2018. 6. 1..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    let resultLabel = UILabel(frame: CGRect(x: 15, y: 30, width: Int(UIScreen.main.bounds.width)-30, height: Int(UIScreen.main.bounds.height)/4))
    
    var resultNum = 0 {
        didSet{
            resultLabel.text = " \(resultNum) "
        }
    }
    var countResultNum = 0
    
    var num1 : Int = 0
    var num2 : Int = 0
    var str1 : String = ""
    var str2 : String = ""
    
    var numArray : Array<Int> = []

    var sum1 : Int = 0
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let calView = UIView(frame: CGRect(x: 0, y: 15, width: Int(view.frame.width), height: Int(view.frame.height)-15))
        calView.backgroundColor = .black
        
        resultLabel.backgroundColor = .black
        resultLabel.text = "0"
        resultLabel.textColor = .white
        resultLabel.font = UIFont.boldSystemFont(ofSize: 100)
        resultLabel.textAlignment = .right
        
        
        let clearButton = makeButton(xline: 0, yline: 2, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.lightGray)
        clearButton.setTitleColor(UIColor.black, for: .normal)
        let absoluteButton = makeButton(xline: 1, yline: 2, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.lightGray)
        absoluteButton.setTitleColor(UIColor.black, for: .normal)
        let remainderButton = makeButton(xline: 2, yline: 2, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.lightGray)
        remainderButton.setTitleColor(UIColor.black, for: .normal)
        
        let divideButton = makeButton(xline: 3, yline: 2, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.orange)
        let num7Button = makeButton(xline: 0, yline: 3, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let num8Button = makeButton(xline: 1, yline: 3, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let num9Button = makeButton(xline: 2, yline: 3, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let multiplyButton = makeButton(xline: 3, yline: 3, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.orange)
        let num4Button = makeButton(xline: 0, yline: 4, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let num5Button = makeButton(xline: 1, yline: 4, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let num6Button = makeButton(xline: 2, yline: 4, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let subtractionButton = makeButton(xline: 3, yline: 4, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.orange)
        let num1Button = makeButton(xline: 0, yline: 5, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let num2Button = makeButton(xline: 1, yline: 5, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let num3Button = makeButton(xline: 2, yline: 5, frame: CGRect(x: 0, y: 0, width: 0, height: 0))
        let additionButton = makeButton(xline: 3, yline: 5, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.orange)
        let num0Button = UIButton(frame: CGRect(x: 0, y: Int(view.frame.minY)+(Int(view.frame.width)/4*6), width: Int(view.frame.width)/2, height: Int(view.frame.width)/4))
        num0Button.backgroundColor = .darkGray
        num0Button.layer.cornerRadius = 50

        let getButton = makeButton(xline: 3, yline: 6, frame: CGRect(x: 0, y: 0, width: 0, height: 0),.orange)
        let dotButton = makeButton(xline: 2, yline: 6, frame: CGRect(x: 0, y: 0, width: 0, height: 0), .darkGray)
        
        clearButton.setTitle("C", for: .normal)
        absoluteButton.setTitle("+/-", for: .normal)
        remainderButton.setTitle("%", for: .normal)
        divideButton.setTitle("/", for: .normal)
        multiplyButton.setTitle("*", for: .normal)
        subtractionButton.setTitle("-", for: .normal)
        additionButton.setTitle("+", for: .normal)
        
        dotButton.setTitle(".", for: .normal)
        
        getButton.setTitle("=", for: .normal)
        
        num0Button.setTitle("0", for: .normal)
        num1Button.setTitle("1", for: .normal)
        num2Button.setTitle("2", for: .normal)
        num3Button.setTitle("3", for: .normal)
        num4Button.setTitle("4", for: .normal)
        num5Button.setTitle("5", for: .normal)
        num6Button.setTitle("6", for: .normal)
        num7Button.setTitle("7", for: .normal)
        num8Button.setTitle("8", for: .normal)
        num9Button.setTitle("9", for: .normal)
        
        additionButton.addTarget(self, action: #selector(getAdd), for: .touchUpInside)
        subtractionButton.addTarget(self, action: #selector(getSub), for: .touchUpInside)
        multiplyButton.addTarget(self, action: #selector(getMul), for: .touchUpInside)
        divideButton.addTarget(self, action: #selector(getDiv), for: .touchUpInside)
        remainderButton.addTarget(self, action: #selector(getRem), for: .touchUpInside)
        
        clearButton.addTarget(self, action: #selector(clear), for: .touchUpInside)
        absoluteButton.addTarget(self, action: #selector(absolute), for: .touchUpInside)
        
        getButton.addTarget(self, action: #selector(result), for: .touchUpInside)
        
        num0Button.addTarget(self, action: #selector(getNum0), for: .touchUpInside)
        num1Button.addTarget(self, action: #selector(getNum1), for: .touchUpInside)
        num2Button.addTarget(self, action: #selector(getNum2), for: .touchUpInside)
        num3Button.addTarget(self, action: #selector(getNum3), for: .touchUpInside)
        num4Button.addTarget(self, action: #selector(getNum4), for: .touchUpInside)
        num5Button.addTarget(self, action: #selector(getNum5), for: .touchUpInside)
        num6Button.addTarget(self, action: #selector(getNum6), for: .touchUpInside)
        num7Button.addTarget(self, action: #selector(getNum7), for: .touchUpInside)
        num8Button.addTarget(self, action: #selector(getNum8), for: .touchUpInside)
        num9Button.addTarget(self, action: #selector(getNum9), for: .touchUpInside)
        
        let buttonName = [clearButton, absoluteButton, remainderButton, divideButton,multiplyButton,subtractionButton,additionButton,getButton, num0Button, num1Button, num2Button,num3Button,num4Button,num5Button,num6Button,num7Button,num8Button,num9Button,dotButton]
        

        view.addSubview(calView)
        view.addSubview(resultLabel)
        for index in buttonName{
            calView.addSubview(index)
        }
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
    
    @objc func makeButton(xline : Int = 1, yline : Int = 1, frame : CGRect,_ color : UIColor = .darkGray)->UIButton{
        let newButton = UIButton(frame: setFrame(Int(view.frame.minX) + (Int(view.frame.width)/4*xline), Int(view.frame.minY)+(Int(view.frame.width)/4*yline), Int(view.frame.width)/4, Int(view.frame.width)/4 ))
        newButton.backgroundColor = color
        newButton.layer.cornerRadius = 50
        return newButton
    }
    @objc func setFrame(_ x: Int,_ y: Int,_ width: Int,_ height: Int)->CGRect{
        return CGRect(x: x, y: y, width: width, height: height)
    }

    @objc func resetResultNum(){
        self.resultNum = self.num1
    }
    
    @objc func clear(){
        self.num1 = 0
        self.num2 = 0
        self.str1 = ""
        self.str2 = ""
        self.resultNum = 0
        self.numArray.removeAll()
        print("clear")
    }
    
    @objc func addition(_ num1 :Int,_ num2 : Int)->Int{
        return num1 + num2
    }
    
    @objc func subtraction(_ num1:Int,_ num2:Int)->Int{
        return num1 - num2
    }
    
    @objc func multiply(_ num1: Int,_ num2: Int)->Int{
        return num1 * num2
    }
    
    @objc func divide(_ num1:Int,_ num2:Int)->Int {
        if num2 == 0 {
            return 0
        }
        else{
            return num1 / num2
        }
    }
    
    @objc func remainder(_ num1:Int,_ num2:Int)->Int{
        if num2 == 0 {
            return 0
        }
        else{
            return num1 % num2
        }
    }
    
    @objc func absolute(){
        getArrayNum()
        
        self.num1 = self.num1 * (-1)
        
        resetResultNum()
    }
    
    @objc func result(){
        if self.str1 == ""{
            self.str1 = "res"
        }
        else{
            self.str2 = "res"
        }
        getArrayNum()
        print("res \(self.str1) \(self.str2)")
        resetResultNum()
        countResultNum = 0
    }
    
    
    @objc func set10(num : Int)->Int{
        var returnNum : Int = 1
        if num == 0 {
            return 1
        }
        else{
            for _ in 1...num{
                returnNum = returnNum * 10
            }
            return returnNum
        }
    }
    
    @objc func getArrayNum(){
        nilResultText()
        let newArray = self.numArray.reversed().map{$0}
        for index in self.numArray.startIndex..<self.numArray.endIndex{
            self.sum1 = self.sum1 + (newArray[index]*(set10(num: index)))
        }
        if self.num1 == 0 {
            self.num1 = self.sum1
            sum1 = 0
        }
        else {
            self.num2 = self.sum1
            sum1 = 0
            
            if self.str1 != ""{
                print("before : \(self.num1) \(self.num2) \(self.str1) \(self.str2)")

                switch self.str1{
                case "add":
                    self.num1 = addition(self.num1, self.num2)
                case "sub":
                    self.num1 = subtraction(self.num1, self.num2)
                case "mul":
                    self.num1 = multiply(self.num1, self.num2)
                case "rem":
                    self.num1 = remainder(self.num1, self.num2)
                case "div":
                    self.num1 = divide(self.num1, self.num2)
                case "res":
                    self.str1 = ""
                default :
                    break
                }
                if str2 != ""{
                    self.str1 = self.str2
                    self.str2 = ""
                }
                self.num2 = 0
                print("after : \(self.num1) \(self.num2) \(self.str1) \(self.str2)")
            }
        }
        self.numArray.removeAll()
    }
    
    
    @objc func getAdd(){
        
        if self.str1 == ""{
            self.str1 = "add"
        }
        else{
            self.str2 = "add"
        }
        print("add \(self.str1) \(self.str2)")
        getArrayNum()
        print("add \(self.str1) \(self.str2)")
    }
    @objc func getSub(){
        if self.str1 == ""{
            self.str1 = "sub"
        }
        else{
            self.str2 = "sub"
        }
        getArrayNum()
        print("sub \(self.str1) \(self.str2)")
    }
    @objc func getMul(){
        if self.str1 == ""{
            self.str1 = "mul"
        }
        else{
                self.str2 = "mul"
        }
        getArrayNum()
        print("mul \(self.str1) \(self.str2)")
    }
    @objc func getDiv(){
        if self.str1 == ""{
            self.str1 = "div"
        }
        else{
            self.str2 = "div"
        }
        getArrayNum()
        print("div \(self.str1) \(self.str2)")
    }
    @objc func getRem(){
        if self.str1 == ""{
            self.str1 = "rem"
        }
        else{
            self.str2 = "rem"
        }
        getArrayNum()
        print("rem \(self.str1) \(self.str2)")
    }
    
    @objc func getNum0(){
        self.numArray.append(0)
        print(0)
        setResultText("0")
    }
    @objc func getNum1(){
        self.numArray.append(1)
        print(1)
        setResultText("1")
    }
    @objc func getNum2(){
        self.numArray.append(2)
        print(2)
        setResultText("2")
    }
    @objc func getNum3(){
        self.numArray.append(3)
        print(3)
        setResultText("3")
    }
    @objc func getNum4(){
        self.numArray.append(4)
        print(4)
        setResultText("4")
    }
    @objc func getNum5(){
        self.numArray.append(5)
        print(5)
        setResultText("5")
    }
    @objc func getNum6(){
        self.numArray.append(6)
        print(6)
        setResultText("6")
    }
    @objc func getNum7(){
        self.numArray.append(7)
        print(7)
        setResultText("7")
    }
    @objc func getNum8(){
        self.numArray.append(8)
        setResultText("8")
        print(8)
    }
    @objc func getNum9(){
        self.numArray.append(9)
        setResultText("9")
        print(9)
    }
    
    @objc func nilResultText(){
        self.resultLabel.text = ""
    }
    @objc func setResultText(_ num : String){
        print(countResultNum)
        if countResultNum == 0 {
            nilResultText()
        }
        countResultNum = 1
        self.resultLabel.text = self.resultLabel.text! + num
    }
}

```
