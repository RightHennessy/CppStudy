# [Part 1]  Ch03 배열과 포인터

- (정리 필요) 참조자
    
    함수에 인자 전달 시 swap(&a, &b) → swap(int *a, int *b){함수내용}할 필요 없이
    
    swap(a,b) → swap(int &a, int &b){함수내용} 사용하면 해결
    
    +) 항상 값 변경을 방지하고 싶으면 const 붙여 해결하면 된다
    
- (정리 필요) call-by-value vs call-by-reference

```cpp
// 배열 초기화
const int STUDENTS = 10;
int grade[STUDENTS];

// 2차원 배열
const int ROWS = 3;
const int COLS = 3;
```

for문 내에서의 포인터 선언

```cpp
#include <iostream>
using namespace std;

int main(void){

	const int STUDENT = 5;
	int grade[STUDENT] = {10, 20, 30, 40, 50};

	for(int *p = grade, *pend = grade + STUDENT; p != pend; p++)
		cout << *p << " ";

	return 0;
}
```

배열을 함수로 전달

```cpp
#include <iostream>
using namespace std;

int get_average(int score[], int n);
void increment(int score[], int n);

int main(void){

	const int STUDENT = 5;
	int grade[STUDENT] = {10, 20, 30, 40, 50};
	int avg;

	increment(rade, STUDENTS)
	avg = get_average(grade, STUDENTS);
	cout << "평균은" << avg << "입니다.\n";

	return 0;
}

// 배열을 그대로 전달
void increment(int score[], int n){
	int i;
	
	for(i=0;i; i<n;i++)
		++score[i];
}

// const 붙으면 원본 배열 변경 불가
int get_average(const int score[], int n){
	int i;
	int sum = 0;
		
	for(i=0;i<n;i++)
		sum += score[i];

	return sum / n;
}
```

comst 와 포인터

```cpp
// double 상수를 가리키는 포인터 -> p의 값은 변경 가능, p가 가리키는 값은 변경 불가능
const double *p;
double d = 1.23;
p = &d;    //가능
*p = 3.14; // 컴파일 오류

// double을 가리키는 포인터 상수 -> p값 변경 불가능
double const *p
```

동적메모리 할당

```cpp
int main(){
		int *pi;
	
		// 동적메모리 할당
		pi = new int[100];

		for(int i = 0; i <100; i++)
				*(pi+i) = 0;
		
		// 동적 배열 반납
		delete[] pi;

		return 0;
}
```

문자열 라이브러리 함수

`strlen(s)`  문자열 s의 길이

`strcpy(s1, s2)`  s2를 s1에 복사

`strcat(s1, s2)`  s2를 s1 끝에 붙여넣기

`strcmp(s1, s2)`  s1과 s2를 비교

`strncpy(s1, s2, n)`  s2의 최대 n개의 문자를 s1에 복사

`strncat(s1, s2, n)`  s2의 최대 n개의 문자를 s1 끝에 붙여넣기

`strncmp(s1, s2, n)`  최개 n개의 문자까지 s1과 s2 비교

`strchr(s, c)`  문자열 s 안에서 문자 c 찾기

`strstr(s1,  s2)`  문자열 s1 안에서 문자열 s2 찾기

문자열 입력 받기

```cpp
char str[80];

cin >> str;

while(str[i] != 0){
	i++;
}
```