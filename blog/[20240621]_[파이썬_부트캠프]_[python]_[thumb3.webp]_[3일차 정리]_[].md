# 3일차 정리

## 오늘의 상식

- LLM 성능 압도, 엔트로픽, '클로드 3.5 소네트' 출시
- 영국, ai 각본 영화 상영 취소, 대중들의 반발
- 앱 개발 사이트 [softr](https://www.softr.io/)

## 리스트(list)

- 시퀀스 자료형
- 위치의 특성을 갖고 있어서 정렬할 수 있음
- 가변적인 자료여서 변경 추가 삭제 가능

```
# 리스트 기초
# 다양한 자료형을 리스트에 넣는 것을 권장 X

x = [1, 2, 3]   # csv 파일과 비슷
y = ['apple', 'banana', 'cherry']
z = [1, [2], 3]  # 리스트 안에 리스트 가능

print([2] in z)
print(len(x), len(y))    # 출력 값: 3, 3
# 리스트의 길이가 너무 길 때, 자료 개수
```

```
x = [1, 2, 3]   # csv 파일과 비슷
y = ['apple', 'banana', 'cherry','melon']
# 데이터 매칭에 오류가 생겼을 때 활용 가능

print(len(x) == len(y))    # 출력 값: False
```

```
# 리스트 항목 변경하기
a = [1, 2, 3, 4, 5]
a[0] = 10

print(a)    # 출력 값: 10, 위치를 통해 변경 가능

a = ['apple', 'banana', 'cherry']
a[0] = 'melon'

print(a)    # 출력 값: ['melon', 'banana', 'cherry]
```

```
# 다차원 리스트
a = [[1, 2, 3], [10, 20, 30]]

print(a[0][1])  # 출력 값: 2
print(a[1][2])  # 출력 값: 30
```

```
# 리스트의 연산
a = [1, 2, 3]
b = [4, 5, 6]

print(a + b)    # 출력 값: [1, 2, 3, 4, 5, 6]
print(a * 3)    # 출력 값: [1, 2, 3, 1, 2, 3, 1, 2, 3]
print(b + a)    # 출력 값: [4, 5, 6, 1, 2, 3]
```

```
# 리스트 인덱싱, 슬라이싱
a = [1, 2, 3, 4, 5]

print(a[1:3])    # 출력 값: [2, 3]
print(a[10])     # 출력 값: IndexError: list index out of range
print(a[::-1])     # 출력 값: [5, 4, 3, 2, 1]
```

```
# 자주 쓰는 메서드
a = [1, 2, 3]
a.append(4)
print(a)    # 출력 값: [1, 2, 3, 4]

a.clear()
print(a)    # 출력 값: []

a = [1, 2, 3]
b = a.copy()    # 얕은 복사
print(b)    # 출력 값: [1, 2, 3]

a = [1, 2, 3]
b = a
print(b)    # 출력 값: [1, 2, 3],

b[0] = 10000
print(a)    # 출력 값: [10000, 2, 3]
# copy를 사용하지 않으면 원본도 변경됨

a = [1, 2, 2, 2, 2, 2, 3, 3]
print(a.count(2))    # 출력 값: 5
```

```
# extend(append와 비슷)

a = [1, 2, 3]
a.extend([4, 5, 6]) # 리스트가 풀어져서 구성원이 추가됨
print(a)    # 출력 값: [1, 2, 3, 4, 5, 6]

a.extend('hello')
print(a)    # 출력 값: [1, 2, 3, 4, 5, 6, 'h', 'e', 'l', 'l', 'o']

a = [1, 2, 3]
a.append([4, 5, 6])
print(a)    # 출력 값: [1, 2, 3, [4, 5, 6]]
```

```
# index()
a = [1, 2, 3, 4, 5]
print(a.index(3))    # 출력 값: 2, 위치를 찾아줌
```

```
# insert()
a = [1, 2, 3, 4, 5]
a.insert(1, 10) # insert(자리, 값)

print(a)    # 출력 값: [1, 10, 2, 3, 4, 5]
```

```
# pop()
a = [1, 2, 3, 4, 5]
print(a.pop(2))    # 출력 값: 3 -> 위치의 값을 뺌
print(a)    # 출력 값: [1, 2, 4, 5] -> 3이 빠진 리스트가 됨

l = [1, 2, 3, 4, 5]
while l:
    print(l.pop())  # 출력 값: 5 4 3 2 1 -> 값을 순서대로 뺌

# remove()
a = [1, 2, 3, 4, 5]
a.remove(3)
print(a)    # 출력 값: [1, 2, 4, 5] -> 3이 빠진 리스트가 됨

a = [1, 2, 2, 2, 2, 2, 2, 3, 4, 5]
while a.count(2):
    a.remove(2)
print(a)    # 출력 값: [1, 2, 4, 5]
```

```
# reverse()
# reversed()
a = [1, 2, 3, 4, 5]
a.reverse()
print(a)    # 출력 값: [5, 4, 3, 2, 1]

a = [1, 2, 3, 4, 5]
b = reversed(a)
print(list(b))    # 출력 값: [5, 4, 3, 2, 1]
```

```
# sort()
# sorted()
a = [1, 3, 2, 5, 4]
a.sort()
print(a)    # 출력 값: [1, 2, 3, 4, 5]

a = [5, 4, 3, 2, 1]
b = sorted(a)
print(a)    # 출력 값: [5, 4, 3, 2, 1]
print(b)    # 출력 값: [1, 2, 3, 4, 5]
```

## 튜플(tuple)

- 불변
- 튜플은 변경되면 안되는 정보(예를 들어, 주민번호, 비밀번호 등)에 활용
- Key 값(SQL)
- 튜플은 소괄호 사용
- 연산, 슬라이싱 등 가능(변경만 안됨)

```
# 튜플
a = (1, 2, 3)
print(type(a))    # 출력 값: <class 'tuple'>

b = [1, 2, 3]
c = (1, 2, b)
print(c)    # 출력 값: (1, 2, [1, 2, 3])
```

```
# 단일 튜플
t1 = ()
t2 = (0,) # 단일 값의 튜플을 사용할때 꼭 콤마 사용
t3 = (0)
t4 = (0.1)
print(type(t1)) # 출력 값: tuple
print(type(t2)) # 출력 값: tuple
print(type(t3)) # 출력 값: int
print(type(t4)) # 출력 값: float
```

```
# count()

a = (1, 2, 3, 4, 5)
print(a.count(3))    # 출력 값: 1

# index

a = (1, 2, 3, 4, 5)
print(a.index(3))    # 출력 값: 2
```

## 딕셔너리(dict)

- 사전과 같은 구조
- key(유일)와 value(중복 가능)가 존재
- 시퀀스 자료형 아님

```
# 딕셔너리 예시
Kim = {'age': 25, 
       'name': 'Kim', 
       'gender': 'male', 
       'height': 170, 
       'weight': 60
       }
```

```
# 중복된 key 값 중 마지막 값으로 출력
d = {'one' : '하나', 'one' : '하나2', 'one' : '하나3'}
print(d)  # 출력 값: {'one' : '하나3'}
```

```
# 키 값으로 다양한 자료형이 나와도 됨
# 하지만, 관리 상 그렇게 사용하진 않음
complex_dict = {
    "numbers": [1, 2, 3],
    42: "answer",
    ("x", "y"): [10, 20],
    True: [100, 200]
}

print(complex_dict["numbers"])  # 출력 값: [1, 2, 3]
print(complex_dict[42])         # 출력 값: answer
print(complex_dict[("x", "y")]) # 출력 값: [10, 20]
print(complex_dict[True])       # 출력 값: [10, 20]
```

**JavaScript Object Notation (JSON)**
- Javascript 객체 문법으로 구조화된 데이터를 표현하기 위한 문자 기반의 표준 포맷
- 웹 어플리케이션에서 데이터를 전송할 때 일반적으로 사용

```
# 딕셔너리 수정
person = {'name': 'Kim', 'age': 25, 'gender': 'male'}
person['age'] = 24

print(person)    # 출력 값: {'name': 'Kim', 'age': 24, 'gender': 'male
person['height'] = 170 # 이 형식으로 추가할 수 있음

print(person)
# 출력 값: {'name': 'Kim', 'age': 24, 'gender': 'male', 'height': 170}
```

```
# 중첩된 딕셔너리
users = {
    'user1': {'name': 'Kim', 'age': 25, 'gender': 'male'},
    'user2': {'name': 'Lee', 'age': 24, 'gender': 'male'},
    'user3': {'name': 'Park', 'age': 23, 'gender': 'female'}
}

print(users['user1']['name'])    # 출력 값: Kim
print(users['user2']['age'])     # 출력 값: 24
print(users['user3']['gender'])  # 출력 값: female
```

```
# zip(list1, list2): 두개의 리스트를 짝짓는 함수

keys = ['name', 'age', 'gender']
values = ['Kim', 25, 'male']
new_dict = dict(zip(keys, values))
print(new_dict)    # 출력 값: {'name': 'Kim', 'age': 25, 'gender': 'male'}
```

```
# clear(): list와 동일, 전부 삭제
# copy(): 얕은 복사본
# fromkeys(): 공통적으로 일괄 적용
keys = ['name', 'age', 'gender']
values = None
new_dict = dict.fromkeys(keys, values)

print(new_dict)    # 출력 값: {'name': None, 'age': None, 'gender': None}

keys = ['name', 'age', 'gender']
values = ['Kim', 25, 'male']
new_dict = dict.fromkeys(keys, values)

print(new_dict)    # 출력 값: {'name': 'Kim', 'age': 25, 'gender': 'male'}
```

```
# get(): key 값을 찾음
person = {'name': 'Kim', 'age': 25, 'gender': 'male'}

print(person.get('name'))    # 출력 값: Kim
print(person.get('height'))  # 출력 값: None
print(person.get('height', 170))  # 출력 값: 170
```

```
# items(): 딕셔너리의 키와 값을 쌍으로 추출
person = {'name': 'licat', 'city': 'Jeju', 'job': 'Developer'}

print(person.items())
print('one' in person)  # 출력 값: False
print('name' in person) # 출력 값: True
```

```
# keys(): 딕셔너리의 모든 키를 추출
person = {'name': 'licat', 'city': 'Jeju', 'job': 'Developer'}

print(person.keys())
```

```
# pop(): 주어진 키의 값을 반환하고, 해당 키-값 쌍을 딕셔너리에서 삭제
numbers = {'one': '하나', 'two': '둘', 'three': '셋'}
one_value = numbers.pop('one')

print(one_value)    # 출력 값: 하나
print(numbers)    # 출력 값: {'two': '둘', 'three': '셋'}

# popitem():  마지막 키-값 쌍을 반환하고, 그 항목을 삭제
numbers = {'one': '하나', 'two': '둘', 'three': '셋'}
four_value = numbers.setdefault("four", "넷")
print(four_value)   # 출력 값: 넷
print(numbers)    # 출력 값: {'one': '하나', 'two': '둘', 'three': '셋', 'four': '넷'}
```

```
# update(): 기존 딕셔너리에 추가 데이터를 병합
numbers = {'one': '하나', 'two': '둘', 'three': '셋'}
numbers.update({'four': '넷', 'five': '다섯'})
print(numbers)
# 출력 값: {'one': '하나', 'two': '둘', 'three': '셋', 'four': '넷', 'five': '다섯'}

# values()
person = {'name': 'licat', 'city': 'Jeju', 'job': 'Developer'}
print(person.values())    # 출력 값: dict_values(['licat', 'Jeju', 'Developer'])

# setdefault(): 주어진 키에 대한 값을 반환
numbers = {'one': '하나', 'two': '둘', 'three': '셋'}
four_value = numbers.setdefault("four", "넷")
print(four_value)   # 출력 값: 넷
print(numbers)
# 출력 값: {'one': '하나', 'two': '둘', 'three': '셋', 'four': '넷'}
```

## 셋(set)

- 순서 없음, 중복 허용 X -> 인덱싱 불가
- 수학의 **집합**
- 리스트처럼 쓰면서 중괄호 사용
- 집합은 데이터 중복을 제거하는 데 매우 유용
- 집합 연산을 사용하여 두 그룹의 유사성이나 차이점을 빠르게 파악

```
x = {1, 2, 3}   # 형태도 집합이랑 같음
y = {'apple', 'banana', 'cherry'}

# 문자열도 중복 허용 x
string_set = set("Hello")
print(string_set)    # 출력 값: {'l', 'o', 'H'}
```

```
# 집합의 연산
x = {1, 2, 3}
y = {3, 4, 5}

# 합집합
print(x | y)    # 출력 값: {1, 2, 3, 4, 5}

# 교집합
print(x & y)    # 출력 값: {3}

# 차집합
print(x - y)    # 출력 값: {1, 2}
```

## 5장 연습문제 풀이

### 1.

다음은 python 강좌 학생들의 시험 점수를 딕셔너리로 나타낸 것입니다.

student_score = {
		'홍의': 97,
		'원희': 60,
		'동해': 77,
		'변수': 79,
		'창현': 89,
}

1. 학생들의 총점을 구하는 코드를 작성하세요.

2. 학생들의 평균 점수를 구하는 코드를 작성하세요.

3. 호준: 98 점수가 추가되었습니다. 이 점수를 반영하여 학생들의 평균 점수를 구해주세요.

4. 문제가 하나 잘못 출제되어 모두 2점이 올랐습니다. 학생들의 모든 점수를 2점씩 올려주세요.

5. 점수가 가장 높은 학생의 이름과 그 점수를 구하는 코드를 작성하세요.

6. 점수가 가장 낮은 학생의 이름과 그 점수를 구하는 코드를 작성하세요.

```
# 강좌 학생들의 시험 점수 딕셔너리
student_score = {'홍의': 97,
                 '원희': 60,
                 '동해': 77,
                 '변수': 79,
                 '창현': 89
                 }

# 학생들의 점수 총점
all_score = student_score.values()
total_score = sum(all_score)
print(total_score)

# 학생들의 점수 평균
avg_score = total_score / len(all_score)
print(avg_score)

# 호준 추가, 새로운 평균
student_score["호준"] = 98
all_score2 = student_score.values()
total_score2 = sum(all_score2)
avg_score2 = total_score2 / len(all_score2)
print(avg_score2)

# 모든 학생 + 2점
for key, value in student_score.items():
    student_score[key] = value + 2
print(student_score)

# 가장 높은 점수와 그 학생
max_score = max(student_score.values())
max_student = max(student_score, key=student_score.get)
print(f"가장 높은 점수: {max_score}, 학생: {max_student}")

# 가장 낮은 점수와 그 학생
min_score = min(student_score.values())
min_student = min(student_score, key=student_score.get)
print(f"가장 낮은 점수: {min_score}, 학생: {min_student}")
```

### 2.
학생 7명이 같이 먹을 점심 메뉴를 고르려고 합니다. 학생들의 각자 좋아하는 메뉴와 싫어하는 메뉴를 like 와 dislike 리스트에 담았습니다.

like = ['볶음밥', '라면', '국수', '파스타', '치킨', '짜장면', '국밥']

dislike = ['국밥', '짬뽕', '찜닭', '파스타', '국수', '카레', '덮밥']

학생들은 점심 메뉴를 고를 때, 한 명이라도 싫어하는 메뉴라면 고르지 않기로 했습니다.

최종 후보 메뉴들의 리스트를 구하는 코드를 작성해주세요.

```
# 좋아하는 메누에서 싫어하는 메뉴 빼기
like = ['볶음밥', '라면', '국수', '파스타', '치킨', '짜장면', '국밥']
dislike = ['국밥', '짬뽕', '찜닭', '파스타', '국수', '카레', '덮밥']

# 차집합
final_menu = list(set(like) - set(dislike))
print(final_menu)


# 모범 답안
like = ['볶음밥', '라면', '국수', '파스타', '치킨', '짜장면', '국밥']
dislike = ['국밥', '짬뽕', '찜닭', '파스타', '국수', '카레', '덮밥']

final_menu = []

for menu in like:
    if menu not in dislike:
        final_menu.append(menu)

print(final_menu)
```

### 3.
주어진 리스트

data = [{"이름": "길동", "수학": 3, "과학": 93}, {"이름": "춘향", "수학": 33, "과학": 11}, {"이름": "철수", "수학": 94, "과학": 67}]

에서 평균점수가 가장 높은 학생의 이름을 출력하세요.

```
# data 불러오기
data = [{"이름": "길동", "수학": 3, "과학": 93},
        {"이름": "춘향", "수학": 33, "과학": 11},
        {"이름": "철수", "수학": 94, "과학": 67}
        ]

# 평균 점수 구하기
avg_scores = []
for student in data:
    avg_score = (student["수학"] + student["과학"]) / 2
    avg_scores.append(avg_score)
name = []
for student in data:
    name.append(student["이름"])

# 이름 평균 점수로 딕셔너리 만들기
avg_score_dict = dict(zip(name, avg_scores))

# 평균 점수 가장 높은 학생 찾기
max_avg_score = max(avg_score_dict.values())
max_avg_student = max(avg_score_dict, key=avg_score_dict.get)

print(f"평균 점수가 가장 높은 학생: {max_avg_student}")


# 모범 답안, lambda 함수 사용
data = [
    {"이름": "길동", "수학": 3, "과학": 93},
    {"이름": "춘향", "수학": 33, "과학": 11},
    {"이름": "철수", "수학": 94, "과학": 67}
]
max_entry = max(data, key=lambda x: x["수학"]+x["과학"])
print(max_entry["이름"])
```

### 4.

주어진 사전 grades = {"Tom": 87, "Jerry": 95, "Mickey": 70}의 모든 값을 5점씩 증가시키고 결과를 출력하세요.

```
# 딕셔너리 불러오기
grades = {"Tom": 87, "Jerry": 95, "Mickey": 70}

# 5점씩 증가시키기
for key, value in grades.items():
    grades[key] = value + 5

print(grades)


# 모범 답안
grades = {"Tom": 87, "Jerry": 95, "Mickey": 70}

updated_grades = {name: score + 5 for name, score in grades.items()}
# 딕셔너리 구조로 grades에서 key와 values를 불러옴
# value에 5를 더함

print(updated_grades)
```

### 5.

주어진 문자열

s = "apple banana apple cherry banana cherry apple"에서

가장 자주 등장하는 단어를 출력하세요.

```
# 문자열
s = "apple banana apple cherry banana cherry apple"

# 리스트로 만들기
words = s.split()

# 사전에 넣을 단일 값
d = list(set(words))

# 등장하는 동일 단어 개수 계산
s = []
a = 0
b = 0
c = 0
for x in range(len(words)):
    if words[x] in d[0]:
        a += 1
    elif words[x] in d[1]:
        b += 1
    elif words[x] in d[2]:
        c += 1

s.append(a)
s.append(b)
s.append(c)

# 사전으로 고정하기
dic = dict(zip(d, s))

# 가장 자주 등장하는 단어
max_word = max(dic, key=dic.get)
print(max_word)


# 모범 답안
s = "apple banana apple cherry banana cherry apple"
words = s.split()
most_frequent_word = max(set(words), key=words.count)
# words를 list 자료형에서 set 자료형으로 변경하고 key 값을 카운트 한 다음 큰 값 도출

print(most_frequent_word)
```

## 함수(def my_function():)

```
#들여쓰기 - 스페이스바 4번 입력 (띄어쓰기)

def my_function(): #함수의 정의
    print('1') #함수의 본문 시작
    print('2')
    print('3') #함수의 본문

my_function() #함수의 호출

# print의 경우 그 자체로 함수라 출력 가능
```

```
# 함수는 재사용이 가능함
# 한 코드의 구조를 한 눈에 파악 가능
i = 0
def repeat_10():
    for i in range(10):
        i += 1
        print("10번 반복")

repeat_10()
```

```
def function_name(x, y):
    z = x + y
    return z    # 함수는 return으로 종료하게 됨

print(f"function_name(1, 2): {function_name(1, 2)}")    # 출력 값: 3
```

```
# pass
def function_x(x, y):
    """

    Args:
      x:
      y:
    """
    pass    # 함수의 본문이 없을 때 사용, 함수만 저장(실행 X)
```

```
def simple_function():
    print('Hello, World!') # 출력 값: 'Hello, World!'

# 함수 호출
print(simple_function()) # 출력 값: None, return이 없음
```

```
# 파라미터는 없지만 return은 있는 함수
def give_me_five():
    return 5

result = give_me_five()
print(result)    # 출력 값: 5, 고정된 값을 출력할 때 사용
```

```
def greeting(name):
    print(f'Hello, {name}!')

# 함수 호출
greeting('Kim')    # 출력 값: Hello, Kim!
```

```
def add(x, y):
    result = x + y
    return result

# 함수 호출
result = add(5, 4)
print(result)    # 출력 값: 9
```

### 간단한 함수 만들어 보기

```
# 숫자 2개를 입력 받아 합 계산해주는 함수
def add(x, y):
    x = int(input("숫자를 입력하세요"))
    y = int(input("숫자를 입력하세요"))
    z = x + y
    return z

print(add(x, y))
```

**함수 사용 시 주의할 점**
- print는 함수와 관계없이 출력됨
- 함수 안의 변수는 밖에서 사용 시 error
- 함수는 return으로 받아줘야 함

# 마무리
오늘은 리스트형 자료들과 함수 기본에 대하여 배웠다.

![숲](https://images.unsplash.com/photo-1717511140281-52586e5e307d?q=80&w=2671&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
