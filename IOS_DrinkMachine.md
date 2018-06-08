### ViewController

```
//
//  ViewController.swift
//  DrinkMachine_gw
//
//  Created by 임건우 on 2018. 6. 8..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    class moneyInMachine{
        static let shared = moneyInMachine()
        private init(){
            
        }
        var inputMoney = 0
        var outputMoney = 0
        let cokeMoney = 1000
        let ciderMoney = 800
        let coffeeMoney = 1500
        let waterMoney = 500
        
        var cokeNum = 5
        var ciderNum = 5
        var coffeeNum = 5
        var waterNum = 5
    }
    
    let newMachine = moneyInMachine.shared
    
    
    lazy var DrinkMachineView = UIView(frame: getFrame(view.frame.minX + 20, view.frame.minY + 20, view.frame.width - 40, view.frame.height - 40))
    lazy var resultTextLabel = UILabel(frame: getFrame(view.frame.minX + 20, DrinkMachineView.frame.width + 110, DrinkMachineView.frame.width - 40, 50))
    lazy var moneyTextLabel = UILabel(frame: getFrame(view.frame.minX + 20, DrinkMachineView.frame.width + 160 , DrinkMachineView.frame.width - 40, 50))
    lazy var drink1Button = UIButton(frame: getFrame(view.frame.minX + 10, view.frame.minY + DrinkMachineView.frame.width/2, DrinkMachineView.frame.width/2 - 20, 50))
    lazy var drink2Button = UIButton(frame: getFrame(view.frame.minX + DrinkMachineView.frame.width/2 + 10, view.frame.minY + DrinkMachineView.frame.width/2, DrinkMachineView.frame.width/2 - 20, 50))
    lazy var drink3Button = UIButton(frame: getFrame(view.frame.minX + 10, DrinkMachineView.frame.width/2 + 50 + DrinkMachineView.frame.width/2 , DrinkMachineView.frame.width/2 - 20, 50))
    lazy var drink4Button = UIButton(frame: getFrame(view.frame.minX + DrinkMachineView.frame.width/2 + 10, DrinkMachineView.frame.width/2 + 50 + DrinkMachineView.frame.width/2, DrinkMachineView.frame.width/2 - 20, 50))
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.modalTransitionStyle = .crossDissolve
        view.backgroundColor = .white
        
        DrinkMachineView.layer.borderWidth = 2
        DrinkMachineView.layer.borderColor = UIColor.black.cgColor
        DrinkMachineView.backgroundColor = .red
        
        view.addSubview(DrinkMachineView)
        
        let drink1View = UIImageView(frame: getFrame(view.frame.minX + 10, view.frame.minY + 10, DrinkMachineView.frame.width/2 - 20, DrinkMachineView.frame.width/2 - 20))
        drink1View.image = #imageLiteral(resourceName: "coka.jpg")
        drink1View.contentMode = .scaleToFill
        drink1View.layer.borderWidth = 2
        drink1View.layer.borderColor = UIColor.black.cgColor
        drink1View.layer.cornerRadius = 5
        
        DrinkMachineView.addSubview(drink1View)
        
        
        drink1Button.setTitle("1000원", for: .normal)
        drink1Button.setTitleColor(.black, for: .normal)
        drink1Button.setTitleColor(.blue, for: .highlighted)
        drink1Button.layer.borderColor = UIColor.black.cgColor
        drink1Button.layer.borderWidth = 2
        drink1Button.layer.cornerRadius = 5
        drink1Button.backgroundColor = .white
        drink1Button.addTarget(self, action: #selector(getCoke), for: .touchUpInside)
       
        DrinkMachineView.addSubview(drink1Button)
        
        let drink2View = UIImageView(frame: getFrame(view.frame.minX + DrinkMachineView.frame.width/2 + 10, view.frame.minY + 10, DrinkMachineView.frame.width/2 - 20, DrinkMachineView.frame.width/2 - 20))
        drink2View.image = #imageLiteral(resourceName: "cider.jpeg")
        drink2View.contentMode = .scaleToFill
        drink2View.layer.borderWidth = 2
        drink2View.layer.borderColor = UIColor.black.cgColor
        drink2View.layer.cornerRadius = 5
        
        DrinkMachineView.addSubview(drink2View)
        
        
        drink2Button.setTitle("800원", for: .normal)
        drink2Button.setTitleColor(.black, for: .normal)
        drink2Button.setTitleColor(.blue, for: .highlighted)
        drink2Button.layer.borderColor = UIColor.black.cgColor
        drink2Button.layer.borderWidth = 2
        drink2Button.layer.cornerRadius = 5
        drink2Button.backgroundColor = .white
        drink2Button.addTarget(self, action: #selector(getCider), for: .touchUpInside)
        
        DrinkMachineView.addSubview(drink2Button)
        
        let drink3View = UIImageView(frame: getFrame(10, DrinkMachineView.frame.width/2 + 60, DrinkMachineView.frame.width/2 - 20, DrinkMachineView.frame.width/2 - 20))
        drink3View.image = #imageLiteral(resourceName: "letsbe.jpg")
        drink3View.contentMode = .scaleToFill
        drink3View.layer.borderWidth = 2
        drink3View.layer.borderColor = UIColor.black.cgColor
        drink3View.layer.cornerRadius = 5
        
        DrinkMachineView.addSubview(drink3View)
        
        
        drink3Button.setTitle("1500원", for: .normal)
        drink3Button.setTitleColor(.black, for: .normal)
        drink3Button.setTitleColor(.blue, for: .highlighted)
        drink3Button.layer.borderColor = UIColor.black.cgColor
        drink3Button.layer.borderWidth = 2
        drink3Button.layer.cornerRadius = 5
        drink3Button.backgroundColor = .white
        drink3Button.addTarget(self, action: #selector(getCoffee), for: .touchUpInside)
        
        DrinkMachineView.addSubview(drink3Button)
        
        let drink4View = UIImageView(frame: getFrame(view.frame.minX + DrinkMachineView.frame.width/2 + 10, DrinkMachineView.frame.width/2 + 60, DrinkMachineView.frame.width/2 - 20, DrinkMachineView.frame.width/2 - 20))
        drink4View.image = #imageLiteral(resourceName: "evian.jpg")
        drink4View.contentMode = .scaleToFill
        drink4View.layer.borderWidth = 2
        drink4View.layer.borderColor = UIColor.black.cgColor
        drink4View.layer.cornerRadius = 5
        
        DrinkMachineView.addSubview(drink4View)
        
       
        drink4Button.setTitle("500원", for: .normal)
        drink4Button.setTitleColor(.black, for: .normal)
        drink4Button.setTitleColor(.blue, for: .highlighted)
        drink4Button.layer.borderColor = UIColor.black.cgColor
        drink4Button.layer.borderWidth = 2
        drink4Button.layer.cornerRadius = 5
        drink4Button.backgroundColor = .white
        drink4Button.addTarget(self, action: #selector(getWater), for: .touchUpInside)
        
        DrinkMachineView.addSubview(drink4Button)
        
        
        resultTextLabel.textAlignment = .right
        resultTextLabel.backgroundColor = .black
        resultTextLabel.textColor = .white
        resultTextLabel.text = ""
        
        DrinkMachineView.addSubview(resultTextLabel)
        
        moneyTextLabel.textAlignment = .right
        moneyTextLabel.backgroundColor = .black
        moneyTextLabel.textColor = .white
        moneyTextLabel.text = "잔액 : 0 원 "

        DrinkMachineView.addSubview(moneyTextLabel)

        
        let moneyButton1 = UIButton(frame: getFrame(moneyTextLabel.frame.minX, moneyTextLabel.frame.maxY + 10, 100, 50))
        moneyButton1.setTitleColor(.black, for: .normal)
        moneyButton1.setTitleColor(.blue, for: .highlighted)
        moneyButton1.layer.borderWidth = 2
        moneyButton1.layer.borderColor = UIColor.black.cgColor
        moneyButton1.layer.cornerRadius = 5
        moneyButton1.setTitle("1000원", for: .normal)
        moneyButton1.backgroundColor = .white
        moneyButton1.addTarget(self, action: #selector(add1000), for: .touchUpInside)
        
        DrinkMachineView.addSubview(moneyButton1)
        
        let moneyButton2 = UIButton(frame: getFrame(moneyTextLabel.frame.minX + 110, moneyTextLabel.frame.maxY + 10, 100, 50))
        moneyButton2.setTitleColor(.black, for: .normal)
        moneyButton2.setTitleColor(.blue, for: .highlighted)
        moneyButton2.layer.borderWidth = 2
        moneyButton2.layer.borderColor = UIColor.black.cgColor
        moneyButton2.layer.cornerRadius = 5
        moneyButton2.setTitle("500원", for: .normal)
        moneyButton2.backgroundColor = .white
        moneyButton2.addTarget(self, action: #selector(add500), for: .touchUpInside)
        
        DrinkMachineView.addSubview(moneyButton2)
        
        
        let moneyButton3 = UIButton(frame: getFrame(moneyTextLabel.frame.minX + 220, moneyTextLabel.frame.maxY + 10, 110, 50))
        moneyButton3.setTitleColor(.black, for: .normal)
        moneyButton3.setTitleColor(.blue, for: .highlighted)
        moneyButton3.layer.borderWidth = 2
        moneyButton3.layer.borderColor = UIColor.black.cgColor
        moneyButton3.layer.cornerRadius = 5
        moneyButton3.setTitle("Money Back", for: .normal)
        moneyButton3.backgroundColor = .white
        moneyButton3.addTarget(self, action: #selector(refundMoney), for: .touchUpInside)
        
        DrinkMachineView.addSubview(moneyButton3)
        
        let masterButton = UIButton(frame: getFrame(moneyButton1.frame.minX, moneyButton1.frame.maxY + 10,200, 30))
        masterButton.setTitleColor(.white, for: .normal)
        masterButton.setTitleColor(.yellow, for: .highlighted)
        masterButton.layer.borderWidth = 2
        masterButton.layer.borderColor = UIColor.black.cgColor
        masterButton.layer.cornerRadius = 5
        masterButton.setTitle("masterButton", for: .normal)
        masterButton.backgroundColor = .black
        masterButton.addTarget(self, action: #selector(openMachine), for: .touchUpInside)
        
        DrinkMachineView.addSubview(masterButton)
        
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    @objc func getFrame(_ x : CGFloat, _ y : CGFloat,_ width : CGFloat,_ height : CGFloat)->CGRect{
        return CGRect(x: x, y: y, width: width, height: height)
    }

    @objc func add1000(){
        self.newMachine.inputMoney += 1000
        self.newMachine.outputMoney = self.newMachine.inputMoney
        self.resultTextLabel.text = "1000 원 넣었습니다 "
        setInputMoneyText()
    }
    
    @objc func add500(){
        self.newMachine.inputMoney += 500
        self.newMachine.outputMoney = self.newMachine.inputMoney
        self.resultTextLabel.text = "500 원 넣었습니다 "
        setInputMoneyText()
    }
    
    @objc func refundMoney(){
        guard checkMoney("refund") == true else { return }
        
        self.newMachine.outputMoney = self.newMachine.inputMoney
        self.newMachine.inputMoney = 0
        self.resultTextLabel.text = "\(self.newMachine.outputMoney) Back "
        setInputMoneyText()
    }

    @objc func getCoke(){
        guard checkMoney("coke") == true else{ return }
        guard checkDrinkNum("coke") == true else { return }
        
        self.newMachine.inputMoney = self.newMachine.inputMoney - self.newMachine.cokeMoney
        self.newMachine.outputMoney = self.newMachine.inputMoney
        setInputMoneyText()
        self.resultTextLabel.text = "콜라를 구매했습니다 "
    }
    
    @objc func getCider(){
        guard checkMoney("cider") == true else { return }
        guard checkDrinkNum("cider") == true else { return }
        
        self.newMachine.inputMoney = self.newMachine.inputMoney - self.newMachine.ciderMoney
        self.newMachine.outputMoney = self.newMachine.inputMoney
        setInputMoneyText()
        self.resultTextLabel.text = "사이다를 구매했습니다 "
    }
    
    @objc func getCoffee(){
        guard checkMoney("coffee") == true else { return }
        guard checkDrinkNum("coffee") == true else { return }
        
        self.newMachine.inputMoney = self.newMachine.inputMoney - self.newMachine.coffeeMoney
        self.newMachine.outputMoney = self.newMachine.inputMoney
       setInputMoneyText()
        self.resultTextLabel.text = "커피를 구매했습니다 "
    }
    
    @objc func getWater(){
        guard checkMoney("water") == true else{ return }
        guard checkDrinkNum("water") == true else { return }
        
        self.newMachine.inputMoney = self.newMachine.inputMoney - self.newMachine.waterMoney
        self.newMachine.outputMoney = self.newMachine.inputMoney
        setInputMoneyText()
        self.resultTextLabel.text = "물을 구매했습니다 "
    }
    
    @objc func checkMoney(_ drinkName : String)->Bool{
        var checkBool = true
        switch drinkName {
        case "coke":
            if self.newMachine.inputMoney < self.newMachine.cokeMoney {
                self.resultTextLabel.text = "잔액이 부족합니다 "
                checkBool = false
            }
            break
        case "cider":
            if self.newMachine.inputMoney < self.newMachine.ciderMoney {
                self.resultTextLabel.text = "잔액이 부족합니다 "
                checkBool = false
            }
            break
        case "coffee":
            if self.newMachine.inputMoney < self.newMachine.coffeeMoney {
                self.resultTextLabel.text = "잔액이 부족합니다 "
                checkBool = false
            }
            break
        case "water":
            if self.newMachine.inputMoney < self.newMachine.waterMoney {
                self.resultTextLabel.text = "잔액이 부족합니다 "
                checkBool = false
            }
            break
        case "refund":
            if self.newMachine.inputMoney <= 0 {
                self.resultTextLabel.text = "잔액이 \(self.newMachine.inputMoney) 원 입니다 "
                checkBool = false
            }
            break
        default:
            break
        }
        return checkBool
    }
    
    @objc func checkDrinkNum(_ drinkName : String ) -> Bool{
        var checkBool = true
        switch drinkName {
        case "coke":
            if self.newMachine.cokeNum <= 0 {
                self.resultTextLabel.text = "콜라 재고가 없습니다 "
                self.drink1Button.setTitle("sold out", for: .normal)
                self.drink1Button.setTitleColor(.red, for: .normal)
                checkBool = false
            }
            else{
                self.newMachine.cokeNum -= 1
                self.drink1Button.setTitle("1000원", for: .normal)
                self.drink1Button.setTitleColor(.black, for: .normal)
            }
            break
        case "cider":
            if self.newMachine.ciderNum <= 0 {
                self.resultTextLabel.text = "사이다 재고가 없습니다 "
                self.drink2Button.setTitle("sold out", for: .normal)
                self.drink2Button.setTitleColor(.red, for: .normal)
                checkBool = false
            }
            else{
                self.newMachine.ciderNum -= 1
                self.drink2Button.setTitle("800원", for: .normal)
                self.drink2Button.setTitleColor(.black, for: .normal)
            }
            break
        case "coffee":
            if self.newMachine.coffeeNum <= 0 {
                self.resultTextLabel.text = "커피 재고가 없습니다 "
                self.drink3Button.setTitle("sold out", for: .normal)
                self.drink3Button.setTitleColor(.red, for: .normal)
                checkBool = false
            }
            else {
                self.newMachine.coffeeNum -= 1
                self.drink3Button.setTitle("1500원", for: .normal)
                self.drink3Button.setTitleColor(.black, for: .normal)
            }
            break
        case "water":
            if self.newMachine.waterNum <= 0 {
                self.resultTextLabel.text = "물 재고가 없습니다 "
                self.drink4Button.setTitle("sold out", for: .normal)
                self.drink4Button.setTitleColor(.red, for: .normal)
                checkBool = false
            }
            else {
                self.newMachine.waterNum -= 1
                self.drink4Button.setTitle("500원", for: .normal)
                self.drink4Button.setTitleColor(.black, for: .normal)
            }
            break
        default:
            break
        }
        return checkBool
    }
    
    @objc func setInputMoneyText(){
        self.moneyTextLabel.text = "잔액 : \(self.newMachine.inputMoney) 원 "
    }
    
    @objc func openMachine(){
        let myMachine = MasterViewController()
        
        present(myMachine, animated: true){
            myMachine.thisDrinkNum.cokeNum = self.newMachine.cokeNum
            myMachine.thisDrinkNum.ciderNum = self.newMachine.ciderNum
            myMachine.thisDrinkNum.coffeeNum = self.newMachine.coffeeNum
            myMachine.thisDrinkNum.waterNum = self.newMachine.waterNum
            myMachine.DrinkList.text = "\n\n\n\n --- DrinkList ---\nCoke : \(myMachine.thisDrinkNum.cokeNum)\nCider : \(myMachine.thisDrinkNum.ciderNum)\nCoffee : \(myMachine.thisDrinkNum.coffeeNum)\nWater : \(myMachine.thisDrinkNum.waterNum)"
        }
    }
}


```

### MasterViewController

```
//
//  MasterViewController.swift
//  DrinkMachine_gw
//
//  Created by 임건우 on 2018. 6. 8..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class MasterViewController: UIViewController {
    
    class DrinkNum{
        static let shared = DrinkNum()
        
        var cokeNum = 0
        var ciderNum = 0
        var coffeeNum = 0
        var waterNum = 0
        
    }
    
    let thisDrinkNum = DrinkNum.shared
    
    lazy var DrinkMachineView = UIView(frame: getFrame(view.frame.minX + 20, view.frame.minY + 20, view.frame.width - 40, view.frame.height - 40))
    lazy var DrinkList = UITextView(frame: getFrame(view.frame.minX + 20, view.frame.minY + 20, DrinkMachineView.frame.width - 40, DrinkMachineView.frame.width - 40))
    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.modalTransitionStyle = .crossDissolve
        view.backgroundColor = .white
        
        DrinkMachineView.layer.borderWidth = 2
        DrinkMachineView.layer.borderColor = UIColor.red.cgColor
        DrinkMachineView.backgroundColor = .black
        
        view.addSubview(DrinkMachineView)
        
        DrinkList.backgroundColor = UIColor.darkGray
        DrinkList.textAlignment = .center
        DrinkList.textColor = .black
        
        
        DrinkMachineView.addSubview(DrinkList)
        
        let addDrinkButton = UIButton(frame: getFrame(DrinkList.frame.width/2 - 50, DrinkList.frame.maxY + 20, 100, 50))
        addDrinkButton.setTitleColor(.white, for: .normal)
        addDrinkButton.setTitleColor(.yellow, for: .highlighted)
        addDrinkButton.layer.borderWidth = 2
        addDrinkButton.layer.borderColor = UIColor.white.cgColor
        addDrinkButton.layer.cornerRadius = 5
        addDrinkButton.setTitle("Fill Drink", for: .normal)
        addDrinkButton.backgroundColor = .black
        addDrinkButton.addTarget(self, action: #selector(refillDrink), for: .touchUpInside)
        
        DrinkMachineView.addSubview(addDrinkButton)
        
        
        let closeButton = UIButton(frame: getFrame(DrinkMachineView.frame.minX + 10, DrinkMachineView.frame.maxY - 110, 200, 50))
        closeButton.setTitleColor(.white, for: .normal)
        closeButton.setTitleColor(.yellow, for: .highlighted)
        closeButton.layer.borderWidth = 2
        closeButton.layer.borderColor = UIColor.white.cgColor
        closeButton.layer.cornerRadius = 5
        closeButton.setTitle("Close Door", for: .normal)
        closeButton.backgroundColor = .black
        closeButton.addTarget(self, action: #selector(closeMachineDoor), for: .touchUpInside)
        
        DrinkMachineView.addSubview(closeButton)
        
        // Do any additional setup after loading the view.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

    
    @objc func getFrame(_ x : CGFloat, _ y : CGFloat,_ width : CGFloat,_ height : CGFloat)->CGRect{
        return CGRect(x: x, y: y, width: width, height: height)
    }
    
    @objc func refillDrink(){
        self.thisDrinkNum.cokeNum += 5
        self.thisDrinkNum.ciderNum += 5
        self.thisDrinkNum.coffeeNum += 5
        self.thisDrinkNum.waterNum += 5
        
        self.DrinkList.text = "\n\n\n\n --- DrinkList ---\nCoke : \(self.thisDrinkNum.cokeNum)\nCider : \(self.thisDrinkNum.ciderNum)\nCoffee : \(self.thisDrinkNum.coffeeNum)\nWater : \(self.thisDrinkNum.waterNum)"
    }
    
    @objc func closeMachineDoor(){
        guard let preView = self.presentingViewController as? ViewController else{return}
        preView.newMachine.cokeNum = self.thisDrinkNum.cokeNum
        preView.newMachine.ciderNum = self.thisDrinkNum.ciderNum
        preView.newMachine.coffeeNum = self.thisDrinkNum.coffeeNum
        preView.newMachine.waterNum = self.thisDrinkNum.waterNum
        preView.checkDrinkNum("coke")
        preView.checkDrinkNum("cider")
        preView.checkDrinkNum("coffee")
        preView.checkDrinkNum("water")
        dismiss(animated: true)
    }

}

```
