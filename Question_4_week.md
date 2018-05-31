```
import UIKit

class Pet{
	enum petType {
		case dog, cat, snake, pig, bird
	}
	var type : petType
	var age : Int

	init() {
		self.type = .dog
	self.age = 0
	}

	init(_ petType : petType,_ petAge : Int) {
		self.type = petType
		self.age = petAge
	}
}

// 강아지 Practice

let myPet = [Pet(.dog, 13),Pet(.dog, 2),Pet(.dog,7),Pet(.cat,9),Pet(.snake,4),Pet(.pig,5)]

//pactice 1. 강아지들의 나이를 합산한 결과를 반환
func addPetAge(_ pet: Array<Pet>,_ petType : Pet.petType){
	let newPet = pet.filter({$0.type == petType})
	var sum = 0

	newPet.forEach{dog in
		sum = sum + dog.age
	}
	print(sum)
}

addPetAge(myPet, .dog)
addPetAge(myPet, .cat)
print("")

//practice 2. 모든 펫의 나이를 1씩 더하기

print("\(myPet.map({ $0.age+1}))\n")

let array = Array(1...10)

// practice 1. 배열의 각 요소 * index 값을 반환하는 함수
print("\(array.enumerated().map{$0*$1})\n")

// practice 2. 배열 요소 중 짝수만 반환하기
print("\(array.filter{$0%2==0})\n")

//practice 3. 배열의 모든 값을 더하여 반환하기
print("\(array.reduce(0){(sum, next)in sum+next })")

// practice 4. 1~3 을 한번에 하기
print("\(array.enumerated().map{$0*$1}.filter{$0%2==0}.reduce(1){(sum,next) in sum+next})\n")
```
