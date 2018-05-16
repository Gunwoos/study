# Swift

### Basic
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
- 상수 : 고정된 값을 가지는 심볼 또는 식별자
-  리터럴
	- 고정된 값으로 표현되는 문자 (데이터) 그 자체
	- 정수/실수/문자/문자열/불리언 리터럴 등
#### 6. Type Conversion
#### 7. Basic Operators
#### 8. Function

