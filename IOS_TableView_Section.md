# TableView Section
- tablaview 에는 section 을 주어 한 section 당 n 개의 cell 을 가질 수 있다.
- 어떠한 항목을 section 으로 지정해 그 항목이 다루는 사항을 cell 들로 지정하여 table을 구성할 수 있다.

### Section 생성
- ViewController 을 tableViewDataSource 로 extension 하여 section 의 수와 text 를 지정해줌
```
extension ViewController : UITableViewDataSource{
    // section 의 수를 지정
    func numberOfSections(in tableView: UITableView) -> Int { 
        return Int(0)
    }
    // section 의 title 에 들어갈 text 를 지정
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        return "String"
    }
}
```


### ViewController.swift

```
//
//  ViewController.swift
//  Class0620_tableView2
//
//  Created by 임건우 on 2018. 6. 20..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    private let tableView = UITableView()
    private let items = Array(1...48)
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.tableView.dataSource = self
        self.tableView.delegate = self
        self.tableView.register(UITableViewCell.self, forCellReuseIdentifier: "TableViewCell")
        self.tableView.frame = CGRect(origin: CGPoint(x: view.frame.minX, y: view.frame.minY+15), size: view.frame.size)
        
        self.view.addSubview(self.tableView)
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
}

extension ViewController : UITableViewDataSource{
    func numberOfSections(in tableView: UITableView) -> Int {
        return (items.count/10)+1
    }
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        if section != items.count/10{
            return 10
        }
        else{
            return items.count%10
        }
    }
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        return "\(section)"
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell : UITableViewCell = tableView.dequeueReusableCell(withIdentifier: "TableViewCell")! as UITableViewCell
        cell.textLabel?.text = String(indexPath.section*10 + items[indexPath.row])
        
        return cell
    }
    
    
}

extension ViewController : UITableViewDelegate{
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        print(items[indexPath.row])
    }
    
}

```
