# TableView
![simulator screen shot - iphone 8 plus - 2018-07-06 at 17 27 57](https://user-images.githubusercontent.com/39073993/42368618-7862271e-8142-11e8-8a1e-ad75308aed83.png)

- 위에 그림을 tableView 라고 한다
- 어떤 항목들을 관리하기 위한 controller ex) iPhone 의 setting
### tableView 생성
```

// tableview  생성
let myTableView = UITableView() 

// tableview frame 값 지정
myTableView.frame = CGRect(
    x: <#T##CGFloat#>, 
    y: <#T##CGFloat#>, 
    width: <#T##CGFloat#>, 
    height: <#T##CGFloat#>
    )
    
// view 에 tableView 추가
view.addSubview(tableView)
```

### Sample code
#### ViewController
```
//
//  ViewController.swift
//  Class0620_tableView
//
//  Created by 임건우 on 2018. 6. 20..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    private let myTableView = UITableView()
    private let items = Array(1...50)
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.myTableView.dataSource = self
        self.myTableView.delegate = self
        self.myTableView.register(UITableViewCell.self, forCellReuseIdentifier: "TableViewCell")
        self.view.addSubview(self.myTableView)
        
        self.myTableView.frame = CGRect(origin: CGPoint(x: view.frame.minX, y: view.frame.minY), size: view.frame.size)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
}

extension ViewController : UITableViewDataSource{
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.items.count
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell: UITableViewCell = tableView.dequeueReusableCell(withIdentifier: "TableViewCell")! as UITableViewCell
        cell.textLabel?.text = String(items[indexPath.row])
        
        return cell
    }
}

extension ViewController : UITableViewDelegate{
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        print(items[indexPath.row])
    }
}




```
