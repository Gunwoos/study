# AccessoryType
- tableView 의 각 cell 의 accessory 를 줌

### AccessoryType 종류
- case none // don't show any accessory view
- case disclosureIndicator // regular chevron. doesn't track
- case detailDisclosureButton // info button w/ chevron. tracks
- case checkmark // checkmark. doesn't track
@available(iOS 7.0, *)
- case detailButton // info button. tracks

### AccessoryType 생성
- UITableViewDataSource 로 확장하여 cell 의 악세사리 타입을 지정해줌
- 악세사리 타입의 변동 사항은 delegate 에서 다뤄준다
```
extension ViewController : UITableViewDataSource{
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return kermit.count
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = UITableViewCell(style: .default, reuseIdentifier: "CELL")
        cell.textLabel?.text = String(kermit[indexPath.row])
        cell.accessoryType = checked[indexPath.row] ? .checkmark: .none

        return cell
    }
}
```

#### ViewController.swift
```
//
//  ViewController.swift
//  0621_shopping
//
//  Created by 임건우 on 2018. 6. 21..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    private let tableView = UITableView()
    private let kermit = ["Kermit_Goodbye","Kermit_Muppets","Kermit_poleDance","Kermit_puppeteer_fired","Kermit_Sick"]
    var checked: Array<Bool> = []
    
    override func viewDidLoad() {
        super.viewDidLoad()
        checked = Array<Bool>(repeating: false, count: kermit.count)
        
        tableView.frame = view.frame
        tableView.rowHeight = 30
        tableView.dataSource = self
        tableView.delegate = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "CELL")
        
        view.addSubview(tableView)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}

extension ViewController : UITableViewDataSource{
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return kermit.count
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = UITableViewCell(style: .default, reuseIdentifier: "CELL")
        cell.textLabel?.text = String(kermit[indexPath.row])
        cell.imageView?.image = UIImage(named: kermit[indexPath.row])
        cell.imageView?.contentMode = .scaleToFill
        cell.accessoryType = checked[indexPath.row] ? .checkmark: .none

        
        return cell
    }
    func tableView(_ tableView:UITableView, heightForRowAt indexPath: IndexPath)->CGFloat{
        return 80
    }
}

extension ViewController : UITableViewDelegate{
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        guard let cell = tableView.cellForRow(at: indexPath) else { return }
        if cell.accessoryType == .checkmark{
            cell.accessoryType = .none
        }
        else{
            cell.accessoryType = .checkmark
        }
        print(cell.accessoryType)
        checked[indexPath.row] = !checked[indexPath.row]
    }
}

```
