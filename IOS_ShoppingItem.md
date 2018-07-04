
#### ViewController
```
//
//  ViewController.swift
//  ShoppingItems
//
//  Created by giftbot on 2018. 6. 20..
//  Copyright © 2018년 giftbot. All rights reserved.
//

import UIKit

final class ViewController: UIViewController, CustomCellDelegate {
  
  @IBOutlet private weak var tableView: UITableView!
  
    let item = ["iPhone8", "iPhoneSE_Gold", "iPhoneSE_RoseGold", "iPhoneX_SpaceGray", "iPhoneX_White","iPhone8", "iPhoneSE_Gold", "iPhoneSE_RoseGold", "iPhoneX_SpaceGray", "iPhoneX_White","iPhone8", "iPhoneSE_Gold", "iPhoneSE_RoseGold", "iPhoneX_SpaceGray", "iPhoneX_White","iPhone8", "iPhoneSE_Gold", "iPhoneSE_RoseGold", "iPhoneX_SpaceGray", "iPhoneX_White"]
    let itemMaxNum = [5, 2, 4, 7, 1,5, 2, 4, 7, 1,5, 2, 4, 7, 1,5, 2, 4, 7, 1]
    let itemNum = repeatElement(0, count: 20)
    
  override func viewDidLoad() {
    super.viewDidLoad()
    tableView.rowHeight = 80
  }
    
    func addItemToCart(_ itemCell: ItemCell, didTapAddItem : UIButton){
        let num = Int(itemCell.itemAmount.text!)
        itemCell.itemAmount.text = String(num!)
    }
}

// MARK: - UITableViewDataSource

extension ViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return item.count
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "ItemCell", for: indexPath) as! ItemCell
        cell.delegate = self
        
        
        
        cell.itemImage?.image = UIImage(named: item[indexPath.row])
        cell.itemTitle?.text = item[indexPath.row]
        cell.itemAmount?.text = String(itemNum[indexPath.row])
        
        //        cell.itemButton.addTarget(self, action: #selector(addItemAmount), for: .touchUpInside)
        
        
        return cell
    }
}

```


#### ItemCell

```
//
//  ItemCell.swift
//  ShoppingItems
//
//  Created by giftbot on 2018. 6. 20..
//  Copyright © 2018년 giftbot. All rights reserved.
//

import UIKit

// MARK: - Class Implementation
protocol  CustomCellDelegate: class {
    func addItemToCart(_ itemCell: ItemCell, didTapAddItem : UIButton)
}
final class ItemCell: UITableViewCell {
  
  // MARK: Properties
  
    weak var delegate: CustomCellDelegate?
    var orderAmountNum = 0

    @IBOutlet weak var itemImage: UIImageView!
    
    @IBOutlet weak var itemTitle: UILabel!
    
    @IBOutlet weak var itemAmount: UILabel!
    @IBAction func itemButton(_ sender: UIButton) {
        orderAmountNum += 1
        print(orderAmountNum)
        itemAmount.text = String(orderAmountNum)
        delegate?.addItemToCart(self, didTapAddItem: sender)
    }
    
}

```
