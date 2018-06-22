```
//: Playground - noun: a place where people can play

import UIKit

class Node {
    let value: String
    var next: Node?
    init(value: String) {
        self.value = value
    }
}

class LinkedList {
    var head: Node? // 제일 첫번째 node
    var tail: Node? // 제일 마지막 node
    var check: Node? //
    var listSize = 0 // node 의 수

    func push(myNode : String) {
        let newNode = Node(value: myNode)

        if head == nil{
            print("---head is Empty---")
            head = newNode
            tail = newNode
        }
        else{
            print("---head is not Empty---")
            tail?.next = newNode
            tail = newNode
        }
        listSize += 1
    } // 데이터 삽입
    
    func pop() {
        if head == nil{
            print("---node is empty---")
        }
        else{
            check = head
            var checkNum = 1
            if listSize != 1{
                while checkNum != listSize-1 {
                    check = check?.next
                    checkNum += 1
                }
                check?.next = nil
                tail = check
                listSize -= 1
                
                print("---pop()---")
            }
            else{
                head = nil
                print("---pop()---")
            }
        }

    }  // 데이터 반출.
    
    func peek() {
        if head != nil{
            print("last Node Valeu : \(tail!.value)")
        }
        else{
            print("last node is empty")
        }
    } // 마지막 데이터 확인
}

let myNode = LinkedList()

myNode.push(myNode: "1")
myNode.peek()
myNode.push(myNode: "2")
myNode.peek()
myNode.push(myNode: "3")
myNode.peek()

myNode.pop()
myNode.pop()
myNode.pop()

myNode.peek()

print("---my Node List---")
while myNode.head != nil{
    print("\(myNode.head!.value)")
    myNode.head = myNode.head?.next
}

myNode.pop()

myNode.push(myNode: "!")
myNode.peek()
myNode.push(myNode: "@")
myNode.peek()
myNode.push(myNode: "3")
myNode.peek()

print("---my Node List---")
while myNode.head != nil{
    print("\(myNode.head!.value)")
    myNode.head = myNode.head?.next
}






```
