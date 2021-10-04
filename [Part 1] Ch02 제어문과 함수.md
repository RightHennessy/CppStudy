# [Part 1]  Ch02 제어문과 함수

## if-else

```cpp
if(조건){
}
else if(조건 2){
}
else{
}

if(int condition = get_status()){
}
```

else if 와 else 는 생략 가능하다.

if 문 내에서 변수 선언이 가능하다. 

## Switch

```cpp
cin >> number

switch(number){
case 0:
		cout << "0";
		break;
case 1:
		cout << "1";
		break;
case 2:
		cout << "2";
		break;
default:
		cout << "0";
		break;
}
```

## While

```cpp
while(조건){
	문장;
}

do{
	 문장;
}while(조건);
```

둘의 차이점 : 조건식을 루프구조의 시작 vs 마지막

## for

```cpp
for(초기식; 조건식; 증감식){
	문장;
}
```

## 함수

```cpp
반환형 함수이름 ( 매개변수 ) {
		함수의 내용
}
```

- 중복함수 : C++에서는 같은 이름의 함수 생성 가능. 보통 매개변수로 판별 가능

```cpp
int square(int i){
		return i*i;
}

double square(double i){
		return i*i*;
}
```

- 디폴트 매개변수

```cpp
int calc_deposit(int salary = 300, int month = 12);

int main(){
		cout << calc_deposit(200, 6) << endl;
		cout << calc_deposit(200) << endl;      // 자동으로 month = 12
		cout << calc_deposit() << endl;         // 자동으로 salary = 300, month = 12

		return 0;
}

int calc_deposit(int salary, int month){
		return salary*month;
}
```

선언 규칙 : 오른쪽 매개변수부터 정의 가능

```cpp
void func(int p1, int p2, int p3=30);          // OK
void func(int p1, int p2=20, int p3=30);       // OK
void func(int p1=10, int p2=20, int p3=30);    // OK
void func(int p1=10, int p2, int p3=30);       // 컴파일오류
void func(int p1=10, int p2=20, int p3=30);    // 컴파일오류
```

- 인라인 함수

```cpp
inline double square(double i){
		return i*i;
}

int main(){
		cout << square(2.0) << endl;
		cout << square(3.0) << endl;

		return 0;
}
```

함수 호출 시에는 약간의 오버헤드가 발생. 

간단한 함수하면 함수를 호출을 하지 않고 코드를 복사하여 넣어주는 편이 효율적.

inline 이 붙으면 컴파일러가 함수를 생성하지 않고 코드를 호출한 곳에 직접 넣는다. 

→ 오버헤드 사라짐

일반적으로 10번 이상 서로 다른 곳에서 호출되는 경우는 인라인 함수 사용 자제.

가능하면 헤더파일에 존재

함수 매크로(전처리기)와의 차이점

: 매크로는 기계적인 대치라서 잘못 사용될 가능성 있음

: 매크로는 인수의 타입에 관계없이 동작. 인라인 함수는 정해진 타입만을 받음. 

## 변수 선언

C언어에서 지역변수는 블록의 시작에서만 선언 가능

C++ 에서는 지역 변수 선언 위치에 제한이 없음.

- 지역변수 : 블록 안에 선언되는 변수

                        블록이 시작할 때 스택이라 불리는 메모리 공간에 생성, 블록 끝에서 반환 

- 전역변수 : 함수 외부에서 선언되는 변수, 범위는 소스파일 전체
- 정적 지역 변수 : 전역 변수와 같이 프로그램이 시작할 때 메모리에 생성되고 종료시 제거됨.

```cpp
void sub(void){
		int i =0;
		static int s = 0;    // 정적 지역 변수 선언

		i++;
	  s++;
}

int main(){
		sub();      // i=1, s =1
		sub();      // i=1, s =2
		sub();      // i=1, s =3

		return 0;
}
```