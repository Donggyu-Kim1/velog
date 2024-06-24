# 2일차 정리

## 오늘의 상식
- 중국 생성형 AI의 성장 <영상링크>
- 기후위기, 코코아 가격의 상승
- 프론트엔드의 혁신, [Framer](https://www.framer.com/?via=anh72&gad_source=1&gclid=CjwKCAjwg8qzBhAoEiwAWagLrFkl0iN7eGAh70QLjkUpgIoF_sQyK0S4Xh8Oi1fqKzRgTMgJo3bnmBoCFKgQAvD_BwE)
- 'AI & 빅데이터쇼' 개막

## 문자열(str) 자료형
```
# lower() / upper()
# 1. (영어) 단어가 대소문자가 너무 섞여서 전처리가 힘들 때

a = "Hello World"
print(a.lower())    # 출력 값: hello world
print(a.upper())    # 출력 값: HELLO WORLD
```

```
'''
find() / index()
find()와 index()는 특정 데이터를 찾아서 출력해주는 메서드 
다만 두개의 메서드가 완전히 동일한 기능을 수행하는 것은 아님.
찾을 수 없는 문자열일 경우 find는 -1을 반환하는 반면, index는 error를 반환
'''

a = "Hello World"
print(a.find("o"))  # 출력 값: 4
print(a.index("o")) # 출력 값: 4
print(a.find("x"))  # 출력 값: -1, 찾을 수 없기 때문
```

```
# count()

s = "Hello World"
print(s.count("l")) # 출력 값: 3
```

```
# strip, 양쪽의 공백 제거
# 공백도 하나의 문자열에 해당

s = "   Hello World  "
print(s.strip())    # 출력 값: Hello World
```

```
#양쪽의 공백과 ',!'을 제거해주는 method

a = '    ,!!  hello world   '
print(a.strip(' ,!'))   # 출력 값: hello world
```

```
# replace, 문자열 대체

a = "Hello World"
print(a.replace("World", "Universe"))   # 출력 값: Hello Universe

# 텍스트가 다를 경우, 실행은 되지만 바뀌지 않음
```

```
a = "Hello World"
print(a.replace("l", "L"))  # 출력 값: HeLLo WorLd

# 해당되는 문자 전부 바뀜
```

```
# split(), join()
'''
split과 join은 문자열을 나누고 합치는 메서드
이러한 메서드를 통해 원하는 형식으로 데이터를 분할하고 합칠 수 있음
예를 들어 전화번호가 010 1000 1000으로 입력이 되었다면
띄어쓰기로 쪼개 010, 1000, 1000로 만들 수 있으며,
이것을 대쉬(-)로 합쳐 010-1000-1000처럼 만들 수 있음
'''
# 리스트형으로 변환 -> 바로 가져다가 쓸 수 있음

a = "010 1000 1000"
print(a.split())  # 아무것도 안쓰면 공백을 기준으로
                  # 출력 값: ['010', '1000', '1000']
s = "010-1000-1000"
print(s.split("-"))  # 기준: -
                     # 출력 값: ['010', '1000', '1000']

# join
print("-".join(a.split()))  # 나누고 '-'으로 조인
                            # 출력 값: 010-1000-1000
```

```
# rjust() / ljust() / center()
# 지정한 길이를 맞추고 나머지는 지정한 문자로 채워주는 문자

a = "Hello"
print(a.rjust(10,'@'))  # 출력 값: @@@@@Hello
print(a.ljust(10,'@'))  # 출력 값: Hello@@@@@
print(a.center(11,'@')) # 출력 값: @@@Hello@@@

# 고객식별자 -> 고객번호 -> 문자형 '000001' -> 숫자형 1으로 나오는 상황 발생
# 위 함수를 통해 다시 변환

a = 1
print(str(a).rjust(6,'0'))  # 출력 값: 000001
```

```
# zfill
# 주어진 길이만큼 0을 채워서 반환
# 날짜, 데이터 라벨링 등에 사용

a = 1
print(str(a).zfill(6))  # 음수, 문자열도 가능
                        # 출력 값: 000001
filename = '1'.zfill(3) + '.jpg'
print(filename) # 출력 값: 001.jpg
```

```
year = '24'
month = '6'
day = '1'

today = year + month.zfill(2) + day.zfill(2)

print(today)    # 출력 값: 240601
```

```
# 이스케이프 문자

# \n: 새로운 줄을 나타냄
# \t: 탭을 나타냄
# \r: 커서를 오른쪽(줄의 처음)으로 이동
# \": 큰따옴표를 나타냄
# \': 작은따옴표를 나타냄
# \\: 백슬래시를 나타냄

print("Hello\nWorld")   # 출력 값: Hello
                                   world
print("Hello\tWorld")   # 출력 값: Hello    world
print("Hello\rWorld")   # 출력 값: world
print("Hello\"World")   # 출력 값: Hello"World
print("Hello\'World")   # 출력 값: Hello'World
print("Hello\\World")   # 출력 값: Hello\World
```

### 실습 문제
**사용자 정보 입력받기**
    - 사용자의 이름, 나이, 그리고 좋아하는 색깔을 차례로 입력받아서, 입력받은 정보를 출력하는 간단한 프로그램을 만들어보세요.
    - 이 프로그램은 `input()` 함수를 사용하여 사용자의 이름, 나이, 좋아하는 색깔을 입력받습니다.
    - 입력받은 각 정보는 변수에 저장된 후 `print()` 함수로 출력됩니다.
    - 추가적으로 입력된 나이를 숫자로 변환하여 연산에 사용할 수 있습니다 (예: 나이를 더하거나 빼기 등).

```
name = input("이름을 입력하세요: ")
age = int(input("나이를 입력하세요: "))
color = input("좋아하는 색깔을 입력하세요: ")

print(f"이름: {name}, 나이: {age}, 좋아하는 색깔: {color}")
```

**사용자 정보 입력받기2**
- 사용자로부터 좋아하는 음식, 영화, 취미 세 가지를 입력받아 요약해 출력하는 프로그램을 만들어보세요.
- 좋아하는 음식, 영화, 취미에 대한 정보를 입력받아 이를 요약하여 출력합니다.
- `input()` 함수로 각 정보를 받고, 입력받은 정보를 바탕으로 요약 문장을 출력합니다.

```
food = input("좋아하는 음식을 입력하세요: ")
movie = input("좋아하는 영화를 입력하세요: ")
hobby = input("좋아하는 취미를 입력하세요: ")

print(f"oo씨의 좋아하는 음식은 {food}, 좋아하는 영화는 {movie}, 좋아하는 취미는 {hobby}입니다.")
```

**전화번호를 입력받아 지역번호만 추출하는 프로그램**
- `input()` 함수로 전화번호를 입력받습니다.
- `split()` 메서드를 사용하여 '-'를 구분자로 하여 문자열을 나눕니다.
- 리스트 인덱싱을 통해 첫 번째 요소(지역번호)를 추출합니다.
- 입력받은 전화번호 형식이 올바른지 검사하는 간단한 검증 로직을 추가할 수 있습니다.

```
tel = input("전화번호를 입력하세요(- 사용할 것): ")
tel1 = tel.split("-")
print(f"지역 번호: {tel1[0]}")
```

**사용자로부터 문장을 입력받아 특정 단어를 다른 단어로 치환**
- 사용자로부터 문장과 치환하고 싶은 단어, 그리고 새로운 단어를 입력받습니다.
- `replace()` 메서드를 사용하여 문장 내의 특정 단어를 새로운 단어로 치환합니다.
- `replace()` 함수는 원본 문자열을 변경하지 않고 새로운 문자열을 반환함을 유의하세요.
- 대소문자 구분 없이 치환하려면 입력받은 문장과 치환 대상 단어를 모두 소문자 또는 대문자로 변환한 후 처리할 수 있습니다.

```
sentence = input("문장을 입력하세요: ")
word = input("치환하고 싶은 단어를 입력하세요: ")
new_word = input("새로운 단어를 입력하세요: ")

# 소문자로만
print(f"치환된 문자는 다음과 같습니다. \"{sentence.replace(word, new_word).lower()}\"")

# 대문자로만
print(f"치환된 문자는 다음과 같습니다. \"{sentence.replace(word, new_word).upper()}\"")
```

## 논리(bool) 자료형
- True or False
- 덧셈, 곱셈 연산 가능 

```
print(1 == 1)   # 출력 값: True
print(1 == 2)   # 출력 값: False
print(True == 1) # 출력 값: True
print(False == 0) # 출력 값: False
print(True + 1) # 출력 값: 2
print(False + 1)    # 출력 값: 1
print(True * 5) # 출력 값: 5
print(False * 5)    # 출력 값: 1
```

## None 자료형
![None을 설명하는 사진](https://i.imgur.com/vxYZlJg.jpg)

위 사진처럼 
- 0의 경우: 값이 존재하지만 그 값이 0인 경우
- null(None): 빈 공간, 값이 존재하지 않음
- undefined: 정의되지 않음.
- NaN: 잘못된 값을 의미함

```
# 비어 있다, 아무것도 없다, 정보가 없다를 표현할 때 None
# None != 0
# 사칙연산 안됨
# None 값을 찾기 위해선 == 이 아닌 is None 을 사용하는 것을 권장

x = None

print(x is None)    # 출력 값: True

print(dir(None))
# 출력 값: ['__bool__', '__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']
```

## 형변환

```
wage = input("월급을 입력하세요: ")
print(type(wage))   # 출력 값: <class 'str'>

wage = int(wage)
print(type(wage))   # 출력 값: <class 'int'>

annual_salary = wage * 12
print(annual_salary)    # 출력 값: 3600
```

## 연산자

**연산자 종류**
- 산술연산자, 대입연산자(할당연산자), 비교연산자, 논리연산자, 비트연산자, 멤버연산자, 식별연산자

### 산술연산자

```
# 합
# 문자열 간, 실수 + 정수 가능
# set의 경우, 합집합, 차집합으로 적용됨
# 대시 기호 잘 사용하기

print(7 - 4)    # 출력 값: 3
print(7 -- 4)   # 출력 값: 11
print(7 --- 4)  # 출력 값: 3
```

```
# 나눗셈은 0으로 못 나눔

x =10
z = 0
# x / z -> ZeroDivisionError 발생
```

```
a = 10
b = 3

divide = a / b

print(f'{a} ÷ {b} = {divide:.2f}')  # 출력 값: 10 ÷ 3 = 3.33

# .nf : 소수점 n번째자리까지 나타내줌 
```

```
print(-2 ** 2)  # 출력 값: -4
# 괄호로 묶지 않으면 제곱을 먼저 하고 마이너스를 붙이는 연산을 하게 됨

print((-2)**2)  # 출력 값: 4
```

### 비교연산자

- True 인지 False 인지 알 수 있게 하는 연산자

```
# 비교연산자 종류

print(1 > 2)    # 출력 값: False
print(1 < 2)    # 출력 값: True
print(1 >= 2)   # 출력 값: False
print(1 <= 2)   # 출력 값: True
print(1 == 2)   # 출력 값: False
print(1 != 2)   # 출력 값: True
```

```
# 문자열도 가능하지만 유니코드를 알아야 함
print('banana' < 'apple')   # 출력 값: False 

# 자리수가 많을수록 큰 수가 할당됨
print('abcd' > 'abcda')  # 출력 값: False
```

### 논리연산자

- and: 모두 참이어야 True, 하나만 참일 경우 False
- or: 하나만 참이어도 True, 모두 거짓이어야 False
- not: 부정

```
print(True and False)   # 출력 값: False 
print(True or False)    # 출력 값: True
print(not True)         # 출력 값: False
```

#### 단락 평가

- 단락 평가(또는 단락 연산)는 논리 연산에서 연산의 결과가 **확정된 시점에서 더 이상의 평가를 중단**하는 방법
- and의 경우, 앞에 False가 나오면 False를 반환하고 뒤에 함수를 수행하지 않음
- or의 경우, 앞에 True가 나오면 True를 반환하고 뒤에 함수를 수행하지 않음

```
def test1():
    print("test1 함수 호출!")
    return False

def test2():
    print("test2 함수 호출!")
    return True

result = test1() and test2()
print(result)  
# 출력 값: test1 함수 호출!, False, "test2 함수 호출!" 가 출력되지 않음. 
```

### 할당연산자

- 변수에 값을 저장하는 데 사용
- 할당 연산자의 우선순위는 대부분의 다른 연산자들보다 낮음 -> 마지막으로 평가

```
x = 5
y = 2
z = 10

x += y * z  # y * z 연산 후 x에 값을 할당(+ 5)

print(x)  # 출력 값: 25
```

### 식별연산자

- 식별 연산자는 두 변수가 동일한 객체를 참조하고 있는지 확인하는데 사용
- is / is not

| 연산자 | 의미 | 결과 |
|---|---|---|
| `is` | 두 변수가 **같은 메모리 위치**를 가리키는지 확인 | **True**: 같은 위치를 가리킬 때, **False**: 다른 위치를 가리킬 때 |
| `is not` | 두 변수가 **다른 메모리 위치**를 가리키는지 확인 | **True**: 다른 위치를 가리킬 때, **False**: 같은 위치를 가리킬 때 |

```
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(id(a), id(b), id(c))  
# 출력 값: 134749702525056 134748881893440 134749702525056
# a 와 b의 주소가 다른 것을 알 수 있음

print('a == b', a == b) # 출력 값: True
print('a == c', a == c) # 출력 값: True
print('a is b', a is b) # 출력 값: False
print('a is c', a is c) # 출력 값: True
```

### 맴버연산(in 구문)

- 어떤 값이 목록 안에 있는지 확인해주는 기능

|연산자|의미|
|---|---|
| in |	값이 목록 안에 있으면 참(True)이에요.|
| not in |	값이 목록 안에 없으면 참(True)이에요.|

```
fruits = ["사과", "바나나", "포도"]

print("사과" in fruits)  # True, 사과가 목록에 있음
print("오렌지" not in fruits)  # True, 오렌지는 목록에 없음
```

### 연산과 연산자 우선순위

- 여러 연산자가 하나의 표현식(expression) 내에 있을 때 어떤 연산자가 먼저 계산되는지를 결정

| 우선순위 | 연산자 | 설명 | 예시 |
|---|---|---|---|
| 1 | `(값…), {값…}, [값…], {키:값…}` | 튜플, 셋, 리스트, 딕셔너리 생성 | `(1, 2, 3)`, `{1, 2, 3}`, `[1, 2, 3]`, `{‘name’: ‘Alice’, ‘age’: 30}` |
| 2 | `x[인덱스], x[인덱스:인덱스], x(인수…), x.속성` | 리스트와 튜플 인덱싱, 슬라이싱, 함수 호출, 속성 참조 | `my_list[0]`, `my_list[1:3]`, `my_function(1, 2)`, `my_object.attribute` |
| 3 | `await x` | await 표현식 | `await my_async_function()` |
| 4 | `**` | 거듭제곱 | `2 ** 3` (2의 3승) |
| 5 | `+, -, ~` | 부호, 비트 NOT | `-5`, `~10` |
| 6 | `*, /, //, %, @` | 곱하기, 나누기, 내림 나눗셈, 나머지, 행렬 곱셈 | `2 * 3`, `10 / 3`, `10 // 3`, `10 % 3`, `numpy.array([[1, 2], [3, 4]]) @ numpy.array([[5, 6], [7, 8]])` |
| 7 | `+, -` | 더하기, 빼기 | `2 + 3`, `5 - 2` |
| 8 | `<<, >>` | 쉬프트 연산 | `10 << 2`, `10 >> 2` |
| 9 | `&` | 비트연산 AND | `10 & 5` |
| 10 | `^` | 비트연산 OR | `10 ^ 5` |
| 11 | `in, not in, is, is not, <, ≤, >, ≥, ==, !=` | 멤버 연산자, 식별 연산자, 비교 연산자 | `1 in [1, 2, 3]`, `1 not in [1, 2, 3]`, `a is b`, `a is not b`, `1 < 2`, `1 <= 2`, `1 > 2`, `1 >= 2`, `1 == 2`, `1 != 2` |
| 12 | `not` | 논리 부정 | `not True` |
| 13 | `and` | 논리 AND | `True and False` |
| 14 | `or` | 논리 OR | `True or False` |
| 15 | `if else` | 조건부 표현식 | `x if x > 0 else -x` |
| 16 | `lambda` | 람다 표현식 | `lambda x: x ** 2` |
| 17 | `:=` | 할당 표현식 | `x := 10` |

# 마무리
문자열을 변환해주는 다양한 함수, 연산자에 대해 배웠다.

![moon](https://images.unsplash.com/photo-1532767153582-b1a0e5145009?q=80&w=2574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
