```
//: Playground - noun: a place where people can play

import UIKit


class Node {
    let value: Int
    var left: Node?
    var right: Node?
    init(value: Int) {
        self.value = value
    }
}

class LinkedList {
    var head: Node? // 제일 첫번째 node
    var tail: Node? // 제일 마지막 node
    var check: Node? //
    var listSize = 0 // node 의 수
    func nodeSet(){
        head = tail
        tail = head
    }
    func push(newNodeValue : Int){
        let newNode = Node(value: newNodeValue)
        
        if head?.value == nil{
            head = newNode
            tail = newNode
            
            listSize += 1
            print("head is empty")
        }
        else{
            tail?.right = newNode
            newNode.left = tail
            
            tail = newNode
            
            listSize += 1
            print("head is not empty")
        }
    }// 노드 추가
    
    func insert(newNodeValue : Int, at : Int){
        
        guard at <= listSize else { return }
        let newNode = Node(value: newNodeValue)
    
        if at == 1{
            newNode.right = head
            head?.left = newNode
            
            head = newNode
            listSize += 1
        }
        else if at == listSize{
            tail?.right = newNode
            newNode.left = tail
            
            tail = newNode
            
            listSize += 1
        }
        else{
            check = head
            for _ in 2...at{
                check = check?.right
            }
            newNode.right = check
            newNode.left = check?.left
            
            check?.left?.right = newNode
            check?.left = newNode
        }
    }// 원하는 위치에 노드 추가
    
    func pop(){
        guard head != nil else{print("node is empty"); return}
        tail?.left?.right = nil
        tail = tail?.left
        
    } // 마지막 노드 삭제
    
    func remove(at : Int){
        guard at <= listSize else { return }
        
        if at == 1{
            head?.right?.left = nil
            head = head?.right
        }
        else if at == listSize{
            tail?.left?.right = nil
            tail = tail?.left
        }
        else{
            check = head
            for _ in 2...at{
                check = check?.right
            }
            check?.left?.right = check?.right
            check?.right?.left = check?.left
        }
    }
    
    func peak(){
        if head != nil{
            print("last Node Value : \(tail!.value)")
        }
        else{
            print("node is empty")
        }
    }// 마지막 데이터 출력
    
}


let myNodeList = LinkedList()
myNodeList.nodeSet()

myNodeList.push(newNodeValue: 1)
print(myNodeList.head!.value)

myNodeList.push(newNodeValue: 2)


myNodeList.push(newNodeValue: 3)

myNodeList.insert(newNodeValue: 4, at: 3)

myNodeList.insert(newNodeValue: 5, at: 1)

//myNodeList.pop()

//myNodeList.remove(at: 1)

//myNodeList.pop()

myNodeList.peak()

print("---my Node List---")
while myNodeList.head?.value != nil{
    print("\(myNodeList.head!.value)")
    myNodeList.head = myNodeList.head?.right
}




```
