# OOP ( Object-Oriented Programming )

```
객체지향 프로그래밍 ( oop ) 이란 캡슐화, 다형성, 상속 을 이용하여 코드의 재사용을 증가시키고, 유지보수를 감소시키는 장점을 얻기 위해서 객체들을 연결시켜 프로그래밍 하는 것
```
> 4대 특징
- 추상화
- 캡슐화
- 상속성
- 다형성

> 객체의 구성
```
class kermit{
	var color : String = "green" // 데이터 (상태)
	
	func eat(){ // 메소드 (행위, 동작)
	}
}
```
- 객체 : 데이터(상태) + 메소드(행위, 동작)

> 함수와 메소드의 차이
- 함수 : 한 줄 이상의 명령어를 스코프 내에서 실행, 특정 작업을 수행, 독립된 기능을 수행하는 단위
- 메소드 : 멤버 함수 , 클래스 안에서 사용하는 함수, 클래스 데이터 타입에 의존적

> Class 와 Object
```
class Dog{
	var color : String!
	var eye Color : String!
	
	func sit(){ }
}

let kermit : Dog = Dog()
kermit.color = "green"
kermit.sit()
```
- class : 추상적인 단계, 틀, 구조 ex) 타꼬야끼 틀
- object : 실체, class의 구현 ex) 매운 타꼬야끼, 치즈 타꼬야끼
