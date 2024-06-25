# 5일차 정리

## 오늘의 상식

* 문제해결을 위한 3단계 프레임워크 [링크](https://eopla.net/magazines/17715#)
    * 1단계: 해결하는 문제 구체화
    * 2단계: 팀 및 이해관계자와 문제 조율
    * 3단계: 다시 문제로 돌아오기

## 조건문 if

조건이 참인 경우와 거짓인 경우

![사진](https://blog.kakaocdn.net/dn/cMxrL2/btrnoCKWJLC/auiuLAQ0GIDxualBMHykv1/img.jpg)

```
# 기본 조건문
x = 2
if x > 1:
    print('True')
else:
    print('False')
```

```
# 조건 연산자의 경우 결과가 True or False
# 0 이 아닌 모든 정수형은 True
# 리스트에 값이 존재하면 True, 공백이면 False
if True:    # True, False 둘다 가능
    print('True')
else:
    print('False')
```

```
# 1. 오늘 날씨가 어떤가요  ""이 아닐때
# 2. 오늘 기온이 어때요

weather = input('오늘 날씨가 어떤가요?')
tem = int(input('오늘 기온이 어때요?: '))

if weather != '' and tem >= 0:
    print(f'오늘 기온은 {tem}로 {weather}.')
```

### 삼항 연산자

- if-else 구문을 한 줄로 간단하게 표현할 수 있는 방법을 제공
- X if 조건 else Y
- 조건이 참이면 X가 평가되고, 거짓이면 Y가 평가
- 간단한 비교 시 사용
```
x = 5
y = 10
result = 'x가 더 큽니다' if x > y else 'y와 같거나 y가 더 큽니다.'
print(result) 

# 출력 값: 'y와 같거나 y가 더 큽니다.'
```

```
def my_function(x):
  return x + 5 if x > 0 else x - 5

print(my_function(3)) # 출력 값: 8
print(my_function(-2)) # 출력 값: -7
```

### 람다 함수

람다 함수는 다음과 같은 형식을 따름
- lambda 매개변수들: 표현식
- 매개변수: 함수에 전달하는 입력 값, 쉼표로 구분 가능
- : 있음
- 표현식의 경우, 삼항 연산자랑 비슷
- 람다함수가 필요한 경우
    * 간단한 함수가 필요할 때
    * 다른 함수의 인자로써 간단한 함수를 전달할 때
    * 가독성을 해치지 않는 범위 내에서 코드의 간결성 추구
- 하지만, 그냥 함수를 사용하는 것이 일반적
```
# 한개의 매개변수를 가지는 람다 함수

double = lambda x: x * 2    # 파라미터 -> 계산식
print(double(3))    # 출력 값: 6

def double_1(x):
    return x * 2    # lambda와 동일

print(double_1(3))    # 출력 값: 6
```

```
# 두개의 매개변수를 가지는 람다 함수

add = lambda x, y: x + y
print(add(3, 4))    # 출력 값: 7

def add_1(x, y):
    return x + y
print(add_1(3, 4))    # 출력 값: 7
```

```
# 조건식과 함께 하는 람다함수

maxi = lambda x, y: x if x > y else y
print(maxi(3, 4))    # 출력 값: 4

my_function = lambda x: 'Even' if x % 2 == 0 else 'Odd'
print(my_function(1)) # 결과 값: Odd
print(my_function(2)) # 결과 값: Even
```

### if - elif - else

```
# 예시
x = int(input("숫자를 입력하세요"))

if x > 0:
    print('x는 양수입니다.')
elif x < 0:
    print('x는 음수입니다.')
else:
    print('x는 0입니다.')
```

```
# 테이블 안내하기

people = int(input('몇 명 입장했습니까? (숫자만 입력): '))

if people > 6:
    print(f'{people}명이 입장하였습니다. 8인 테이블로 안내해드리겠습니다.')
elif people > 4:
    print(f'{people}명이 입장하였습니다. 6인 테이블로 안내해드리겠습니다.')
elif people > 2:
    print(f'{people}명이 입장하였습니다. 4인 테이블로 안내해드리겠습니다.')
elif people > 0:
    print(f'{people}명이 입장하였습니다. 2인 테이블로 안내해드리겠습니다.')
else:
    print('잘못된 입력입니다.')
```

```
# 등급 매기기

score = int(input("성적을 입력하세요 (0-100): "))

if score >= 90:     # 90점 이상인 경우 A
    print("A")
elif score >= 80:   # 80점 이상인 경우 B
    print("B")
elif score >= 70:   # 70점 이상인 경우 C
    print("C")
elif score >= 60:   # 60점 이상인 경우 D
    print("D")
else:               # 60점 미만인 경우 F
    print("F")
```

```
# 성적별 용돈

score = 81
money = 0

if score >= 90:
    money += 1000000
elif score >= 80:
    money += 100000
elif score >= 70:
    money += 10000
elif score >= 60:
    money += 1000
else:
    money = 0
print(money) # 출력: 100000
```

```
# 중첩 if 문

movie = {
    '영화': '레미제라블',
    '장르': '드라마',
    '서비스': '왓챠',
    '비용': 15000,
    '평점': 4.9
}

if movie['장르'] == 'SF':
    if movie['서비스'] == '디즈니':
        if movie['평점'] >= 4.5 and movie['비용'] <= 20000:
            print('영화시청')
else:
    print(movie['서비스'] + ' 구독하기!')
```

* 하지만, 실무에서는 가독성을 위해 **빌트인 함수 all을 사용**하여 중첩된 문구를 정리함
```
movie = {
    '영화': '레미제라블',
    '장르': '드라마',
    '서비스': '왓챠',
    '비용': 15000,
    '평점': 4.9
}

if all([
    movie['장르'] == 'SF',
    movie['서비스'] in ['디즈니','넷플릭스'],
    movie['평점'] >= 4.5,
    movie['비용'] <= 20000]):
    print('영화시청')
else:
    print(movie['서비스'] + ' 구독하기!')
```

```
# 커피 계산기

# 돈 받기
money = int(input("현재 갖고 있는 금액:"))

# 커피 메뉴 주문 받기
cof_menu = {'아메리카노': 600, '카페라떼': 1000, '카라멜마끼아또': 1500}
cof_pick = input("아메리카노, 카페라떼, 카라멜마끼아또: ")

# 커피 메뉴 잘못 주문
if cof_pick not in cof_menu:
    print("메뉴에 없는 커피입니다.")
else:
    pass

# 가격 계산
cof_price = int(cof_menu[cof_pick])
change = money - cof_price
if change >= 0:
    print(f"커피를 구입합니다. 거스름돈은 {change}원입니다. 감사합니다.")
else:
    print("잔액이 부족합니다.")
```

```
# 비밀번호 확인 함수
# 회원가입 시 데이터 입력 받음, 변하지 못하게 해야하는 변수, 유일 값
password1= 1234

password = input("비밀번호를 입력하세요: ")

def check_password(password):
    if password == str(password1):
        return "로그인 성공"
    else:
        return "로그인 실패. 다시 입력해주세요"

print(check_password(password))
```

```
def login(username, password):
    correct_username = "idididid"
    correct_password = "password"

    if username == correct_username and password == correct_password:
        return "로그인 성공"
    elif username != correct_username and password == correct_password:
        return "아이디가 틀렸습니다. 다시 입력해주세요"
    elif username == correct_username and password != correct_password:
        return "비밀번호가 틀렸습니다. 다시 입력해주세요"
    else:
        return "다시 입력해주세요"

username = input('아이디를 입력하세요: ')
password = input('비밀번호를 입력하세요: ')

result = login(username, password)
print(result)
```

### 실습

1. 실습 1. 사용자가 입력한 비밀번호의 강도를 검사하고 평가합니다.
2. 요구사항:
    - 사용자로부터 비밀번호를 입력받습니다.
    - 비밀번호의 길이, 대소문자, 숫자, 특수문자 포함 여부를 검사합니다.

아래는 비밀번호 강도를 평가하는 조건과 점수를 표형식으로 정리한 내용입니다.
    
| 조건 | 점수 | 설명 |
| --- | --- | --- |
| 길이 | 0-2 | 8자 미만: 0점<br>8-11자: 1점<br>12자 이상: 2점 |
| 대문자 포함 | 0-1 | 미포함: 0점<br>포함: 1점 |
| 소문자 포함 | 0-1 | 미포함: 0점<br>포함: 1점 |
| 숫자 포함 | 0-1 | 미포함: 0점<br>포함: 1점 |
| 특수문자 포함 | 0-1 | 미포함: 0점<br>포함: 1점 |


| 총점 | 강도 평가 |
| --- | --- |
| 0-2 | 매우 약함 |
| 3 | 약함 |
| 4 | 보통 |
| 5 | 강함 |
| 6 | 매우 강함 |
    
    ### 참고사항:
    
    - 최대 총점은 6점입니다. 이는 길이 조건으로 최대 2점과 나머지 각 조건으로 1점씩 부여됩니다.
    - 길이 조건만 차등 점수를 부여하고, 나머지 조건은 충족 여부에 따라 0점 또는 1점을 부여합니다.
    - 강도 평가는 총점을 기준으로 평가됩니다.
    - 평가 결과와 개선 제안을 출력합니다.

```
import re

def check_password_strength(password):
    strength = 0
    suggestions = []
    
    # 길이 검사
    if len(password) >= 12:
        strength += 2
    elif len(password) >= 8:
        strength += 1
    else:
        suggestions.append("8자 이상이어야 합니다.")
    
    # 대문자 검사
    if re.search(r"[A-Z]", password):
        strength += 1
    else:
        suggestions.append("대문자를 포함하세요.")
    
    # 소문자 검사
    if re.search(r"[a-z]", password):
        strength += 1
    else:
        suggestions.append("소문자를 포함하세요.")
    
    # 특수문자 검사
    if re.search(r"[!@#$%^&(),.?\":{}|<>]", password):
        strength += 1
    else:
        suggestions.append("특수문자를 포함하세요.")

    # 숫자 검사
    if any(char.isdigit() for char in password):
        strength += 1 
    else:
        suggestions.append("숫자를 포함하세요.")
    
    # 강도 평가
    if strength == 6:
        return "매우 강함", suggestions
    elif strength == 5:
        return "강함", suggestions
    elif strength == 4:
        return "보통", suggestions
    elif strength == 3:
        return "약함", suggestions
    elif strength <= 2:
        return "매우 약함", suggestions

                 
# 메인 프로그램
password = input("비밀번호를 입력하세요: ")                 
strength, suggestions = check_password_strength(password)
print(f"비밀번호 강도: {strength}")
print("개선 제안:", ", ".join(suggestions) if suggestions else "없음")
```

실습2: 주문을 받고 커피 영수증을 출력
```
import tkinter as tk
from tkinter import messagebox

def order_item():
  order_summary = "order summary\n"
  total_cost = 0

  # 아메리카노 메뉴 계산
  quantity = int(americano_entry.get())  # ex) 3
  if quantity > 0:
    item_total = quantity * 3000
    order_summary += f"Americano: {quantity} x 3000 = {item_total}\n"
    total_cost += item_total

  result_label.config(text=order_summary)

  # 라떼 메뉴 계산
  quantity = int(latte_entry.get())  # ex) 3
  if quantity > 0:
    item_total = quantity * 4000
    order_summary += f"Americano: {quantity} x 4000 = {item_total}\n"
    total_cost += item_total

  result_label.config(text=order_summary)

  # 치즈케익 메뉴 계산
  quantity = int(cheese_cake_entry.get())  # ex) 3
  if quantity > 0:
    item_total = quantity * 5000
    order_summary += f"Cheese Cake: {quantity} x 5000 = {item_total}\n"
    total_cost += item_total

  result_label.config(text=order_summary)

  # 아이스티 메뉴 계산
  quantity = int(ice_tea_entry.get())  # ex) 3
  if quantity > 0:
    item_total = quantity * 2000
    order_summary += f"Ice Tea: {quantity} x 2000 = {item_total}\n"
    total_cost += item_total

  order_summary += f"Total Cost: {total_cost}"
  result_label.config(text=order_summary)


# 기본 윈도우 구성
root = tk.Tk()
root.title("cafe order system")

# 카페 메뉴
# tk.label(기본윈도우, text, 위치)
# 아메리카노
tk.Label(root, text="americano (3000 won)").grid(row=0, column=0)
americano_entry = tk.Entry(root, width=5)
americano_entry.grid(row=0, column=1)

# 라떼
tk.Label(root, text="latte (4000 won)").grid(row=1, column=0)
latte_entry = tk.Entry(root, width=5)
latte_entry.grid(row=1, column=1)

# 치즈케익
tk.Label(root, text="cheese cake (5000 won)").grid(row=2, column=0)
cheese_cake_entry = tk.Entry(root, width=5)
cheese_cake_entry.grid(row=2, column=1)

# 아이스티
tk.Label(root, text="ice tea (2000 won)").grid(row=3, column=0)
ice_tea_entry = tk.Entry(root, width=5)
ice_tea_entry.grid(row=3, column=1)

# 결제 버튼
order_button = tk.Button(root, text="order", command=order_item)
order_button.grid()

# 결과 창
result_label = tk.Label(root, text="total price")
result_label.grid(row=5, column=0)

# 메인 루프
root.mainloop()
```

## 매치(match)

- 여러 조건을 체크하여 해당 조건에 맞는 코드 블록을 실행하는 제어문
- match 문을 Python 3.10 이상에서 사용할 수 있게 됨

```
# 예시
text = 'Hello World'
match text:
    case 'Hello':
        print('Hello')
    case 'World':
        print('World')
    case _:
        print('No Match') # 출력 값: 'No Match'

# case_ 는 일종의 디폴트 값으로 앞에서 값이 정해지지 않으면 무조건 출력되게 됨, else와 비슷
```

```
text = '1'
match text:
    case '1' | '2':
        print('1, 2')
    case _:
        print('No Match')

# case 에서는 and 나 or이 아닌 |를 사용하여 or을 표현
```

# 마무리
오늘은 조건문 if에 대하여 배웠다.

![사진](https://images.unsplash.com/photo-1718027808460-7069cf0ca9ae?q=80&w=2574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
