# Closure
---
#### 클로저란
> 함수지만 함수의 모습이 아닌, 하나의 블록
#### why
> 굳이 구현할 필요가 없는 함수에 대하여  잠깐만 사용하고 버리려고
#### 클로저의 모양
- 이름을 가지며, 어떤 값도 가지지 않는 전역 함수
- 이름을 가지며, 다른 함수 내부의 값을 획득할 수 있는 중첩된 함수
- 이름이 없고, 주변 문맥에 따라 값을 획득할 수 있는 축약 문법

#### 클로저의 특징
- 문맥을 통해 매개변수와 리턴값의 타입을 문맥을 통해 유추 가능 -> 타입 생략이 가능함
- 축약하여 단 한줄이 된 경우 리턴 값으로 취급 된다
- 축약된 전달인자 사용 가능
- 후행 클로저

#### 기본 클로저
```
name.sorted(by:{(first: String, second, String) -> Bool in
	return first > second
})
```
#### 후행 클로저
```
name.sorted(){(first:String, second:String) -> Bool in
	return first > secont
}
```
> 맨 마지막 클로저만 () 가 생략이 가능
```
name.sorted{(first: String, second: String) -> Bool in
	return first > second
}
```
> 타입 생략
```
name.sorted{(first, second) in
	return first > second
}
```
> 변수명에 대하여 단축인자를 제공

- 첫 전달인자부터 $0, $1, $2, $3, ...
```
name.sorted{ $0 > $1 }
```
> 반환값을 가지는 클로저가 코드가 단 한줄이라면
- return 이 생략이 가능
```
name.sorted(by: >)
```
