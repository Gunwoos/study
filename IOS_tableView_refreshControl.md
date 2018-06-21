```
//
//  ViewController.swift
//  0621_pullToRefresh
//
//  Created by 임건우 on 2018. 6. 21..
//  Copyright © 2018년 lims. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    private let tableView = UITableView()
    private var data : [Int] = Array(1...20)
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        setTableView()

    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
    
    func setTableView(){
        
        tableView.frame = self.view.frame
        tableView.dataSource = self
        tableView.delegate = self
        tableView.allowsMultipleSelection = true
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "myCell")
        
        
        view.addSubview(self.tableView)
        
        let refreshControl = UIRefreshControl()
        refreshControl.addTarget(self, action: #selector(reloadData), for: .valueChanged)
        refreshControl.attributedTitle = NSAttributedString(string: "Refreshing...")
        refreshControl.tintColor = .blue
        tableView.refreshControl = refreshControl
        
    }
    
    @objc func reloadData(){
        var selectedNumbers: [Int] = []
        if let selectdRows = tableView.indexPathsForSelectedRows{
            selectedNumbers = selectdRows.map{ return data[$0.row]}
        }
        data = selectedNumbers
    
        for _ in selectedNumbers.count...20{
            setData()
        }
        
        if tableView.refreshControl!.isRefreshing{
            tableView.refreshControl?.endRefreshing()
        }
        
        tableView.reloadData()
    }
    
    func setData(){
        let randomNum = Int(arc4random_uniform(50))
        guard !self.data.contains(randomNum) else{ return setData()}
        self.data.append(randomNum)
    }
    
}

extension ViewController : UITableViewDataSource{
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.data.count
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell : UITableViewCell = tableView.dequeueReusableCell(withIdentifier: "myCell", for: indexPath)
        cell.textLabel?.text = String(data[indexPath.row])

        return cell
    }

}

extension ViewController : UITableViewDelegate{
    func tableView(_ tableView: UITableView, willSelectRowAt indexPath: IndexPath) -> IndexPath? {
//        guard  data[indexPath.row] > 10 else { return nil
//        }
        return indexPath
    }
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    }
}


```
