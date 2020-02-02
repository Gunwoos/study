# OOP ( Object-Oriented Programming )
---

```
객체지향 프로그래밍 ( oop ) 이란 캡슐화, 다형성, 상속 을 이용하여 코드의 재사용을 증가시키고, 유지보수를 감소시키는 장점을 얻기 위해서 객체들을 연결시켜 프로그래밍 하는 것
```
- 객체의 구성
	```
	class kermit{
		var color : String = "green" // 데이터 (상태)

		func eat(){ // 메소드 (행위, 동작)
		}
	}
	```
	- 객체 : 데이터(상태) + 메소드(행위, 동작)

- 함수와 메소드의 차이
	- 함수 : 한 줄 이상의 명령어를 스코프 내에서 실행, 특정 작업을 수행, 독립된 기능을 수행하는 단위
	- 메소드 : 멤버 함수 , 클래스 안에서 사용하는 함수, 클래스 데이터 타입에 의존적

- Class 와 Object
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
	
- 4대 특징
> Abstraction (추상화)
```
protocol Human {
	var name: String { get }
	var age: Int { get }
	var gender: String { get }
	var height: Double { get }
	func sleep()
	func eat()
	func walk()
}
```
- 대상의 불필요한 부분을 무시하여 복잡성을 줄이고 목적에 집중할 수 있도록 단순화 시키는 것 ( 디자인 레벨)

> Encapsulation (캡슐화)
```
class Person{
	private birthday : Int = 950228
	
	private func study(){
		code
	}
	func goSchool(){
		study()
	}
}
```
- 구현 레벨
- 데이터 은닉화 : 연관된 상태와 행동으로 하나의 단위( 객체 ) 로 캡슐화
- 정보 은닉화 : 외부에 알릴 정보만 알리고 보안을 위한 정보는 숨김

> Inheritance (상속)
```
class car{
	var wheel : Int = 4
	func move(){
	}
	func stop(){
	}
}
class autoCar : car {
		
}
class  manualCar: car {

}
final class bus : manualCar {

}
```
- 하나의 클래스( 부모 클래스)를 다른 클래스가 상속받아 부모클래스의 속성과 기능을 동일하게 사용하는 것
- 재사용과 확장성 때문에
- swift 에서는 다중 상속을 비허용
- final 은 선언한 클래스를 상속 못하게 하는 메소드


> Polymorphism (다형성)

- 동일한 요청에 대해 각각 다른 방식으로 응답할 수 있도록 만드는 것
- Overriding (오버라이딩)
	- 상위 클래스의 메소드를 재정의 하여 사용
	- 동일 요청이 객체에 따라 다르게 응답
	```
	class Shape{
		var color = UIColor.black
		init(color:UIColor){
			self.color=color
		}

		func draw(){
			print("draw shape")
		}
	}

	class Rectangle : Shape{
		override var color : UIColor{
		get {
			return UIColor.red
		}
		set{
			self.color = UIColor.red
		}
		override func draw(){
			super.draw()
	
			print("draw rect")
		}
	}
	
	let rect = Rectangle(color: UIColor.blue)
	rect.draw()
	```
	- super 메소드는 부모클래스의 함수르 호출하여 사용
	
	
- Overloading (오버로딩)
	- 동일한 이름의 메소드가 매개변수의 이름,  타입, 개수에 따라 다르게 동작
	```
	class circle{
	    var radius : Int = 0
	    var color : UIColor
	    init(){
		self.radius = 10
		self.color = UIColor.black

	    }
	    func getCircle(){
		self.radius = 10
		self.color = UIColor.black
	    }
	    func getCircle(_ :Int = 10,color:UIColor){
		self.radius = 10
		self.color = color
	    }
	    func getCircle(radius : Int,_ :UIColor=UIColor.black){
		self.radius=radius
		self.color = UIColor.black
	    }
	    func getCircle(radius:Int,color:UIColor){
		self.radius=radius
		self.color=color
	    }
	}

	var newCircle = circle()

	newCircle.getCircle()
	newCircle.getCircle(color: UIColor.brown)
	newCircle.getCircle(radius: 20)
	newCircle.getCircle(radius: 30, color: UIColor.red)
	```
	
	

