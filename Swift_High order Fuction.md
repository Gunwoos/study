# High order Function
```
- 하나 이상의 함수를 인자로 취하는 함수
- 함수를 결과로 반환하는 함수
- 함수가 First class Citizen 이어야 함
	- 변수나 데이터에 할당할 수 있어야 함
	- 객체의 인자로 넘길 수 있어야 함
	- 객체의 리턴값으로 리턴할 수 있어야 함
```

### forEach
- collection 전용 for 문
- forEach 형식
```
// public func forEach(_ body: (Element) throws -> Void) rethrows

let numbers = [1,2,3,4,5,6,7,8,9]
numbers.forEach({(num:Int) in
	print("3 * \(num) = \(3*num)")
})
```
- for문 과의 차이점
	- for 문은 조건을 주어 중간에 종료할 수 있는데 forEach 문은 해당 index 에 대한 함수만 종료되고 끝까지 실행이 된다.
	```
	let numbers = [1,2,3,4,5]

	for i in numbers{
		guard i != 3  else{break}
		guard i%2==0  else{continue}
		print(i)
	}
	
	numbers.forEach{num in
		guard num != 3  else{return}
		guard num%2==0  else{ return}
		print(num)
	}
	```
	↓
	```
	2 // for문 결과
	2 // forEach 문 결과
	4
	```
### Map
- collection 각 요소에 동일 연산 후 새 collection 을 반환
```
//  public func map<T>(_ transform: (Element) throws -> T) rethrows -> [T]

let num = Array[1, 2, 3, 4, 5]
num.map({ (number:Int) -> Int in
	return num + 1
})
// num.map{$0+1} // [2, 3, 4, 5, 6]
```
### filter
- collection 각 요소를 필터링 하여 참이 되는 값을 새 collection 으로 반환
```
let num = Array[1, 2, 3, 4, 5]

num.filter({(num:Int) -> Bool in
	return num%2==0
})

// num.filter{$0%2==0}
```

### reduce
- collection 의 각 요소들을 결합하여 단 하나의 타입으로 변환
- ex) Array[Int] → Int
```
let num = Array[1, 2, 3, 4, 5]
num.reduce(0, {(sum : Int,next : Int) -> Int  in 
	return sum + next
})
num.reduce(0){$0+$1} // 동일 내용
num.reduce(0,+) // 동일 내용
```

### flatMap
- collection 들을 joined() 하여 새 collection 으로 변환
```
let num = [[1,2,3],[nil,4],[5,nil],[nil,nil]]
num.flatMap{$0} // [1,2,3,nil,4,5,nil,nil,nil]
```


### compactMap
- collection 의 옵셔널 값을 언래핑 하여 새 collection 으로 변환
```
let num = [1, nil, 2, 3]
num.compactMap{$0} // [1,2,3]
// num 의 요소가 nil 이면 제거 후 새 collection 을 만듬
```


