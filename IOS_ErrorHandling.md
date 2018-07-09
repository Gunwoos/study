# Error Handling
---

### Error
1. Simple Domain Error (단순 도메인 오류)
- 명백한 실패가 존재하는 곳에 연산 or 추측에 의한 실행 등으로 발생
	- ex
		- 숫자가 아닌 문자로부터 정수를 파싱
		- 빈 배열에서 요소 꺼내기
- 오류 발견 시 쉽게 처리가 가능함
2. Recoverable (복구 가능한 오류)
- 복잡한 연산 수행 도중 실패가 발생할 수 있지만 사전에 미리 오류를 합리적으로 예측할 수 있는 작업
- NSError or Error 로 에러 처리
- 일반적으로 오류를 무시하지 말고 오류를 처리하는 코드를 작성하는 것이 좋다.
- 오류 내용을 유저에게 알려줌
3. Universal Error (범용적, 보편적 오류)
- 시스템이나 어떤 다른 요인에 의한 오류
 - 이론적으로는 복구가 가능하지만, 어느 지점에서 오류가 발생하는 지 예상하기 어려움
4. Logic Failure
 - Logic 에 대한 오류는 프로그래머의 실수로 발생하는 것으로 프로그램적으로 컨트롤할 수 없는 오류에 해당- 시스템에서 메시지를 남기고 abort()를 호출하거나 Exception 발생

### 4 way to handle errors
- Propagating Errors Using Throwing Functions (Throwing 함수 사용 하기) 
- Handling Errors Using Do-Catch (Do-Catch 문 사용하기) 
- Converting Errors to Optional Values ( 옵셔널 변수 )
- Disabling Error Propagation
