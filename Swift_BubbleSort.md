```
func bubbleSort(input: inout [Int]) {
  for i in 1..<input.count {
    print("\(i):", input)
    var isSorted = true

    for idx in 0..<input.count - i {
      if input[idx] > input[idx + 1] {
        input.swapAt(idx, idx + 1)
        isSorted = false
      }
    }

    guard !isSorted else { break }
  }
}

bubbleSort(input: &input)
```
