# Optional
- 선택적인
- 값이 있을 수도, 없을 수도 있음
- 변수 or 상수의 값이 nil 일 수도 있음

#### Optional 정의
```
public enum Optional<Wrapped> : ExpressibleByNilLiteral{
	case none
	case some(Wrapped)
	
	public init(_ some: Wrapped)
	// 중략...
}
```
- nil 값일 때는 none 케이스 , 값이 있는 경우는 some 케이스

```
var optionalType1 : String?  // 타입형 뒤에 ? 붙이기
var optionalType2 : Optional<Int> // Optional<타입형> 키워드 사용하기
var optionalType3 = Optional<Int>(10)
var something = nil // (x) Optional 도 타입을 명시해주어야 선언됨
```
- optionalType1 처럼 사용하는게 더 편함


```
var optionalInt : Int? = 0 // optionalInt 라는 optional 변수 선언
optionalInt = nil // optional 변수에는 nil 값을 줄 수 있음

var integer = 1
optionalInt = integer
print(optionalInt) // Optional(1) // 이 출력됨
```
- optional 타입을 nonoptional 타입에 대입 하면 에러
- optional 타입에 nonoptional 타입을 대입 가능

#### If  문 과 Forced Unwrapping
```
var maybeName : String? = "Tom"
var isName : String = maybeName! // ! 를 사용하여 옵셔널 값을 unwrapping 해주어야 nonoptional 변수에 넣을 수 있음
// 단 ! 사용 시 옵셔널 변수를 unwrapping 했을 때 값이 nil 이 아니라는 확신이 있어야 함, 그러므로 가급적 사용하지 않는게 좋다

if maybeName != nil {
	print("name is \(maybeName!)")
}
else{
	print("maybeName == nil")
}
```

#### Optional Binding
- 옵셔널에 값이 있는지 확인하여, 만약 값이 있다면 옵셔널에서 추출된 값을 일정 블록 안에서 사용할 수 있는 상수나 변수로 할당해서 사용할 수 있도록 해줌
- if 문, while문, guard문 과 결합하여 사용
```
var optionalStr : String? = "Hello World"

if let newOptionalStr = optionalStr{
	optionalStr
}
else{
	"It is nil"
}

func doSomething(str : String){
	guard let str = str else {
		return
	}
	print(str)
}

doSomething(str:nil)
```
#### Implicitly Unwrapped Optionals
- 옵셔널 바인딩으로 값을 추출하기 귀찮거나 nil 때문에 에러가 발생하지 않을 것 같다는 확신이 들 때 암시적 추출 옵셔널을 사용
```
var myName : String! = "Samyy"
print(myName)
```
 -_아무리 옵셔널 변수가  nil 이 아니라는 확신이 있어도 nil 값이 될 수도 있으므로 가급적 사용하지 않는 방향이 좋음_

#### Optional Chaining
- 옵셔널을 반복 사용하여 자전거 체인처럼 서로 꼬리를 물고있는 모양
- 프로퍼티나 메소드, 서브스크립트를 호출하고 싶은 옵셔널 변수나 상수 뒤에 ? 를 붙여서 표현
```
class Person{
 var residence : Residence?
}
class Residence{
	var numberOfRooms : Int = 1
	var address: String?
}
let newPerson=Person()
newPerson.residence=Residence()

let roomCount = newPerson.residence?.numberOfRooms

if let roomCount = newPerson.residence?.numberOfRooms {
print("newPerson's residence has \(roomCount) room(s)")
}
else{
	print("Unable to retrieve the number of rooms.")
}
```

#### Array Optional
```
var num1 : Array[Int]? = [1, 2, 3]
var num2 : Array[Int?] = [1, 2, 3]
```
- 위 선언 방식의 차이점은?
	- num1 배열은 배열 자체가 옵셔널
	- num2 배열은 배열안의 요소가 옵셔널

#### Question
> 친구 목록을 출력하는 내용을 구현
friendList(배열) 옵셔널 변수 만들기
func addFriend(name: String) 만들기
printFriendList() 함수 만들기

```
class friend{
	var friendList : Array<String?> = [nil,"tom"]
 
	func addFriend(newFriend : String){
		friendList.append(newFriend)
	}
  
	func printFriendList(){
		print("Friend List")
		for index in self.friendList.startIndex..<self.friendList.endIndex{
			if let myFriend = self.friendList[index]{
				print(myFriend)
			}
			else{
				print("There is no friend's name")
			}
		}
		print("-end-")
	}
}
  
var newFriendList = friend()

//newFriendList.addFriend(newFriend: "james")

newFriendList.printFriendList()
```

