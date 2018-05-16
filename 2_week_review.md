# Swift

### Basic
---
#### 1. Hello, world
> Comment 주석
- // : 한 줄 주석
- /// : 한 줄 주석 + Quick Help Markup
- /* */ : 한 줄 이상 주석

> 출력하기
```
print(3.14)		// 3.14
var num = 1
print(num)		// 1
print("숫자",num)		// 숫자 1
print("숫자 \(num) ")		// 숫자 1
print("숫자 " + String(num))		// 숫자 1		
``` 
> Semicolon ( ; )
- 각 라인의 마지막에 붙는 ; 은 옵션
- 한 라인에 다중 명령을 사용할 때 필수
- ` print(1); print(2); print(3); `
		
#### 2. Constansts and Variables
- 상수와 변수는 현재 어떤 데이터에 대한 상태값, 속성 정보 등을 담고 있는 컨테이너
- 상수 (Constants) : 한 번 설정되면 값 변경 불가
- 변수 (Variables) : 설정한 값을 변경 가능

```
let maxStudent = 30
maxStudent = 20 // error 변경 불가

var numStudent = 15
numStudent = 10 // ok 변경 가능
```
> Naming
- 변수 이름을 정할 때 의미, 방식, 길이 등 확인
- 영어 외에도 유니코드 문자를 포함한 대부분의 문자를 사용해 변수 이름 짓기 가능
- 이모티콘도 지원함
- Swift 에서 사용되는 키워드일 경우 backquote (  ` ) 를 이용해 사용 가능
```
let `let`=1
```
- 변수로 사용 할 수 없는 이름
```
- 같은 스코프 범위 내에서 중복되는 이름
	스코프 <- 같은 영역
	let a = 1
	let a = 2  (x)

	let a = 1
	func add(){
		let a = 2
	} (o)
- 공백
- 수학 기호
- 화살표
- 숫자로 시작하는 이름 ( 시작 외에는 사용 가능 )
```
#### 4. Type Annotation & Type Inference
> Type Annotation ( 타입 명시 )
- 선언 시 자료의 타입을 명확하게 지정
```
let thisYear : Int = 2018
let thisLanguage : String = " Swift 4 "

var num : Double = 3.14
```
> Type Inference ( 타입 추론)
- 변수 선언 시 초기화로 사용되는 값의 타입을 통해 변수의 타입을 추론하여 적용
```
let name = "Dean" // String 로 추론
let char = "A" // String 로 추론 

var age = 24 // Int 로 추론
var weight = 66.7 // Double 로 추론 
```
- swift 는 문자도 문자열로 추론함 그러므로 문자로 지정하고 싶을 때는 타입 명시를 해주어야함
- float 변수 형을 사용 하고 싶을 때 타입 명시 해야함
- `type(of:index)` : index의 타입 확인 가능

#### 5. Literals & Types
- 상수 : 고정된 값 (메모리 주소) 을 가지는 심볼 또는 식별자
-  리터럴
	- 고정된 값으로 표현되는 문자 (데이터) 그 자체
	- 정수/실수/문자/문자열/불리언 리터럴 등

> Typealias
- 문맥상 더 적절한 이름으로 기존 타입의 이름을 참조하여 사용하고 싶을 경우 사용
`typealias type name = type expression`

ex) 
```
typealias AudioSample = UInt16

var maxAmplitudeFOund = Audio.Sample.min

```

#### 6. Type Conversion (타입 변환)
```
var num = 10
var doubleNum=Double(num) // Double로 변환

var i = 20
var j = 5.6
var k = 0.0

k = j * Double(i) // int 와 double 연산 하는 방법
```
- 서로 다른 타입은 비교하거나 연산 불가
```
let h = UInt8(25)
let x = 10 * h
type(of:x) // UInt8 로 추론
```
- 위 코드가 실행되는 이유는 10 이라는 상수가 타입이 명시 되어있지 않기 때문에 h의 타입인 UInt8 로 추론되어 * 연산이 되기 때문

> 양수 사용 시 Int / UInt 중 어느 것이 좋을까?
- Int - why?
	- 연산 중 음수가 나오는 경우도 있으므로 안전성이나 사용성, 타입 추론, 변환 등 에서 Int 가 유리함
- magnitude 와 abs 의 차이점
	- magnitude는 UInt 으로, abs는 Int 로
	- abs 가 절대값을 구할 때 더 편함, abs는 항상 같은 타입으로 반환해주기 때문에


#### 7. Basic Operators
> Unary Operator (단항 연산자)
- `-a // 항 하나만으로 연산 가능`

> Prefix (전위 표기법)
- `-a // 변수 앞에 연산자를 표기`

> Postfix (후위 표기법)
- `c! // 변수 뒤에 연산자를 표기`

> Binary Operator (이항 연산자)
- `a + b // 항이 두가지 있어야 연산 가능`

> Infix (중위 표기법)
- `a + b // 항 사이에 표기`

> Ternary Operator (삼항 연산자)
- Swift 에서 삼항 연산자는 단 하나
	- `a > 0 ? "positive" : "negative" // a 가 0 보다 크면 positive 작으면 negative`

> Assignment Operators
- Basic assignment operator
	- `var value = 0`
- Addition assignment operator
	- `value = value + 10`
- Subraction assignment operator
	- `value = value - 5`
- Multiplication assignment operator
	- `value = value * 2`
- Division assignment operator
	- `value = value / 2`
- Modulo assignment operator
	- `value = value % 2`
- Compound Assignment Operators
	```
	value += 10
	value -= 5
	value *= 2
	value /= 2
	value %= 2
	```

> Overflow
- overflow 연산하고 싶을 때 & 사용
	- ` var add : Int8 = Int8.max &+ 1`

> Comparison Operators
- Equal to operator
	- `a == b`
- Not equal to operator
	- `a != b`
- Greater than operator
	- `a > b`
- Greater than or equal to operator
	- `a >= b`
- Less than operator
	- `a < b`
- Less than or equal to operator
	- `a <= b`

> Logical Operators
- Logical AND Operator
	- 둘 다 참이여야 참
	```
	true && true //t
	true && false //f
	false && true //f
	false && false //f
	```
- Logical OR Operator
	- 둘 중 하나만 참이어도 참
	```
	true || true //t
	true || false  //t
	false || true //t
	false || false //f
	```
- Logical Negation Operator
	- 부정
	```
	!true //f
	!false //t
	```
>Range Operators
- Closed Range Operator
	- `0...100` :  0~100 
- Half-Open Range Operator
	- `0..<100` : 0~99
- One-Sided Ranges
	- `1...` : 1~
	- `...100` : ~100까지
	- `..<100` : ~99까지

#### 8. Function
>일련의 작업을 수행하는 코드 묶음을 식별할 수 있는 특정한 이름을 부여하여 사용하는 것
- Input 과 Output 이 모두 있는 것 (Function)
	```
	func getNum(num:Int)-> Int{ // getNum() Int 형을 받음
		var a : Int = 10
		return a // output a 
	}
	```
- Input 이 없고 Output 만 있는 것 (Generator)
	```
	func getNum()->Int{

		return a
	}
	```
- Input 이 있고 Output 은 없는 것 (Consumer)
 	```
	func getNum(num : Int){

	}
	```
- Input 과 Output 이 모두 없는 것
 	```
	func getNum(){

	}
	```

>Argument Labels and Parameter Names
```
func someFunction(firstParameterName : Int, secondParameterName : Int){
	print(firstParameterName, secondParameterName)
}
```
- Argument Labels : 함수 밖에서 불리는 이름 
	ex) firstParameterName, secondParameterName 
- Parameter Names : 변수 타입
	ex) Int Double String etc...

> Parameter
- 매개변수 = 인자 = Parameter
- 인수를 담는 변수의 한 종류로서 해당 함수 내부 스코프에만 영향
- 대부분 call by value 가 기본
- call by reference 는 호출할 때 사용한 전달인자에까지 영향

> Argument
- 전달인자 = 인수 = 실인수 = Argument
- 함수 호출 시 그에 필요한 데이터를 전달


Q. Argument Labels 와 Parameter Names 를 다르게 하는 이유?
`- 동일하게 지정하면 함수 밖에서 사용하거나 협업하는 타인이 코드를 볼 때 무슨 내용인지 이해하기 쉽지 않기 때문에 이름을 다르게 하여 코드 내용의 이해를 돕기 위해 `

>Omitting Argument Labels
- Argument Label 의 생략이 가능한 경우 _ 를 사용하여 생략
```
func someFunction(_ firstParameterName : Int, secondParameterName : Int){

}
someFunction(10, secondParameterName: 29)
```

>Default Parameter Values
- 기본값 주기
	```
	func someFunction(first : Int = 10, second : Int){

	}

	someFunction(second : 20) // first에 자동으로 10이 들어감
	```

>Variadic Parameters
- 같은 타입의 변수를 하나 이상 입력할 때 사용
```
func getGrade(_ score : Double...)->Double{
	var total=0.0
	for number in score{
		total+=number
	}
	return total/Double(score.count)
}

getGrade(4.5, 4.0, 4.4, 4.1)
```

>Nested Functions
- 외부에는 숨기고 함수 내부에서만 사용할 함수를 중첩하여 사용 가능
```
func outsideFunction(){
	func inside1Function(){

	}
	func inside2Function(){
	
	}

	if {
		inside1Function()
	}
	else {
		inside2Function()
	}
}
```

#### 9. Conditional Statements
>If문
- if문 형식
	```
	if 조건 {
		코드
	}
	else if 조건 {
		코드
	}
	else {
		코드
	}
	```

- if문 에서는 " , " 는 AND 랑 의미가 동일

>switch문
- switch문 형식
	```
	switch index{
	case index1:
		index1 에 관한 코드
	case index2:
		index2 에 관한 코드
	case index3:
		index3 에 관한 코드
	default:
		default 에 관한 코드
	}
	```
- character 타입도 사용 가능
```
let alphabet: Character = "a"

switch  alphabet {
case  "a":
	print("The first letter of the alphabet")
case  "z":
	print("The last letter of the alphabet")
default: // Invalid, the case has an empty body
	break//  print("Some other character")
}
```
- Interval Matching
```
let approximateCount = 30

switch  approximateCount {
case 0...50:
	print("0 ~ 50")
case  51...100:
	print("51 ~ 100")
default:
	print("Something else")
}
```
- Compound Cases
```
case "a", "e", "c"
```
- switch 에서는 " , " 는 OR 을 뜻한다

> Value binding
```
let stillAnotherPoint = (9, 0)

switch  stillAnotherPoint {
case (let distance, 0), (0, let distance): 
	print("On an axis, \(distance) from the origin")
default:
	print("Not on an axis")
}
```

- 변수명으로 변수 값을 대신함으로 써 변수명을 사용한 자리는 신경쓰지 않겠다는 것을 의미

>no default case
```
let isTure:true

switch isTure{
case true:
	print("t")
case false:
	print("f")
}
```
- ture or false 는 값이 둘중 하나 이므로 default 를 사용하면 error 가 난다

>fallthrough
-swift의 switch문은 break가 생략되어있어 break 기능을 사용하고 싶지 않을 때 사용
```
switch index{
case 1:
	print("1")
	fallthrough
default:
	print("2")
}
```


> guard문

- guard문 형식

```
func update(age:Int){
	guard 0...100 ~= age, age == 100
	else {
		return
	}
	print("Pass")
}
```

- if문 코드의 간결화

#### 10. Loops


#### 11. Tuples


#### 12. ControlTransfer


#### 13. Enumerations 
