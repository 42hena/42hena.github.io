---
published: false
---
# 1-1 printf와 scanf를 대신하는 입출력 방식
## 문자열 "Hello World"의 출력
```c++
HelloWorld.cpp
#include <iostream>

int main(void)
{
    int num = 20;
    std::cout << "Hello World!" << std::endl;
    std::cout << "Hello "<< "World!" << std::endl;
    std::cout << num << ' ' << 'A';
    std::cout << ' ' << 3.14 << std::endl;
    return (0);
}

<실행 결과>
Hello World!
Hello World!
20 A 3.14
```

- 헤더파일 선언문 #include <iostream>
- std::cout과 << 연산자를 이용한 출력
- << 연산자를 이용한 개행


HelloWorld.cpp <파일 참고>
### 헤더파일 선언문 #include <iostream>
**c언어**   - scanf 및 printf를 사용하기 위해서 <stdio.h>를 사용함   
**c++언어** - cin, cout 그리고 endl를 사용하기 위해서 <iostream>을 사용한다.

헤더파일 확장자는 **.h**이지만, C++에서 프로그래머가 정의하는 헤더파일의 선언이 아닌, **표준 헤더파일의 선언에서는 확장자를 생략하기로 약속**되어 있다.

#### [참고] 새로운 라이브러리 등장
**<iostream.h>**에서 **<iostream>**를 사용
1. 과거의 표준 라이브러리와 새로운 표준 라이브러리의 구분
2. 새로운 표준 라이브러리를 사용하는 형태로 소스코드를 쉽게 변경할 수 있게 함

### std::cout과 << 연산자를 이용한 출력
- std::cout<< '출력대상';

출력 대상의 위치에는 무엇이든 올 수 있다.  
(정수, 실수, 문자열, 변수) 또한 c언어의 printf와 달리 서식문자를 이용해서 지정하지 않아도 적절히 이뤄진다.

### << 연산자를 이용한 출력 대상의 연이은 표현과 개행
- << 는 연산자

<< 연산자를 이용시에 std::cout << '출력대상' << '출력대상2' << '출력대상3';  
과 같이 연속으로 출력 가능하다

## scanf를 대신하는 데이터의 입력
```c++
SimpleAdder.cpp
#include <iostream>

int main(void)
{
    int val1;
    std::cout<< "First num input: ";
    std::cin >> val1;

    int val2;
    std::cout<< "Second num input: ";
    std::cin >> val2;

    int result = val1 + val2;
    std::cout << "Add result: " << result << std::endl;
    return 0;
}

실행 결과
First num input: 3
Second num input: 5
Add result: 8
```
SimpleAdder.cpp
- 키보드로부터의 데이터 입력에도 헤더파일 선언문 #include <iostream>
- 키보드로부터의 데이터 입력에는 std::cin과 >> 연산자가 사용된다.
- 변수의 선언은 어디서든 가능하다.

### 데이터의 입력에 사용되는 std::cin과 >> 연산자
- std::cout<< '변수';

c++에서는 데이터의 입력도 데이터의 출력과 마찬가지로 별도의 포맷 지정이 필요 없다.

### C++의 지역변수 선언
c++에서의 지역변수 선언은 함수 내 어디든 가능하다.
```c++
c언어
int num;(최상단)
...
for (num = 0 ; num < 10 ; num++){}

c++언어
...
for (int num = 0 ; num < 10 ; num++){}
```
  

```c++
BetweenAdder.cpp
#include <iostream>

int main(void)
{
    int val1, val2;
    int result = 0;
    std::cout << "Two number input: ";
    std::cin >> val1 >> val2;

    if (val1 < val2)
    {
        for (int i = val1 + 1 ; i < val2 ; i++)
            result += i;   
    }
    else
    {
        for (int i = val2 + 1 ; i < val1 ; i++)
            result += i;
    }

    std::cout << "Between Two number Integer Sum: " << result << std::endl;
    return 0;
}

실행결과
Two number input: 3 7
Between Two number Integer Sum: 15
```
- cin도 마찬가지로 연속적인 데이터의 입력이 가능하다.

#### 배열 기반의 문자열 입출력
```c++
StringIO.cpp
#include <iostream>

int main(void)
{
    char name[100];
    char lang[200];

    std::cout << "What is your name? ";
    std::cin >> name;

    std::cout << "What is your favorite language? ";
    std::cin >> lang;

    std::cout << "My name is " << name << ".\n";
    std::cout << "My favorite language is " << lang <<"." << std::endl;    
    return 0;
}

실행결과
What is your name? Young
What is your favorite language? C++
My name is Young.
My favorite language is C++.
```
- 문자열도 동일