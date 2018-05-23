# Collection
---

#### Array
- 순서가 있음
- 인덱스가 0 부터 시작
- array 선언
	```
	var name : Array<String> = [ "a", "b", "c" ]
	var name2 = ["a","b","c"]
	var name3 = Array<String>(repeating 	: "re",count : n) // re라는 문자열을 n번만큼 array를 만듬
	```
- array 명령어
	
`name.startIndex`
	- array name의 첫번째 인덱스 위치를 가져옴
`name.endIndex`
	- array name의 마지막 요소에 + 1 한 값을 가져옴
`name.contains(index)`
	- name 안에 index 가 있는지 검사 후 있으면 true, 없으면 false
`name.index(of:index)` 
	- name 안에 index가 있는지 검사 후 있으면 index의 위치를 반환
`name.append(index)` 
	- name 맨 뒤에 index를 추가
`name.insert("index", at:n)`
	- name에 n의 위치에 index를 추가
`name.endIndex.advanced(by : n)`
	- endIndex의 위치에서 n 만큼 위치를 반환
`name.remove(at.index)`
	- index 에 해당하는 위치에 있는 요소 삭제
`name.removeall()`
	- array에 있는 모든 요소 삭제

#### Dictionary
- 순서가 없음
- 고유한 key 값과 변수로 구성
- Dictionary 선언
`var dictionary = ["key":"A","key2":"B", "key3","C"]`
- Dictionary 명령어
`dictionary.isEmpty`
- dictionary 가 비어있으면 false 아니면 true
`dictionary["key"]`
- key 값의 value를 가져옴
`dictionary["key"]="index"`		 
- dictinoary 의 key 값에 해당하는 곳의 index 초기화
- 초기화 전의 값을 삭제
`dictionary.updateValue("index", forkey : "key")`
- key 값에 해당하는 index 초기화
- 초기화 전의 값을 바로 지우지 않음
`dictionary["key"]=nil`
 - key 값에 해당하는 index 삭제
 - 삭제 전 값을 바로 삭제
`dictionary.removeValue(forKey="key")`
- key 값에 해당하는 index 삭제
- 삭제 전 값을 보유

#### Set
- 순서 없음
- 요소들이 각각 하나의 고유한 값만을 가짐
- 형태가 array 와 비슷해서 set 키워드를 항상 사용해야 함
- Set 선언
```
let setNum : Set<String> = ["apple", "Orange", "Melon"]
let numbers: Set = [1,2,3,4]
let emptySet = Set<String>()
```

- Set 명령어
`let fileteredSet = numbers.filter{ (element) -> Bool in return element.hasPrefix("i")}`
- filter 요소가 있는지 검사
- hasPrefix 해당 인덱스를 가진 요소가 있는지 검사
`numbers.insert("ddd")`
- Set 에 순서 상관없이 요소 추가
`numbers.remove(1)`
- Set 에서 인덱스 값을 가지고 있는 요소 삭제
`numbers.removeall()`
- 모든 요소 삭제
` numbers.elementsEqual(numbers2)`
- 두 Set 을 비교 요소 뿐만 아니라 순서도 같아야 함
`numbers == numbers2`
- 요소만 같으면 참
`numbers.isSubSet(of:numbers2)`
- numbers 가 numbers2 의 부분집합인지 확인
`numbers.isSuperSet(of:numbers2)`
- numbers 가 numbers2 의 부모집합인지 확인
`numbers.isDisjoint(with:numbers2)`
- 교집합인지 여부
`numbers.union(numbers2)`
- 합집합인지 여부
