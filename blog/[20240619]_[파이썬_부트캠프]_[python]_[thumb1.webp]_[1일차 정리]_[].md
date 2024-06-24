# 1일차 강의 정리

## **오늘의 상식**
- 엔비디아, MS 애플 제치고 첫 시총 1위 달성
- slop: 원래는 쓰레기, 오물이란 뜻이지만, 오류가 많은 AI 생성물을 뜻하기도 함.

## **코랩 단축키**

### **생성 방법**
- Shift + Enter 실행 후 다음 칸으로 이동
- Ctrl + Enter 실행
- Alt + Enter 실행 후 생성
- Ctrl M A : 코드 셀 위에 삽입
- Ctrl M B : 코드 셀 아래 삽입
- Ctrl M D : 셀 지우기
- Ctrl M Y : 코드 셀로 변경
- Ctrl M M ; 마크다운 셀로 이동
- Ctrl M Z : 실행 취소

### **수정 방법**
- (자주)`Ctrl(Command)` + `Alt(Option)` + 화살표위아래 : 동시 수정
- (자주) `Ctrl(Command)` + D : 같은 단어 찾아 동시 수정
- `Ctrl(Command)` + `Shift` + L : 동일 단어를 전체로 찾아 동시 수정
- `Alt(Option)` + `Shift` + 화살표위아래 : 해당내용을 위나 아래 복사해서 붙여넣기
- `Alt(Option)` + 화살표위아래 : 해당 내용을 위나 아래로 보내기
- (자주) `Ctrl(Command)` + `Alt(Option)` + 화살표위아래 : 위아래 동시 수정
- (자주) Home, End : 문장의 양 끝
- (필수) `Ctrl(Command)` + `/` : 주석
- (필수) `Shift`(`Command`) + `Del` : 한 줄 지우기
- (필수) `Tab`, `Ctrl` + `]` : 들여쓰기
- (필수) `Shift` + `Tab`, `Ctrl` + `[` : 내어쓰기

## **마크 다운**
- '#'의 갯수로 제목의 수준을 정함
- '*', '_'을 통해 _글자 기울이기_ 가능, 2개 사용 시 __볼드__
- 순서 있는 목록
    1. Hello
    2. World
- 순서 없는 목록은 '*', '-' 표시를 통해 작성
- **링크**: \[텍스트](URL) 형식을 사용하여 하이퍼링크 삽입
- **이미지링크**: !\[대체 텍스트](URL) 형식을 사용하여 하이퍼링크 삽입
- 인용문 '>', 중첩된 인용문

_워렌 버핏_
> 첫번째 돈을 잃지 마라
>> 두번째 첫번째 원칙을 잊지 마라
- 구분선 만들기 '---'

---
구분선
---

- 취소선 만들기 \~~문자열~~

~~취소선~~

## **주석**
- 목적: 코드의 이해를 돕고 코드의 특정 부분이 일시적으로 실행되지 않도록 보류하기 위해 사용되므로 **프로젝트**의 목적에 따라 주석을 관리
- \#: 한 줄 주석
- ''' 여러줄 주석 '''
- 파이썬 코드 스타일 가이드

'[파이썬 코드 스타일 가이드](https://google.github.io/styleguide/pyguide.html)' 링크

## 입력과 출력

### 입력함수 input

<예시>

```
age = input('나이를 입력해주세요: ')
print(age + age)

# 1. input을 출력하면 결과창에 입력하는 화면이 나온다.
# 2. 입력된 값이 age라는 변수에 저장된다.
# 3. 변수는 계산이 된다.
# 4. 변수의 type 생각하기
```
### 출력함수 print

<예시>

```
print('010', '1234', '5678', sep='-', end = '???')
# sep: 문자열 사이에 삽입
# end: 문자열 끝에 삽입
# 출력 값: 010-1234-5678???
```
### f-string

<예시>

```
name = input('이름을 입력해주세요: ')
age = int(input('나이를 입력해주세요: '))
print(f"Hello World! nice to meet you, {name}, {name} is {age} years old")

# 변수를 추가할 때 가독성이 좋다는 장점 존재
```
### None

<예시>

```
# None은 마지막 라인에 출력되지 않는다.
# print문을 사용하지 않으면 출력 X

a = None
a
```

## 타입

### 변수
#### 변수 생성

<예시>

```
age = 30
name = '김민수' # 문자열을 사용할 때는 꼭 따옴표나 쌍따옴
print(age, name)

# 출력값: 30 김민수
```
```
x = 10
y = x
z = y
x = 20   # 변수를 재할당했을 때, 연결되었다 하더라도 다른 변수 값은 변하지 않음.

print(x, y, z)

# 출력 값: 20 10 10
```

#### 변수의 이름 짓기

- 변수 이름은 알파벳, 숫자, 언더스코어(_)로 구성
- 변수 이름은 숫자로 시작할 수 없음
- 파이썬의 키워드(if, else, try 등)는 변수로 사용할 수 없음
- 하이픈은 허용되지 않음
- 변수 이름은 대소문자를 구분함
- 변수명이 같으면 덮어쓰기처럼 작용한다.
- 일반변수는 첫 문자를 소문자로 사용함, Class만 첫 문자가 대문자
- 사용하지 않는 변수는 언더스코어(_)로 명명
- 스네이크 표기법(ex. daily_user_count)

#### 변수의 타입

타입은 변수를 어떻게 관리하고 처리할 것인지 결정

<예시>

```
age = 30
print(type(age))

name = '김민수'
print(type(name))

# 출력 값: <class 'int'> <class 'str'>
```

#### 정수(int)자료형

<예시>

```
# 정수의 사칙연산

x = 10
y = 3

result = x + y  # 결과가 정수형
print(result)
result = x - y  # 결과가 정수형
print(result)
result = x * y  # 결과가 정수형
print(result)
result = x / y  # 결과가 실수형
print(result)

# 출력 값: 13 7 30 3.3333333333333335
```
```
x = 10
y = 3

result = x // y  # 몫
print(result)
result = x % y  # 나머지
print(result)
```
```
# 진수
# b: 2진수,o: 8진수, x: 16진수(색깔 표현 시 사용)
x = 731
y = 0b0110  # 2진수
z = 0o123  # 8진수
w = 0x123  # 16진수

print(x, y, z, w)

# 출력 값: 731 6 83 291
```
```
# 메서드

x = 'hello'
print(x.upper())
print(x.lower())
print(x.capitalize())
print(x.title())

# 출력 값: HELLO hello Hello Hello
```
```
# id
'''
 -5 ~ 256은 메모리에 똑같이 할당되지만, 
그 외 나머지는 같은 값이더라도 id가 다를 수 있음
'''

x = 5453
print(id(x)) # 출력값: 134179368864560

y = 5453
print(id(y)) # 출력값: 134179368863504

# 다른 메모리에 재할당돼서 값이 바뀔 수 있음
```

#### 실수(float)자료형

<예시>

```
x = 10.0
y = 3.0

result = x + y  # 결과가 실수형
print(result)

# 출력 값: 13.0
# 금융 어플의 경우 -> 10000.00 -> 10000원 형태의 중요성(UI/UX)
```
```
# float의 특수 값

x = float('inf')
y = float('-inf')
z = float('nan') # 계산 오류

print(x > 10)
print(y > 10)
print(z == 10)

# 출력 값: True False False
# 부동소수점 문제
```
```
# 승수 e

x = 10e5
y = 10e-5

print(x)  # 1000000.0
print(y)  # 0.00001
```

#### 문자열(str)자료형

문자'열' -> 순서, 규칙 존재

<예시>
```
# 짧은 문장

x = 'Hello'
y = "World"

print(x, y)
print(f'{x} {y}')
print(type(x), type(y))

'''
출력 값: 
Hello World
Hello World 
<class 'str'> <class 'str'>
'''
```
```
# 문자의 합과 곱

x = 'Hello'
y = "World"

print(x + y)  # HelloWorld
print(x * 3)  # HelloHelloHello
```
```
x = '위니브 월드'
#    0 1 2 3 4 5
#    -6-5-4-3-2-1

print(x[0])  # 첫번째 문자
print(x[-1])  # 마지막 문자
print(x[0:2])  # 0부터 1까지, 0 <= x < 2, 2(stop) 포함 안됨
print(x[2:])  # 2부터 끝
print(x[:2])    # 처음부터 1
print(x[::-1])  # 역순
print(x[::2])  # 짝수
print(x[1::2])  # 홀수

# x[start:stop:step], : = 슬라이싱(리스트 일부 선택), 기본 스텝: 1
```
```
s = 'weniv_licat.png' 

# .png 삭제

print(s[:-4])  # weniv_licat
```
```
s = 'weniv_licat.png' 

# .png 표시

print(s[-4:])  # .png

'''
슬라이싱이 메서드보다 더 처리 속도가 빠름.
따라서, 메서드로 자르기 보단 슬라이싱으로 자르는 것이 바람직함
'''
```

# 마무리

오늘은 마크다운, 주석, 입출력, 정수 자료형, 실수 자료형, 문자열 자료형에 대해 배웠다.
![여름](https://images.unsplash.com/photo-1586902197503-e71026292412?q=80&w=2672&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
