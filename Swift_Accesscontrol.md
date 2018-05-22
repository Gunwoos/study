
# Access control
---
```
 다른 모듈의 코드 or 다른 소스 파일 등으로부터 접근을 제한하는 것
세부 구현 내용을 숨기고 접근할 수 있는 인터페이스 지정이 가능
```
- Module (모듈)
	- import 를 통해 다른 모듈로부터 호출이 가능한 하나의 코드 배포 단위
	- ex) Library / Framework / Application 등
- Source FIle (소스파일)
	- 모듈 내에 포함된 각각의 swift 소스 코드 파일

#### Access Levels
```
private(제한) < fileprivate < internal < public < open (개방)
```
- private
	- 해당 스코프 범위에서만 접근 가능
- fileprivate
	- 해당 파일에서만 접근 가능
- internal
	- 해당 모듈러에서만 접근 가능
- public
	- 다른 모듈에서도 접근 가능
- open
	- 다른 모듈에서 접근 가능 + Subclass, Override 가능
