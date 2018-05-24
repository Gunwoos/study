# Collection Functions
---
#### Stride
- stride(from:to:by)
```
func stride<T>(from: T, to:T, by: T.Stride)
// from 값으로 시작하여 stride 값만큼 증가하고 to 값을 포함하지 않는 숫자 까지 반복

for i in stride(from:0, to:10, by: 1){
	print(i)
}
```
- stride(from:through:by)
```
func stride<T>(from: T,through: T,by: T.Stride)
//from 값부터 stride 값만큼 증가하면서 through 값을 포함한 숫자까지 반복

for i in stride(from:0, through:10, by:2){
	print(i)
}
```

#### RepeatElement
```
func repeatElement<T>(_ element: T,count n : Int)->Repeated<T>
// 동일 요소를 count값만큼 생성

let zeroes = repeatElement(0, count: 10)
```

#### Zip
```
func zip<Sequence1, Sequence2>(_ sequence1: Sequence1,_ sequence2: Sequence2
) -> Zip2Sequence<Sequence1, Sequence2> where Sequence1 : Sequence, Sequence2 : Sequence

// 두 개의 시퀀스를 통해 새로운 한 쌍의 시퀀스를 생성

let words = ["A","B","C","D"]
let numbers = [1,2,3,4]

for(word, number) in zip(words, numbers){
	print("\(word) : \(number)")
}
```
#### Sequence
```
func sequence<T>(first: T, next: (T) -> T?)
// first 값으로 시작하여 next 값을 lazy 하게 반복하는 순열 생성

var addBy1 = sequence(first:1){$0+1}
print(addBy1.next()!)
print(addBy1.next()!)
```
#### etc
- enumerated()
	- index 값을 부여
		```
		for(idx, num) in [1,5,7,2,9,4].enumerated(){
			print(idx, num)
		}
		```
- sorted()
	- 배열을 정렬
		```
		for(idx, num) in [1,5,7,2,9,4].enumerated().sorted(){
					print(idx, num)
				}
		```
- reversed()
	- 역순
		```
		for(idx, num) in [1,5,7,2,9,4].enumerated().sorted().reversed(){
					print(idx, num)
				}
		```

> enumerated(), sorted(), reversed() 순서에 따라 각각 다른 값이 나옴
