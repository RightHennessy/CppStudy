# [Part 1]  Ch01 기초사항

## #include <iostream>

헤더파일 전처리기

입출력을 위한 cin, cout 등의 객체를 사용하기 위해 필요

기존 C언의 헤더파일에는 .h 사용, C++에서 추가된 헤더파일에는 사용하지 않음

## using namespace std;

C++에서 이름을 사용할 때에 반드시 "공간:이름"와 같이 공간명을 이름 앞에 붙여야 함

원칙적으로는 다음과 같지만, 매번 붙이기에 번거롭기 때문에 using 지시어를 사용

```cpp
std::cout << "Hello World!" << endl;
```

## #include <string>

string 타입을 이용하기 위해서 선언해야하는 헤더

```cpp
#include <iostream>
#include <string>
using namespace std;

int main(void) {
		string s1 = "Good";
		string s2 = "Morning";
		string s3 = s1 + " " + s2 + "!\\n";

		cout << s3;

		return 0;
}
```

문자열은 + 을 이용해 쉽게 이어붙일 수 있다. 

## 기호상수 const

보통의 상수에는 변수와 달리 이름이 없다. 

이 때 상수에 이름을 붙이는 방법이 기호 상수를 이용하는 것이다. 

```cpp
const double TAX_RATE = 0.25;
```

## 출력 cout

```cpp
cout << 100;

int i = 100;
cout << "변수 i의 값은";
cout << i;
cout << "입니다.";
cout << endl;

// 한줄로 작성
cout << "변수 i의 값은" << i << "입니다." << endl;
```

## 입력 cin

```cpp
int i;
cin >> i;

double f;
cin >> f;

string name;
cin >> name;
```

## 연산자

- 산술 연산자  + -  * / %
- 관계 연산자  == != > < >= <=
- 논리 연산자 && || !

```cpp
int x=0, y=0, z=0;
bool r1, r2;

r1 = (x==y);
r2 = (x > y);

cout.setf(cout.boolalpha);     
cout << r1 << endl;
cout << r2 << endl;

cout << (x = y = z = 1) << endl;  //ture : 한번에 비교 가능. 오른쪽에서 왼쪽으로
```

`setf`  bool 변수의 값을 1과 0 대신에 true 와 false로 출력