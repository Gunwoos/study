# Question
- 두 개의 정수를 입력받아 두 수를 하나로 합친 결과를 출력하는 함수 (1, 5 입력 시 15 반환)
- 문자열 두 개를 입력받아 두 문자열이 같은지 여부를 판단해주는 함수
- 학점을 입력받아 각각의 등급을 반환해주는 함수 (4.5 = A+,  4.0 = A, 3.5 = B+ ...)
- 여러 등급을 입력받아 그 학점의 평균을 반환해주는 함수
- 윤년 구하기 (2월 29일이 있는 해.  매 4년 마다 윤년. 매 100년 째에는 윤년이 아님. 매 400년 째에는 윤년)
- 세 수를 입력받아 세 수의 곱이 양수이면 true , 음수이면 false 반환하는 함수
- 특정한 달을 숫자로 입력 받아 문자로 반환해주는 함수 (1 = "Jan" , 2 = "Feb")```

1.
```
func addNum(_ num1 :Int,_ num2 :Int){
    print(String(num1) + String(num2))
}
addNum(1,2)
```

2.
```
func checkStr(_ Str1:String,_ Str2:String){
    if Str1==Str2{
        print("true")
    }
    else{
        print("false")
    }
}
checkStr("apple", "e")
```

3. and 4.

```
func getGrade(_ score:Double...)->Double{
    var total=0.0

    for newScore in score{
        total += newScore

        if newScore>=4.5{
            print("A+")
        }
        else if newScore>=4.0 && newScore<4.5{
            print("A")
        }
        else if newScore>=3.5 && newScore<4.0{
            print("B+")
        }
        else if newScore>=3.0 && newScore<3.5{
            print("B")
        }
        else if newScore>=2.5 && newScore<3.0{
            print("C+")
        }
        else{
            print("재수강")
        }
    }
    print("평균 학점 : ",total/Double(score.count))
    return total/Double(score.count)
}
getGrade(2.5, 1.0, 4.5, 4.0, 3.0, 3.7, 4.3)
```

5.
```
func checkYear(_ year:Int){
    if year%4==0{
        if year%100==0{
            if year%400==0{
                print("윤년")
            }
            else{
                print("평년")
            }
        }
        else{
            print("윤년")
        }
    }
    else{
        print("평년")
    }
}

checkYear(196)
checkYear(200)
checkYear(400)
```

6.
```
func checkNegative(_ num1:Int,_ num2:Int,_ num3:Int)->Bool{
    var isTrue = true

    if (num1*num2*num3)>=0{
        isTrue=true
    }
    else{
        isTrue=false
    }
    return isTrue
}

checkNegative(15, -15, -15)
```

7. 숫자를 달로 리턴해주는 함수
```
func getNum(_ num:Int)->String{
    if num==1{
        
    }
    else if num==2{
        
    }
    else if num==3{
        
    }
    else if num==4{
        
    }
    else if num==5{
        
    }
    
    return "No"
}
```


# Question
for , while , repeat - while 등을 활용하여 아래 문제들을 구현해보세요.
- 1 ~ 9 사이의 숫자를 입력받아 해당 숫자에 해당하는 구구단의 내용을 출력하는 함수
- 정수 하나를 입력받아 그 수의 Factorial 을 구하는 함수
- 정수 두개를 입력받아 첫 번째 수를 두 번째 수의 횟수만큼 곱한 값을 반환하는 함수
- 정수 하나를 입력받아 각 자리수 숫자들의 합을 반환해주는 함수
- 100 이하의 자연수 중 3과 5의 공배수를 모두 출력하는 함수
- 정수 하나를 입력받아 그 정수의 약수를 모두 출력하는 함수
- 2 이상의 정수를 입력받아, 소수인지 아닌지를 판별하는 함수
- 정수를 입력받아 입력받은 수에 해당하는 자리의 피보나치 숫자를 반환하는 함수


1. 구구단
```
func mul(_ num1:Int,_ num2:Int){
    for index in 1...num2{
        print("\(num1) * \(index) = \(num1*index)")
    }
}
mul(2,9)
```


2.Factorial
```
func factorial(_ num1:Int){
    var sum=1
    for index in (1...num1).reversed(){
        sum*=index
    }
    print(sum)
}

factorial(3)
```

3.
(x)


4.
```
func addNum(_ num : Int)-> Int{
    var count = 1
    var sum = 0
    var newNum = 0
    var firstNum:Int
    firstNum=num

    while num > count{
        count *= 10
    }

    while count >= 1{
        newNum = firstNum/count
        sum += newNum
        firstNum = firstNum - (newNum * count)
        count /= 10
    }

    return sum
}

addNum(123)
addNum(1)
addNum(6463)
```

5.

```
func getNum(_ num1:Int,_ num2:Int,_ min:Int,_ max:Int){
    var minNum:Int; minNum=min
    var maxNum:Int; maxNum=max
    var checkNum:Int=0

    for index in minNum...maxNum{
        if index%num2==0{
            if index%num1==0{
                checkNum+=1
                print(index)
            }
        }
    }
    if checkNum==0{
        print("해당 범위 내에 최소 공배수 없음")
    }
    else{
        print("해당 범위 내에 최소 공배수 갯수 : ",checkNum)
        print()
    }
}

getNum(3,5,1,100)
getNum(15,17,1,50)
```

6.

```
func getNum(_ num:Int){

    for index in 1...num{
        if num%index==0{
            print(index)
        }
    }
}

getNum(15)
```

7.

```
func checkNum(_ num:Int){
    var check:Int=0

    if num<2{
        print("입력 받은 수가 2보다 작습니다.")
    }
    else{
        for index in 2...(num-1){
            if num%index==0{
                check+=1
            }
        }
        if check==0{
            print(" \(num) : 소수 입니다")
        }
        else{
            print(" \(num) : 소수가 아닙니다")
        }
    }
}

checkNum(17)
checkNum(100)
```

8.

```
func checkFibonacci(_ num:Int)->Int{
    var sum:Int=0
    var firstNum=0
    var secondNum=1

    if num<=0{
        print("0 이하의 수 입니다")
        return 0
    }
    else if num==1{
        sum=0
    }
    else if num==2{
        sum=1
    }
    else{
        for _ in 1...(num-2){
            sum=firstNum+secondNum
            firstNum=secondNum
            secondNum=sum
        }
    }
    return sum
}

checkFibonacci(0)
checkFibonacci(1)
checkFibonacci(2)
checkFibonacci(5)
checkFibonacci(7)
```
