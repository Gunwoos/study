# Markdown이란

- GitHub에서 모든 형태의 글쓰기를 꾸미기 위한 용도로 가볍고 사용하기 쉽다
- 웹의 텍스트 스타일을 지정함
- 도큐먼트의 디스플레이를 제어(글씨 굵기 또는 기울기, 이미지 추가, 리스트 만들기 )
- Markdown은 알파벳이 아닌 텍스트이다  ( # 또는  * )
- Gists, 주석, 들여쓰기 에 사용
- .md or .markdown 형식의 파일에 사용 가능


### Markdown의  Syntax guide

> Headers
- " # " : h1
- " ## " : h2
- " ###### " : h6
- #의 개수로 크기 조절( 단  7개부턴 일반 문자로 인식됨)

>Emphasis : 강조

- ‘  *  ’  or  ‘  _  ’  로 italic사용
	- ex)  ```*italic* _apple_```-> *italic* _apple_
- ‘  **  ‘  or  ‘  __  ‘ 로  bold 사용
	- ex) ```**apple** __mac__```->**apple** __mac__
- ex) ```  _aa **bb** aa_  ``` 섞어서 사용 가능 -> _aa **bb** aa_

>Lists : 리스트
#### Unordered : 제일 앞에  ‘ * ’ 나  ‘ – ‘ 를 사용하여 정렬되지 않은 목록을 표현
```
- list
- list
- list
	- list
	- list
- list
```
- list
- list
- list
	- list
	- list
- list

#### Ordered : 제일 앞에 숫자를 사용하여 정렬된 목록을 표현
```
1. list
2. list
3. list
4. list
	1. list
	2. list
5. list
```
> Images : 이미지

- ex) 
```
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)
```
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

> Links : 링크

- ex) 
```[link to Google!](http://google.com)``` -> [link to Google!](http://google.com)

> Blockquotes : 인용구

- ‘ > ‘ 로 사용하여 표현

> Inline code
- " ``` " 적용하고자 하는 문장의 시작과 끝에 작성  
- 한 줄은 " ` " 하나만 사용해도 가능
- ex) ``` `inline code` ```

### GitHub Flavored Markdown

> Syntax highlighting : 구문 강조

-  " ``` " 이나 스페이스바  4번으로 강조

> Task Lists : 작업리스트
- 작업 상태를 볼 수 있다
- [x] :  완전한 상태 ` - [x] `
- [ ] : 불완전한 상태 ` - [] `

> Tables : 행렬

- ‘ – ‘ 와  ‘ | ‘ 로 행과 열을 표현


> SHA(Secure Hash Algorithm) references
- GitHub에서 SHA-1 hash 에 대한 참조는 자동적으로 링크로 변환된다.

> Issue references within a repository
- 문제 참조나 들여쓰기에 대한 숫자는 자동적으로 링크로 변환된다.

> Username @mentions
- @사용자이름 을 사용하여 다른 사용자를 언급하여 글을 보게 할 수 있음

> Automatic linking for URLs
- URL링크는 자동으로 클릭링크로 변환됨

> Strikethrough
- 취소선
- ex) ~~hello~~ -> ` ~~hello~~`

> Emoji
- 이모티콘을 지원함
