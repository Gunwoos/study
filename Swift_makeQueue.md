```
//: Playground - noun: a place where people can play

import UIKit

class CustomQueue{
    var EnqueueStack : Array<Int> = []
    var DequeueStack : Array<Int> = []
    
    func Enqueue(_ newValue : Int){
        if DequeueStack.isEmpty{
            EnqueueStack.append(newValue)
        }
        else{
            while DequeueStack.isEmpty != true {
                EnqueueStack.append(DequeueStack.popLast()!)
            }
            EnqueueStack.append(newValue)
        }
    }
    func Dequeue(){
        if EnqueueStack.isEmpty{
            DequeueStack.popLast()
        }
        else{
            while EnqueueStack.isEmpty != true {
                DequeueStack.append(EnqueueStack.popLast()!)
            }
            DequeueStack.popLast()
        }
    }
}

var myCustomQueue = CustomQueue()


myCustomQueue.Enqueue(1)

myCustomQueue.Enqueue(2)

myCustomQueue.Dequeue()

myCustomQueue.Enqueue(3)

myCustomQueue.Dequeue()


```
